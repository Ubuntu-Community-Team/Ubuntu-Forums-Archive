---
title: "Cannot Mount Selected Partition - NO BOOT"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by dkatz on 2007-03-05
I'm installing and at the reboot I get the os menu and choose Ubuntu and get this error:

Booting 'Ubuntu, kernel 2.6.15-26-386

root (hd3,1)

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sdd2 ro quiet splash

Error 17: cannot mount selected partition

I'm installing on a scsi drive, created a new partition alongside my old fat32 partition.

I wonder if Grub might be confused and trying to boot from the wrong place. Without linux, how do I run Grub to change parms?

Any help will be deeply appreciated - been trying for days to get rolling. btw, debian installs, but cannot get the video working right, so back to trying Ubuntu (my first choice).

---

### Post by mikewhatever on 2007-03-05
Try booting with the Live cd you probably have and post the output of 
sudo fdisk -l
a live session will work too, but you'll need removable media.

---

### Post by bernied on 2007-03-05
When you boot you are already 'running' grub. You just need to interrupt it before it tries to boot that linux install. 

Do you get a boot menu? If yes, then hit 'c' for a command-line.
If you don't get a menu, hit escape as soon as you get past the bios screens, then hit 'c'

Or, you can select the menu item for the linux install, then hit 'e' to edit the commands, then you can try different boot locations.

Once at a command line, it's a bit of a new world. But a few hints:
- you can use Tab-completion, if you just hit the Tab key you get a list of commands.

To boot linux, you need to use
- root (hdA,B)
- kernel /location/name options root=/dev/XdYZ
- initrd /location/initrdname
- boot
The trick is knowing the values for A, B, X, Y and Z

You can also use the find command, like
- find menu.lst
Should return a partition name, which will probably be the one you want in the root command

Does this help?

---

### Post by bernied on 2007-03-05
You don't need to setup grub again, as grub is already booting. You probably only need to tweak your /boot/grub/menu.lst file, which is where all those menu items are stored.

---

### Post by dkatz on 2007-03-05
Thanks for the suggestion. Sorry to be such a newbie, but I don't know how to post the output to this forum. I tried to drag the output from the desktop to my usb drive which appears as WD320 in the file browser, but I don't have permission to write there, perhaps because I've booted from the cd...

Anyway, the /dev/sdd2 entry seems to be what I want to boot from. It's marked bootable and is the one I thought I installed into.

I got into grub but find menu.lst says file not found, and I can't figure what to use for the other parameters. I tried root (hd5,1) and got 'File system is extfs, partition type 0x83, so I think I'm on the right track, but can't figure the other parms I need. Thanks!

---

### Post by dkatz on 2007-03-05
Aha, I figured the remaining parameters out and appear to be booting! Will grub remember how to do this, or do I need to reconfigure?

Thanks![http://www.ubuntuforums.org/images/smilies/guitar.gif](http://www.ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

### Post by bernied on 2007-03-05
You need to edit that file /boot/grub/menu.lst and change the entry to what works.
I have to go - back a bit later

---

### Post by dkatz on 2007-03-05
Ok, I spoke too soon - after lots of messages I get this message:

Alert! does not exist. Dropping to a shell!

BusyBox v1.01.... built-in shell (ash)

Where do I go from here?

Thanks.

---

### Post by bernied on 2007-03-05
OK, you are getting there. What happened there is probably the kernel not finding its root filesystem. But at least you found the kernel.
I'd suggest that you reboot, get a grub menu, select the ubuntu line, then hit 'e' to edit, and edit only the line with root, so that it says
- root (hd5,1)
leave the rest of the entry as it is, then hit 'b' for boot.

Does that get you there?

---

### Post by bernied on 2007-03-05
And, incidentally, how many disks have you got in there and what type are they? 
And, do you have any external drives attached when you boot, and were they attached when you did the install? The disk (hd5) that you are booting to is usually the 6th disk.

As an earlier poster suggested, the output of ```
sudo fdisk -l
```might be informative.

---

### Post by dkatz on 2007-03-05
Bingo! The gui is a thing of beauty when you've worked so hard to see it!

Thanks 1000 times.

---

### Post by bernied on 2007-03-05
You're very welcome. I agree it's worth the effort.

But have you fixed up your menu.lst file yet?
There are two bits you need to change. The first is the grub entry itself, which will look something like this (this is mine, you will have a different partition specified):
```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```You just need to change the root line so it's like the one you used at startup (you weren't editing the file when you were messing with it in grub). You need to change this line for any other ubuntu entries as well (like single-user mode)

The other bit is a bit more obscure and you'll only notice its effects the next time you install a new kernel, which could be months away, but will happen. If you don't fix this, when you install a new kernel, the menu entries will revert to how they are now, and you will have to boot manually again. The bit you are looking for looks like this:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```It's that last line that you need to change to your boot drive. The options in this section get used by the update-grub script, which is invoked by the package manager whenever you install a new kernel. You can run this yourself like this (from a terminal):
```
sudo update-grub
```

And incidentally, if you haven't figured out how to edit files with administrative rights, you can do something like:
```
gksudo gedit /boot/grub/menu.lst
```or```
sudo nano /boot/grub/menu.lst
```

Have fun
Bernie

---

### Post by dkatz on 2007-03-05
Thanks for your very clear instructions. I've done the edits on menu.lst and I'm off and running.

---

### Post by lakamsani on 2007-03-11
Hi,

I installed Ubuntu 6.10 server on a Dell  Dimension 8300 with a single 120GB SATA drive. During installation I let it use its defaults for partitioning. I asked it to use the entire drive for Linux. It identified my disk as SCSI2(0,0,0,) sda. It put the root partition (ext3) on sda1 and swap on 5 (sda5 I think). At the end of the installation it ejected the install CD and started to boot but it is unable. 

First I see the Dell BIOS startup messages and logo (F2 to setup etc.). Then I see this:

```

Grub Loading Stage 1.5 ....

Grub Loading  (Esc for menu) 

```

then the screen goes blank for a split second and I see:

```

Starting up ...

```

Then instead of starting Linux it goes back to the Dell BIOS startup screen and the cycle repeats. 

So I pressed "Esc" to go to the menu and then "c" to get the grub command prompt and then "cat /boot/menu.lst". I see this (plus the single user mode and the memtest)

```
title           Ubuntu, kernel 2.6.17-10-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-server root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-server
quiet
savedefault
boot
```


Is there anything I can do to get this going?  I tried editing the root line to say (sda,0) and some other combinations starting with sd but it does not like (Error parsing number). 

I had success running Ubuntu and Linux Mint Bianca (including Beryl on some of them) on older PCs and Laptops. This Dimensions 8300 is relatively new compared to the others (3Ghz P4 with hyper threading). I guess Ubuntu does not like SATA? Linux Mint and Open Suse 10.2 won't install at all. With Ubuntu server atleast I 'm able install and get to the grub menu.

---

