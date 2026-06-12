---
title: "rm -rf /*"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by dracofusco on 2011-07-13
Okay, for some reason, 11.04 <beep> up my machine big time to the point I was unable to do anything with it, and I couldn't delete anything. So, being at the last resort, and this Linux machine not being my main machine, I ran the command of destruction "**sudo rm -rf /***"
It did it's job perfectly, and erased every last thing on the PC except BIOS itself. Now, I can't boot from a CD still, I just get grub_rescue. Is there anyway to do a reinstall of Ubuntu or another Linux distro through grub_rescue, or bypassing it? Or did I just cast this old machine to the graveyard? Any help is appreciated, I'd like to be able to use this machine with Linux, and I don't think it's ready to hit the grave *just yet.* Thanks for the help!

---

### Post by sikander3786 on 2011-07-13
Grub or the grub_rescue prompt has nothing to do with booting a CD. Just make sure that the boot order is properly set in Bios and also, make sure your CD drive is actually working. Or, you can also try to boot a Live USB if the Bios supports it.

BTW, that is not the ideal method to remove Linux from your HDD ;)

---

### Post by Gawains Green Knight on 2011-07-13
Thats funny.... yes, go to your bios and boot from a cd or usb (if your computer isn't too old).

---

### Post by gdonwallace on 2011-07-13
That command will erase everything on the hard drive but not in the Master Boot Record, that takes a low level format to erase the MBR, which you can get from the manufacturer of the hard drive.

To boot from CD, you will need to check your BIOS and ensure that CD is the first item in your boot list.  That should do it.

---

### Post by mörgæs on 2011-07-13
If you want to completely wipe the hard drive, Killdisk is a good program. There are links to it here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Normally you don't need this, though. Just do a live boot of Ubuntu and install, if you want a fresh system.

---

### Post by spcwingo on 2011-07-13
Another way to wipe the disk would be to zero it from a live environment:

```
sudo dd if=/dev/zero of=/dev/sda
```

Of course, this would be assuming that sda is the drive that you want wiped.  If I'm not mistaken this should also wipe the MBR.  If not, that can be accomplished with this command (again from a live environment):

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

One more option is Darik's Boot and Nuke (DBAN):

[http://www.dban.org/]("http://www.dban.org/")

---

### Post by YannBuntu on 2011-07-14
Hi,

- if you have several OSs on your computer, you can uninstall one OS by using this little tool : **[OS-Uninstaller]("http://ubuntuforums.org/showthread.php?t=1769489&highlight=os-uninstaller")**
- if you have only one OS on your computer, as Mörgæs says, there is no need to wipe the disk if you install another OS above it. (except if you had ultra-confidential data that you want to make disappear forever)


Nota: for newbies reading this thread, let's remind that **"sudo rm -rf /*" and commands given above by spcwingo are very dangerous commands as they wipe the disk !**

---

