---
title: "mountall problem: can't boot after release upgrade 9.04-&gt;9.10"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by elianto on 2010-05-10
hello to all!
I made a release upgrade 9.04->9.10 in a xen enviroment the process went relatively smooth, switched to the latest paravirt kernel, rebooted and it dropped in recovery mode 
 
       **Code:**              One or more of the mounts listed in /etc/fstab cannot yet be mounted 
(ESC for recovery shell) 
/: waiting for /dev/xvda 
/tmp: waiting for (null) 
swap: waiting for /dev/xvdb 
/mnt/bkup: waiting for /dev/xvdc 
     
 
fsck is ok and the boot stop there waiting for mountall to complete... other people (on desktop) have this error bypassed after a while and the system boots, but here it doesn't. 
 
I found a lot of people having the [same problem ]("http://www.google.it/search?q=One+or+more+of+the+mounts+listed+in+%2Fetc%2Ffstab+cannot+yet+be+mounted&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:it:official&client=firefox-a") 
and two related bugs in lanchpad 
[URL="https://bugs.launchpad.net/ubuntu/lucid/+source/mountall/+bug/559582"]559582 
[/URL] 
[URL="https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/459859"]459859 
[/URL] 
 
the suggested solution was to upgrade to initramfs-tools (>0.92bubuntu74) but it's available only for lucid it (brings a lot of dependency and mountall >2.14). I tried with mountall 1.02 but doesn't change anything. Tried the dpkg --configure -a but makes no effects/msg. Other suggested to change UID in fstab but I've none of them 
 
So I wonder how people here managed to upgrade? 
thanks for any advice I'm really stressed out this is a server in production

---

### Post by elianto on 2010-05-11
ok I solved after experimenting with the most weird setup to bypass mountall I found out that some packeges were left unconfigured And dpkg --configure -a didn't detected I had to do and aptiitude upgrade and it solved all!!! :)

---

