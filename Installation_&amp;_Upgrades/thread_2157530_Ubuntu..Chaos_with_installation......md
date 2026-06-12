---
title: "Ubuntu..Chaos with installation....."
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by krowkiley on 2013-06-25
I recently decided to give linux another shot. So I loaded up unetbootin, selected the daily distro, and went to work... 

i originally opened and installed under windows using wubi.exe, however it was unsuccesful (unitframs - i still havent solved this part of my problem) and decided to uninstall

NOTE:at the time i had a boot menu supporting both linux and windows...

i then installed it again under a live usb, which led to my problems with the boot menu...

I have been looking around for awhile, testing things... but i cant seem to fix it

mainly because i cant get boot-repair.
i tried the super grub loader, but that couldnt fix it via automation...

The Message i get when i boot my computer is

Error no such device
grub>


Please Help, I just want to play BF3 again



PS. when i tried to get the boot-repair i typed in the Terminal 

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
and then 
sudo apt-get install -y boot-repair && (boot-repair &)
but it said it couldnt find the package

---

### Post by oldfred on 2013-06-25
I just ran the command as you posted and they worked for me.

Wubi is being phased out. It does not work with gpt partitioned drives which all new UEFI systems have. In 12.04 you can only install wubi from inside Windows not from liveCD.

 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

---

### Post by buzzingrobot on 2013-06-27
When you say "daily distro", what exactly do you mean?  Which release?  

If it's the 13.10 daily, there's no assurance that that image will work from one day to the next.  It's still months from release.

---

