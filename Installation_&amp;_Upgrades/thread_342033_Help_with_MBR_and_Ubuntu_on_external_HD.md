---
title: "Help with MBR and Ubuntu on external HD"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by Deived on 2007-01-19
I installed Ubuntu to an external USB HD while booted to the Ubuntu Live CD. The install went with no problem but now I have a problem when I boot up.

When I attempt to boot without the external HD plugged in, GRUB launches and give me an error (I'm at work so I cant tell when the error is right now, but I can give it later if needed.) However, when I have the HD connected, GRUB starts up fine and I can choose Ubuntu or WinXP.

My question is, do I need GRUB on my MBR of my main laptop HD in order to boot to Ubuntu? or can I fix the MBR so it boots into WinXP when the drive is not plugged in. I dont know why the install modified the MBR on the drive that I was NOT installing Ubuntu on and wasn't expecting that. My laptop has the ability to boot to an external USB drive so I think that's all I need. So... can I fix MBR on my laptop and be OK?


ALSO, if anyone can tell me how to fix the MBR on my main drive without booting to a WinXP CD that would be great. I didn't have much time to look for my disk this morning before I left for work, and would like to fix it on my lunch if I can.

Any help would be much appreciated.

---

### Post by confused57 on 2007-01-19
Here's a guide for restoring your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk can also be used for this purpose:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
see the section on "Situations where Super Grub Disk is useful"

Once you're repaired your Windows mbr so that Windows will boot without your external drive, you can install grub to the external drive, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I've never installed Ubuntu on an external drive, but in theory, this should work...when your external drive isn't connected, your pc should boot Windows.  With your external drive connected and set as first boot drive, you should be able to boot Ubuntu...you'll need to manually enter an entry to boot Windows to your /boot/grub/menu.lst, similar to this:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

taken from this link:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Your Ubuntu root partition was probably set as (hd1,0) during installation, so you'd need to change it to (hd0,0) in order to boot Ubuntu, which you can do by highlighting the Ubuntu entry in your grub menu at bootup, press "e" for edit, & change it, then try to boot.

First thing is to get your Windows mbr restored... then it might be easier to reinstall Ubuntu to your external drive(set as your first boot drive), it's another option.  The alternate install cd allows your to select where to install grub, whereas I'm unsure about the desktop live cd.

There are several threads in the forum about howto install Ubuntu to an external hard drive, you may want to read some of them first.
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28](https://help.ubuntu.com/community/BootFromUSB?highlight=%28)

---

