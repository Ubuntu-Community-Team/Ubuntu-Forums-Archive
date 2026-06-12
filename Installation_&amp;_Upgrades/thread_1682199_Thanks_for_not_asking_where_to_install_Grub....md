---
title: "Thanks for not asking where to install Grub..."
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by The MAX on 2011-02-05
So I install Ubuntu 10.10 on a multi-drive, dual boot with windows 7 computer. At almost the end of the install, I see "running grub-install sda" or whatever it is. sda is my windows drive.

So rather than asking where to install the bootloader or give you the option like it used to, it just did it to my "first" drive. 

What the hell? Now my Windows MBR is gone. I like to maintain that so if my linux drive dies I can still boot into windows via the old windows boot loader.

Possible to move Grub2 to my other drive and repair windows 7 drive MBR?

---

### Post by uRock on 2011-02-05
Windows 7 repair disk can do this with ease.

When running an install where you prefer to have each OSes MBR intact it is best to disconnect the other drives or use the alternate installer.

You can reinstall grub where you want it using the LiveCD.

Cheers,
uRock

---

### Post by kansasnoob on 2011-02-05
The option to choose where to install grub is now only available if you choose “Manual partitioning”, I discussed that here along with other changes to the installer:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I'm not sure what the proper drive designation of your Ubuntu drive is, I'll assume you do, but all you really need to do is boot into your newly installed Ubuntu and run the command:

```
sudo grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**
```

You would of course substitute the proper device designation "b", "c", etc for the red X.

Then you could even create a Windows readable MBR while booted into Ubuntu by running:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Or if you have a Windows recovery disc you can follow the "How to restore the Windows Vista or 7 bootloader" section of this guide:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by The MAX on 2011-02-05
And I just did something that was a prime example. Was playing with dynamic disks to span two discs and rendered my Ubuntu Partition unbootable. lol 

I'm going to attempt to repair windows 7 mbr (i've done it before with windows xp, seems similar) and reinstall 10.10, this time with only one disk plugged in.

Thanks guys, I was mostly just ranting. :p

---

