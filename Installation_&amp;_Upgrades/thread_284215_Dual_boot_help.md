---
title: "Dual boot help"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by WorfSOM on 2006-10-25
Hi all.

I recently made the jump from Windows to Ubuntu Linux on my computer a few days back, and i do think its fantastic, even if it will take me a while to get used to it.

The thing is though, i still need access to certain applications for my university work, such as Dreamweaver MX, Visio, Photoshop and Visual Basic etc.

So, i was thinking of adding a slave HD so that i could dual-boot Windows the odd few times i need it, just for these specific apps.

My question (finally! lol), is can i add the slave HD with Windows to the computer and will GRUB detect it immediately?

Or, as i have been told elsewhere, would i need to reinstall Ubuntu again for GRUB to detect the HD with Windows when its being installed?

Or is it neither of those options? lol

Sorry if this sounds like such a stupid question, but any help is much appreciated.:)

---

### Post by aarbear26 on 2006-10-25
[SIZE=2]you can install the second drive and have windows run on it. But after you install windows you will no longer see grub, windows kinda wipes it out.

You do not need to completely reinstall ubuntu after this point though. I'm not sure about the normal install CD, but with the alternate install Cd, you can choose what to install and what not to. You can tell it to just install grub by hitting escape somewhere in the early stages of install and then going to grub on the list that comes up. After you install grub just hit escape again and go to the end of the list.  I've done it before and it worked well, I'm not sure is the process is that cut and dry but with a little common sense about the names in the escape menu you should be ok.[/SIZE]

---

### Post by acolic on 2006-10-25
Hi,

you will need to add a line to your grub menu to allow you to boot into windows on your slave drive.

I have the same setup as you do, one hard drive for ubuntu, another for windows 98. From the grub menu I can boot into either drive.

Check the ubuntu docs for a FAQ that explains how to set up a dual boot system using two separate hard drives.

btw the way I did it was to unhook the ubuntu hard drive and connect the windows hard drive. Install windows to it and set it up to be the slave master. Then reconnect the linux hard drive and set it up to be the master drive. Then add the entry into the grub menu.

Alex

---

### Post by Rhubarb on 2006-10-25
A slightly less fiddley way to do this would be:-

Windows tends to be very picky about where it placed on your system.
It likes to be on the primary master hard drive.

Your best bet is indeed to wipe Ubuntu (I know it's hard to even think about doing it :( ).
Then install windows (it's best here to specify the size of your ntfs partition - say 20GB or so).
Then install Ubuntu - specify that it should install in unused space.
Grub will automatically detect windows and you'll have a nice menu on startup.

---

### Post by bulldog on 2006-10-25
Do what acolic says,just unplug your Ubuntu hdd and install windows on your second hdd.

Then plug the ubuntu hdd [ubuntu master--windows slave] on and boot into Ubuntu.

Now you have to alter your menu list.
```
gksudo gedit /boot/grub/menu.lst
```

Put the following lines to the bottom of the list.
```
### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

Save the file and close it.


Now you can boot Ubuntu and Windows from GRUB.

If you run into trouble you can set the slave [windows] as bootdevice and boot into windows without GRUB.

---

### Post by WorfSOM on 2006-10-25
Thanks everyone for the advice.

When i have some free time i will try what has been suggested, and see what works for me.

Thanks again.:)

---

