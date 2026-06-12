---
title: "vsftpd problem :("
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by gvardia-cs on 2013-11-19
Hi there :)
I'm quiet new to ubuntu , I have ubuntu 12.04 server , and I'm trying to setup vsftpd , but it is not working , and there is no ftp.myip :(
I have followed [THIS]("http://forumubuntusoftware.info/viewtopic.php?f=127&t=9294") tut (i have dynamic ip address so i'm using no-ip) , and then i restart vsftpd i get this :

stop: Unknown instance:
vsftpd start/running, process "number" 

But then i go to webmin , a can't find running process with that "number" :'(

Can anyone help ? 

P.S.
I port forwarded :
22
21
20
4242-4252

Thanks a lot :)

---

### Post by Lars Noodén on 2013-11-20
What problem are you trying to solve with vsftpd? 

If you are just looking for secure file transfers for your accounts then I would suggest instead installing the package OpenSSH-server.  It's there in the repository too.  Once installed you will have SFTP capabilities working out of the box with no additional configuration needed.  You can connect with the text-based sftp client or graphical clients like FileZilla, Nautilus, Thunar, and PCManFM.

---

### Post by gvardia-cs on 2013-11-20
Hi there , 
Thanks for your replay , i have openssh-server , and i can connect to my server , but i want to setup so other ftpuser can connect to my server , but can't go outside there directory (I have running website on my server , and i want to give few people ftp access to their subdomains)
So how do I do that ?

Thanks a lot :)

---

### Post by Lars Noodén on 2013-11-20
You can give separate types of access to different groups using the [match](http://manpages.ubuntu.com/manpages/saucy/en/man1/match.1.html) option in sshd_config. 

There are several such scenarios for chrooted SFTP access here:

[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts)

---

