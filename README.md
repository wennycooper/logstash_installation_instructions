# logstash INSTALLATION INSTRUCTIONS
以下步驟說明如何安裝 logstash 到 iRSUs 內

## Requirements
* Ubuntu 16.04

## Install openJDK 1.8

    $ sudo apt-get install openjdk-8-jre
    $ cd /etc
    $ sudo vi /etc/environment   
    // 新增一行以下內容
    JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
    
    $ sudo bash
    # sync;sync;reboot  // reboot

// 等開機完成, 登入使用者, 然後繼續安裝以下套件.

## Install logstash 7.3.2
// 參考  https://www.elastic.co/guide/en/logstash/7.3/installing-logstash.html

    $ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
    
    $ sudo apt-get install apt-transport-https
    
    $ echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
    
    $ sudo apt-get update && sudo apt-get install logstash=1:7.3.2-1

## 測試

    $ sudo /usr/share/logstash/bin/logstash -e 'input { stdin { } } output { stdout {} }'
    // 等10秒鐘, 然後敲入 hello [按Enter]
    // 如果有輸出類似以下內容, 就算成功了, 請按 [CTRL]+[D] 退出即可

    2018-11-21T01:22:14.405+0000 0.0.0.0 hello
