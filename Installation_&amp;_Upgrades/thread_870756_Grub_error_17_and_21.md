---
title: "Grub error 17 and 21"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by chris_tikva on 2008-07-26
Hello, I've just installed ubuntu and now can't get my computer to start.

What I did was this:

From the live CD I selected "install". When it asked me to choose the disk, I choose "use all disk" and picked an external drive ( with the intention of keeping windows XP as an alternative ). 

Installation proceeded without a problem but when I restarted I got a grub error 17. I changed the external disks around and that changed it to error 21 but still would go no further. I can't find any info on what these errors are and, more importantly, what the solution is. 

I can still get into my system by booting off the live CD but windows XP which was on drive c: seems to be no longer available.

Any help gratefully received.

Chris

---

### Post by ftwww on 2008-07-26
had the same problam last weekend, here's how i solved it:

disconnect ALL your hard drives, including internal ones, except the one you want to install on. install, restart and shut down. reconnect your drives and restart. done.

there surely is a better way by configuring grub correcctly, but we newbies still have to learn it.

btw: it's not an ubuntu specific problem. i've tried several linux distributions and it's been the same with all of them. and ubuntu was the clear winner in that little competition.

hope this was helpful - ralf

---

### Post by Sef on 2008-07-26
> I can still get into my system by booting off the live CD but windows XP which was on drive c: seems to be no longer available.

Applications > Accessories > Terminal

then copy/paste or type this code:

```
sudo fdisk -l
``` Small L; copy/paste the results here.

---

### Post by logos34 on 2008-07-26
> **ftwww said:**
> had the same problam last weekend, here's how i solved it:

disconnect ALL your hard drives, including internal ones, except the one you want to install on. install, restart and shut down. reconnect your drives and restart. done.

+1

save yourself troubleshooting time and reinstall.  The only thing is if you have windows on the internal drive and want to access it, you have to add it manually.

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support internal device 

this will edit fstab for you, adding a windows entry so it automounts at boot.

---

### Post by chris_tikva on 2008-07-27
Thanks, folks. 

I did a reinstall with just one disk in the usb but leaving the internal drive as it was. This works fine now but there are a couple of, probably naive, questions left.

First, if I have a second disk plugged into usb it will give the error again but if I change which disk is plugged into which usb then it works fine. Is there a hierarchy of usb sockets? Will it be ok as long as I have the ubuntu disk in the one which boots happily now?

Secondly, I had the grub boot loader installed when I was using the live CD and it gave me the option of windows or ubuntu. Now I'm using the usb disk based version I first get a list of options including various flavours of ubuntu and also windows. If I select windows I get a second list which is what I had when I was using live CD.

Am I right in thinking that grub is now installed in two places? Is there an easy way of getting rid of the, now superfluous, second menu?

As a third question, if I plug my ubuntu disk into another computer, can I boot into it and run ubuntu there as well? Or is it not as simple as that?

Thanks for your help!

Chris

---

### Post by logos34 on 2008-07-27
2.  Sounds like you need to restore the windows bootloader to the internal drive.  Boot from the XP install cd> 'R' for recovery console>type **fixmbr** at prompt

Or use the super grub disk to restore (see link my sig)

3. Hardware differences may prevent that (like if you installed on AMD platform but plugged it into and tried to boot on Intel machine)

---

### Post by chris_tikva on 2008-07-29
I think I see a bit more light now. I looked at the boot.ini file and found a reference to ubuntu which must have been added when I was using the live CD. I deleted that line and now when I select windows it goes straight in, no messing. 

Also I tried booting with the external drive unplugged and got error 21.

From this I deduce that the MBR in my internal drive now points to the /boot in the external drive which then points back to the internal drive when windows is selected. Which means that I can only get into windows if the ubuntu disk is plugged in! Or use a separate boot disk. Am I correct? Is there a better way?

I guess all this is obvious to the linux savvies but it provides hours of good clean fun to the newbie!

Thanks for the tips :)

Chris

---

### Post by logos34 on 2008-07-30
Do like I said above, or as ftwww suggested.

Restore the windows bootloader to the internal drive MBR.  Then write grub to the external mbr (using live cd).  Then you just toggle the bios boot drive when you want to boot ubuntu.

---

### Post by chris_tikva on 2008-08-01
> **logos34 said:**
> Do like I said above, or as ftwww suggested.

Restore the windows bootloader to the internal drive MBR.  Then write grub to the external mbr (using live cd).  Then you just toggle the bios boot drive when you want to boot ubuntu.

Thank for that. I've now done this but still have problems. If I boot from the external drive it happily reads the grub menu but when I select ubuntu it gives me either an error 15 or an error 17 depending on whether I have a memory stick in the other usb port or not. It still works happily either from supergrub disk or by booting off the internal hard drive.

Is the (hdn) allocation dependent on where the computer is booted from, in which case does the menu.lst need editing? Or am I off track!?

Thanks for the help

Chris

---

### Post by confused57 on 2008-08-01
> **chris_tikva said:**
> Thank for that. I've now done this but still have problems. If I boot from the external drive it happily reads the grub menu but when I select ubuntu it gives me either an error 15 or an error 17 depending on whether I have a memory stick in the other usb port or not. It still works happily either from supergrub disk or by booting off the internal hard drive.

Is the (hdn) allocation dependent on where the computer is booted from, in which case does the menu.lst need editing? Or am I off track!?

Thanks for the help

Chris
When you boot first to your external drive with Ubuntu, it needs to be designated as (hd0) in the line with root, e.g. "root (hd0,1)".  In the grub boot menu, make sure the first Ubuntu entry is highlighted, press "e", highlight the line with root, press "e" again, change root from (hdx,y) to (hd0,y), press "enter" then "b" to boot...y means leave this value as it already is(0,1,2...).  This is temporary, if it works, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
also change the root in the line with #groot.

---

### Post by logos34 on 2008-08-01
nm--confused57 beat me to it.

How's it goin confused57?

---

### Post by confused57 on 2008-08-01
> **logos34 said:**
> nm--confused57 beat me to it.

How's it goin confused57?

Hi logos34,
Thought I might beat you to the punch, since you weren't logged in at the time, so I decided to help out a little in my meager sort of way. 

Doing well, thanks for asking.

---

### Post by chris_tikva on 2008-08-01
Brilliant!

I've added a new entry to the menu.lst with hd1 replaced by hd0 and now it works fine.

One further question, where does the "root" string in the kernel line come from? In the examples I've read it seems to be a device name such as:

kernel /vmlinuz root=/dev/sda2 ro vga=791

but in the menu.lst file which is on my unbuntu disk it is a long string starting with "UUID=". If I wanted to add another entry for another operating system how would I know what to use here?

Thanks again

Chris

---

### Post by logos34 on 2008-08-02
> **chris_tikva said:**
> 
One further question, where does the "root" string in the kernel line come from? In the examples I've read it seems to be a device name such as:

kernel /vmlinuz root=/dev/sda2 ro vga=791

but in the menu.lst file which is on my unbuntu disk it is a long string starting with "UUID=". If I wanted to add another entry for another operating system how would I know what to use here?

to get the uuid just run any of the following commands:

sudo blkid

sudo vol_id /dev/sd?

ls -l /dev/disk/by-uuid

you can also just continue to use the 'root=/dev/sd?' format

---

