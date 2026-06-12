---
title: "Dualboot Issue: Ubuntu can't see hard drive"
date: 2017-11-12
forum: Installation &amp; Upgrades
---

### Post by varb on 2017-11-12
I am a first time Ubuntu/Linux user and I am trying to install Ubuntu alongside Windows 10 on my Laptop. I am following this guide: [http://dailylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://dailylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

I made my partition in Windows. Image attached. After I booted into Ubuntu using my installation USB, I began the installation but got stuck at the Installation Type screen. That image is here [https://imgur.com/YgzJg8V](https://imgur.com/YgzJg8V) (sorry, for some reason it wouldn't let me upload it). I think this means Ubuntu cannot see my hard drive but I'm not completely sure. What can I do to resolve this? Thanks!

---

### Post by oldfred on 2017-11-12
You do not have what is normally considered the default partitions with a standard Windows UEFI install.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)

So how did you install Windows?
What brand/model system? Windows pre-installed or did you reinstall it?

What does this show from Live installer?
sudo parted -l

Is Windows fast start up off?
       
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

