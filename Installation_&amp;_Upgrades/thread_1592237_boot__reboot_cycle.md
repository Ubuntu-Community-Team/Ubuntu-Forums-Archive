---
title: "boot  reboot cycle"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Don544 on 2010-10-10
After an attempt to install Ubuntu 10.10 as a dual boot with windows 7 64 bit my machine is stuck in a constant boot then Ubuntu screen then reboot then Ubuntu screen then reboot.
This process will continue as long as I choose to let it.
I am able to boot to the Ubuntu cd and run Ubuntu from the cd.
I can no longer boot to any cd, usb or dvd that is Windows based, as in my repair cd.
As a newbie I am lost as to how to get past this and any help would be appreciated.

---

### Post by bcbc on 2010-10-10
> **Don544 said:**
> After an attempt to install Ubuntu 10.10 as a dual boot with windows 7 64 bit my machine is stuck in a constant boot then Ubuntu screen then reboot then Ubuntu screen then reboot.
This process will continue as long as I choose to let it.
I am able to boot to the Ubuntu cd and run Ubuntu from the cd.
I can no longer boot to any cd, usb or dvd that is Windows based, as in my repair cd.
As a newbie I am lost as to how to get past this and any help would be appreciated.

Try reinstalling grub2 bootloader [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708). If you just want to get windows booting then install lilo from the live CD. (In the following form it's a windows equivalent bootloader).

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore warnings as they relate to using lilo to boot linux

---

### Post by Don544 on 2010-10-10
After doing this step I no longer boot at all unless I use the Ubuntu CD, the windows cd repair tool I have boots fine on my other machines but this one will only boot to the Ubuntu cd and no other

---

### Post by oldfred on 2010-10-10
So we can see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Don544 on 2010-10-18
So after a few days of trying different suggestions from here and elsewhere I wiped the machine and started over with a reset bios.
This was needed because for some reason after the attempt to install Ubuntu the machine would no longer display the boot sequence on the monitor unless it was booted from the Ubuntu cd, do not know how but I can only assume that a driver got messed with in the install.
Then after a reset of the bios and a clean install of windows  I used WUBI on Ubuntu.
Machine now boots fine but have another problem I will post in new thread.

Thank You for your help.
Don

---

