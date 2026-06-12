---
title: "Bootloader default OS"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by NoSuchDevice on 2010-11-03
Hey all

I just installed Ubuntu, and I realised that the Default OS is Ubuntu however my family use this PC as well and by Default I want the system to boot in to windows vista, ubuntu is for my use only, how can I do this? Also my family are not that good with computers and it shows Windows Vista loader (sda3) that's a recovery partition! I don't want them to messing around with the bootloader.

Thanks

---

### Post by oldfred on 2010-11-03
Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even grub2.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

If you want to change titles it is not so easy unless you are comfortable editing files.

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will. Then turn off osprober so you do not have both sets of entries.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

### Post by NoSuchDevice on 2010-11-04
Right Thanks.

---

