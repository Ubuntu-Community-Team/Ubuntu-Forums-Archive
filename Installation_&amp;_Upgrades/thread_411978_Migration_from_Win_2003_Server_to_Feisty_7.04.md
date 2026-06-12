---
title: "Migration from Win 2003 Server to Feisty 7.04"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by MockY on 2007-04-17
Here is the situation. I have a Win 2003 server running as a file and web server. I have 2 750 gig hard drives attached as slave that hosts all of the files. Since PHP and MySQL doesn't really like to reside and work properly in windows, I am now seriously thinking about swapping to Fesity 7.04 now when it is officially is released.

Since the 750 gig drives are in NTFS, my question is simply this. How easy is it to put Ubuntu as OS and keep the slave drives intact. FTP accounts should be able to upload, alter, remove, and download from these drives. Or can I convert the NTFS drives to EXT3 without loosing any data? My other worry is remote access. I would like Remote Desktop in working condition and I figured that is a no brainer. My main consern is the slave drives.

How would I go about to do this? 

And as a side note. I have tried every FTP Server known to man that runs natively in Linux and I find the setup unnecessary complicated. I am used to ServU on Windows and would like a just as easy GUI to the ftp server. Since ServU doesn't run on Wine, I am forced to use a Linux native ftp server. So could someone guide in the right direction?

MockY

---

### Post by garlik42 on 2007-04-17
You can mount the ntfs drives and share them with samba, but the security will need to be at the share level.

As far as converting the drives to ext3 I don't think this is possible, to gain the full functionality of linux and sharing etc, you really should back those suckers up, and rebuild them as some linux file system type, this will allow you to have more granular security at the file and directory level.

I have always used proftp on linux for an ftp server, I don't know of a GUI that configures it, but I am sure there is one somewhere ...

---

### Post by thelinuxguy on 2007-04-17
I use PureFTP which has a GUI frontend PureAdmin. Available in the repos.

---

### Post by MockY on 2007-04-18
I installed PureFTP and PureAdmin to see what it was about. I started PureAdmin and I see 2 tabs. Activity and Logging. Clicking Manage Users results in a question about Password file, if I want to create it. I click yes and get an error: ```
There was an error when trying to create password file [(null)].
The error reported was: 'Bad address'
```
I guess that is because I am not root. But wouldn't I have to be root in order to run it later if it is created by root? And where do you add the different domains, ports, and users. 

I created manually a file in my home directory and added a file. I later pointed to that file and that worked. But, now when I try to add a user, I can't save. So I have to close the window to get out of there. Then it asks me if I wanted to save. I choose yes but it still doesn't stick. This gui is not the best in the world I would say. Nothing makes sense.

---

### Post by aberry5555 on 2007-04-18
One of the easiest Guis, which will also give you functionality for mysql and php etc, is WebMin, it means you can install the server version and never have to bother installing the desktop if you don't want to, as it lets you log on to it from another PC using your servers IP address + a port number (e.g. [https://192.168.0.1:10000)](https://192.168.0.1:10000)). It isn't in the repos, I dont think, but you can download it from here:

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

---

### Post by MockY on 2007-04-18
Just installed Webmoin but haven't applied any settings yet. But by just browsing around it looks really sweet. If the software listed is not installed, it will install it for you with one click of a button. Really dope. This is quite cool. Hopefull it works just as nice as it looks and feels.

Proftpd failed to install using webmin. Worked to install manually though.

---

### Post by aberry5555 on 2007-04-18
if it doesn't install automatically you can actually open a terminal within webmin so you can do it "manually" that way too.

---

