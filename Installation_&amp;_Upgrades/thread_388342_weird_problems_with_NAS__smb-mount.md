---
title: "weird problems with NAS / smb-mount"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by Helmi on 2007-03-19
hi, 

don't know if this is the right place but as i'm really confused about the background of these problems i'll post it in the general section.

situation: i got a little SOHO network with a view pc's (some ubuntu, some windows), a little devel-server (ubuntu) and a Storage Box (buffalo tera station 1 TB).

the storage box runs a proprietary os only accessable via samba.

i got several mounts from my workstation (ubuntu) to the box which generally worked fine for about 2 weeks now. i didn't doo soo much work on that machine especially no programming. i started programming yesterday using eclipse (first time install).

one weird problem came up after a few minutes using eclipse. Eclipse whined about the open files (directly opened from the smb mount) were changed while open and have to be reloaded but i'm sure they were not - not wilfully. that's happening to nearly any open file (open via smb mount). it drives me crazy.

This morning another problem appeared. i had about 5 files open and one of them was already modified several times. after the next modification i tried to save it and got an error. I couldn't save it anymore so i closed it without saving and reopened it - same thing. 

I opened a console windows, navigated to the directory and opened it with vim - trying to save - same shi*. I looked at the rights and everything was fine. That happened again to some other files. After a reboot of the tera station that worked again until it rehappened some hours later.

if someone cares... this is an example of fstab

//192.168.xx.xx/linux /net/linux cifs username=xxx,password=xxx,dir_mode=0777,file_mode=0777,iocharset=utf
8,codepage=CP850,uid=1000,gid=1000 0 0


btw: the ubuntu server (little testmachine with LAMP-Config) also accesses these smbmounts to use the files to display a website with apache...

Hopefully anyone has ANY idea where the problem could reside. I alreday checked:

[LIST]
[*]same timezone (WS and NAS)
[*]time synched on both stations
[*]user/group rights
[/LIST]

thanks,
Frank

---

