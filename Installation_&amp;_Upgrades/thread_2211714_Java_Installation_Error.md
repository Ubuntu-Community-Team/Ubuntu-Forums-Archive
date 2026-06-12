---
title: "Java Installation Error"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by rajeshwar2 on 2014-03-17
When i am trying to install "Oracle(TM) Java Development Kit(JDK) 7" from Update Manager
I am getting error.

```
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Setting up oracle-java7-installer (7u51-0~webupd8~1) ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Downloading Oracle Java 7... 
--2014-03-17 21:54:36--  [http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 111.119.230.9, 111.119.230.8 
Connecting to download.oracle.com (download.oracle.com)|111.119.230.9|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) [following] 
--2014-03-17 21:54:36--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.47.230.140 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.47.230.140|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following] 
--2014-03-17 21:54:37--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) 
Connecting to download.oracle.com (download.oracle.com)|111.119.230.9|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
 
    The file is already fully retrieved; nothing to do. 
 
Download done. 
Removing outdated cached downloads... 
sha256sum mismatch jdk-7u51-linux-x64.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 oracle-java7-installer 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up oracle-java7-installer (7u51-0~webupd8~1) ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Downloading Oracle Java 7... 
--2014-03-17 21:54:38--  [http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 111.119.230.8, 111.119.230.9 
Connecting to download.oracle.com (download.oracle.com)|111.119.230.8|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) [following] 
--2014-03-17 21:54:38--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.47.230.140 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.47.230.140|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following] 
--2014-03-17 21:54:38--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) 
Connecting to download.oracle.com (download.oracle.com)|111.119.230.8|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
 
    The file is already fully retrieved; nothing to do. 
 
Download done. 
Removing outdated cached downloads... 
sha256sum mismatch jdk-7u51-linux-x64.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 


```

So what can i do,
Please Help me.

---

