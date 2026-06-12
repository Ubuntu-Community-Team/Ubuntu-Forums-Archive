---
title: "2 OS, no boot loader installed."
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by gavinguinness on 2007-05-07
Hey all.

Until 30 mins ago, I was dual booting XP and SUSE 10.  Due to Dell's recent decision, I thought I should start to look at Ubuntu.

I removed the SUSE partitions, and used my XP disk to FIXMBR.  So then I had a normal booting XP machine and about 60gb of free space on my second HDD (previously used by SUSE).  Great, all set.

Then I installed Ubuntu, which initially wanted to resize my XP partition, it didn't seem to see the free space during installation, so I told it to use the free space on the second hard disk.  Second or third option I think at the partition stage.

Installation went smoothly, no problems.  But when I reboot, The PC goes straight into XP.  No Boot Loader.  

I've installed Linux many times, but the boot loaded, usually GRUB, always seems to get installed automatically, I've got no experience in this area.

Can I manually install Grub?  Any ideas, help?  Appreciated.  ;)

---

### Post by GrueTamer on 2007-05-07
I don't know why grub didn't automatically install, but you can install grub from the terminal (assuming that you want it on the first hard drive's master boot record) with the ```
grub install
``` command.  To do this, use your Ubuntu livecd and mount your Ubuntu root hard drive, then run the command.  If things go wrong, just type ```
grub
``` instead and then specify the root device (where the grub files are) with ```
root (hdX,Y)
```.  Then, to install, do ```
install hdX
```

I hope this helps!

---

### Post by gavinguinness on 2007-05-07
Cheers.  That's the kind of thing I expected.  Just didn't know where to start.

I'll report back shortly...

---

### Post by bulldog on 2007-05-07
Boot from the other hdd,and I'm pretty sure GRUB is in the MBR :) 

A common problem with multiple hdd's.
GRUB will be installed to (hd0) by default,which isn't necessarely  the boot hdd.

---

### Post by gavinguinness on 2007-05-07
I'm not having much luck.  

The first command drops me into a GRUB > command with a list of options.  Indeed one of those options is ROOT as you suggested.

But I've not had any joy entering values as in your example, Specifying the location of the XP installation (existing MBR) returns the error (ERROR WHILE PARSING NUMBER).

I know that it's my lack of understanding that is the problem however, so if anyone could give me some additional guidance, that would be fantastic.

Thanks

---

### Post by gavinguinness on 2007-05-07
OK.  I've got my syntax and drives figured out now.

As you said Bulldog, seems my Grub files are presently on hd0.  I don't seem to be able to install them onto my exisitnig boot drive.  Moans about permissions...

Can anyone help?

---

### Post by gavinguinness on 2007-05-14
Weird stuff going on here still...

Managed to screw things up completely on my PC's MBR during the last few days.  All backed up though so no real damage ;)  Just a pain in the A** re-install.

Thing is though, I've just reinstalled Ubuntu and rebooted, I had Grub!  Excellent.
I booted into XP just to burn off a DVD, then rebooted to fire up Ubuntu...  GRUB had bloody vanished again!  

So the PC still only boots into Windows, again!

I've never had so many problems with boot loaders, if fact, I've never had any problems before! LOL

If anyone knows of an idiots guide to restoring my GRUB and retaining dual boot ability, I would be so grateful.  I've read loads of articles and they are beyond my present knowledge.  The comments above, were very helpful, but i've yet to get them to work.

Thanks again.

---

### Post by bulldog on 2007-05-14
Well it isn't that hard :) 
You have two hdd's,which are named (hd0) and(hd1) by GRUB
The best way to do is install windows and make this the slave hdd.
Install ubuntu and grub on the same hdd and make this one the master boot device.
This would be (hd0) as grub would name it.

Now you can boot ubuntu,but not windows,to let windows boot,you'll have to edit the menu.lst and
add some line to your windows entry.
I'll give you mine for example,don't change the boot partition,just add some lines to it.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	(hd1,0)+1

```
Make the hdd with ubuntu installed,the master boot device (hd0) and the windows hdd second hdd in your BIOS.
To reinstall grub to the MBR of the ubuntu hdd,
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

If you don't get it to work,give a PM and I'll return tomorrow [provide the link to the topic in the PM please]

---

