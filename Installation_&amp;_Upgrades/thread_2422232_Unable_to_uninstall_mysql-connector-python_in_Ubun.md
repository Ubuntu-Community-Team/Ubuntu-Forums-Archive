---
title: "Unable to uninstall mysql-connector-python in Ubuntu 19.04"
date: 2019-07-04
forum: Installation &amp; Upgrades
---

### Post by pranav.bhattarai on 2019-07-04
My Java Sir told me to install MySQL-server, workbench, and connector. I did that somehow after spending 30+ hours reading different posts.
After launching Workbench, I went to Tools > Start Shell for MySQL Utilities. Which gave me this popup: [https://imgur.com/GQvHKsI](https://imgur.com/GQvHKsI)
Pressing Download option redirected me to [this]("https://downloads.mysql.com/archives/utilities/") website: [https://imgur.com/ETr2nrY](https://imgur.com/ETr2nrY)
After installing this package, whenever I run: sudo apt update, I get this error:

pranav@inspiron-5548:~$ ```
sudo apt-get upgrade
[sudo] password for pranav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  mysql-connector-python
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,362 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 216555 files and directories currently installed.)
Removing mysql-connector-python (8.0.16-1ubuntu19.04) ...
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'distutils.sysconfig'
dpkg: error processing package mysql-connector-python (--remove):
 installed mysql-connector-python package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 mysql-connector-python
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
So, I thought I should uninstall this, and I used sudo apt-get remove --purge mysql-connector-python command, but it also didn't work, and it throws me the same error as above. 

What to do? I am in limbo here! Since any new development done in "mysql-utilities" is aged back to Jan 17, 2017, I don't think I will be needing this anymore. I did the mistake trying to install old archived deb package. (newbie)
IF u know, how to remove it, what is it, it would be really helpful to tell me about it.

---

### Post by wildmanne39 on 2019-07-04
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

I normalized the fonts as you may have noticed your post was unreadable so now you stand a much better chance of getting your issue resolved.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Glad to see you made it here from facebook and twitter.;)

---

### Post by pranav.bhattarai on 2019-07-04
Normally, sudo apt autoremove should have worked but in this case, I used this command to the solved issue:

sudo mv /var/lib/dpkg/info/mysql-connector-python*/tmp

After using the above command, use sudo apt autoremove again and that will solve everything.
For more details about this issue, visit [this]("https://itsfoss.com/dpkg-returned-an-error-code-1/") site.

---

### Post by lisati on 2019-07-04
As you have already been asked,  please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by lisati on 2019-07-04
Please do not start multiple threads for the same problem, it can confuse those trying to help.

Duplicate of [https://ubuntuforums.org/showthread.php?t=2422199](https://ubuntuforums.org/showthread.php?t=2422199) closed.

---

