---
title: "Linux-image configuration problem"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by richardfarrar on 2010-03-19
Hi,

I'm extremely new to all this Linux malarkey, so still on a steep learning curve. I'm running Ubuntu 9.10 Server on an old Dell Poweredge server for web development with Apace, PHP and MySQL. My server is headless, so I primarily use Webmin for its administration. 

I've been doing pretty well and have got most things sorted, but have been running into problems for the last week or so when trying to update any of the packages, which now routinely fail to install, or so it informs me.

It seems (if I'm not mistaken) to stem from a mal configured file (see example below):

 [FONT=Verdana]linux-image-2.6.31-20-server[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Question: How do I fix this issue that seems to prevent me from doing any further updates? 
[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Regards,[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Richard 
[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]e.g.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]  [FONT=Verdana]Now updating libsmbclient ..[/FONT]
  [FONT=Verdana]**Installing package(s) with command apt-get -y install libsmbclient ..**[/FONT]
  [FONT=Verdana]Setting up linux-image-2.6.31-20-server (2.6.31-20.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-server
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Segmentation fault
User postinst hook script [/usr/sbin/update-grub] exited with value 139
dpkg: error processing linux-image-2.6.31-20-server (--configure):
subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-image-server:
linux-image-server depends on linux-image-2.6.31-20-server; however:
Package linux-image-2.6.31-20-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
linux-server depends on linux-image-server (= 2.6.31.20.33); however:
Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-image-2.6.31-20-server
linux-image-server
linux-server
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
sensible-mda linux-headers-2.6.31-19-server m4 procmail
linux-headers-2.6.31-17 linux-headers-2.6.31-19 sendmail-cf sendmail-base
linux-headers-2.6.31-17-server bsd-mailx mailx
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
libsmbclient
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
Need to get 1816kB of archives.
After this operation, 4096B of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic-updates/main libsmbclient 2:3.4.0-3ubuntu5.5 [1816kB]
Fetched 1816kB in 15s (117kB/s)
(Reading database ... 113710 files and directories currently installed.)
Preparing to replace libsmbclient 2:3.4.0-3ubuntu5.4 (using .../libsmbclient_2%3a3.4.0-3ubuntu5.5_amd64.deb) ...
Unpacking replacement libsmbclient ...
Processing triggers for man-db ...
Setting up linux-image-2.6.31-20-server (2.6.31-20.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-server
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Segmentation fault
User postinst hook script [/usr/sbin/update-grub] exited with value 139
dpkg: error processing linux-image-2.6.31-20-server (--configure):
subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-image-server:
linux-image-server depends on linux-image-2.6.31-20-server; however:
Package linux-image-2.6.31-20-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
linux-server depends on linux-image-server (= 2.6.31.20.33); however:
Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
dependency problems - leaving unconfigured
Setting up libsmbclient (2:3.4.0-3ubuntu5.5) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
linux-image-2.6.31-20-server
linux-image-server
linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]
  [FONT=Verdana]**.. install failed!**[/FONT]
  [/FONT]

---

### Post by UCSBGauchosRock on 2010-03-19
First off let me Welcome You to Ubuntu Linux

Your problem may be caused by broken packages. Try the Following

1.Open Terminal
2.Write Command "sudo dpkg --configure -a" without quotes
3.Try upgrade again.

---

### Post by richardfarrar on 2010-03-20
Hi,

Thanks for the advice, unfortunately however it didn't seem to help. The output result from running the command you suggested was:

Setting up linux-image-2.6.31-20-server (2.6.31-20.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-server
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Segmentation fault
User postinst hook script [/usr/sbin/update-grub] exited with value 139
dpkg: error processing linux-image-2.6.31-20-server (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.31-20-server; however:
  Package linux-image-2.6.31-20-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.31.20.33); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-server
 linux-image-server
 linux-server


Regards,

Richard

---

### Post by richardfarrar on 2010-03-20
I think I've solved it, but more by good luck than judgement I'm afraid; still it's all part of the learning curve. 

I found a post that referenced the same error number that I'd experienced: 

[http://ubuntuforums.org/showthread.php?t=1352300](http://ubuntuforums.org/showthread.php?t=1352300)

I tried the following command as a blind stab in the dark and it appears to have fixed the problem: 

**sudo apt-get install --reinstall grub**

Regards,

Richard

---

