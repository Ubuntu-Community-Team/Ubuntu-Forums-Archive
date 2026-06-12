---
title: "Dual Boot on two h-disks: xp on slave!?"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by alaistair on 2005-03-07
Hello folks...

I am a total newbie at Linux!!

Having said that I have managed to install and boot Ubuntu successfully (albeit after reinstallation to resolve error code 18, by making a smaller /boot section at the beginning of the drive)  :D

The 'minor' problem I am having now is that I can no longer get into windows xp! I setup Ubuntu on the primary 8.4 GB hard disk and after the installation it told me it had detected another os, i.e xp on the slave hard drive, and do I want to install GRUB to manage it!? I did so and everything seemed to go smoothly.  GRUB seems to load fine and when I select Ubuntu everything boot a. ok!

When I select xp it displays the following:

Booting 'Windows NT/2000/XP'

root    (hd1,0)
  Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader  +1

And that is all I get...with a cursor that quite happily flashes at me until the power runs out!!   ](*,) 

 :?: Is it possible to have xp boot from the slave drive? And if so what do I need to do to make it so!!

Thanks for any advice

Alaistair

---

### Post by kamstrup on 2005-03-07
Hmmm from the output I'd guess that your configuration is "correct". The problem probably rests in that Windows*, as far as I know, want's to recide on the first partition on the primary harddisk (and it want's this to be the active partition too!)

Try "sudo fdisk /dev/hdb" and then set the bootable flag on your XP-partition. I don't know if you're even allowed to do this on your secondary drive..?

I bet ypu could solve this by swapping the IDE cables to your two HDs and then setting the XP-aprtition as bootable ("sudo fdisk /dev/hda" this time then), then you just have to install grub to this new partition, or in the Master Boot Record...

---

### Post by alaistair on 2005-03-07
Thanks for the advice.

I now need to go and find another forum to teach me how to use Linux, cos I have no idea 'how to' or even 'where to' execute those commands - I told you I was a nube!!

If you know of any websites that provide real nubbie guidlines for getting started that would be a great help... and then I can do what you suggested!! :p

Alaistair

---

### Post by GrapeApe on 2005-03-07
If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see map), like this:

     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)
     

This performs a virtual swap between your first and second hard drive.

Caution: This is effective only if DOS (or Windows) uses BIOS to access the swapped disks. If that OS uses a special driver for the disks, this probably won't work. 

From: [http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)

Basically, in your "windows xp" section of menu.lst add
   map (hd0) (hd1)
   map (hd1) (hd0)

Unfortunately I haven't done this in grub so use at your own risk and read the linked web page.  I've done it in lilo though and it works.

---

### Post by llama on 2005-03-07
[QUOTE=GrapeApe]If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see map), like this:

     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)
     

This performs a virtual swap between your first and second hard drive.

Caution: This is effective only if DOS (or Windows) uses BIOS to access the swapped disks. If that OS uses a special driver for the disks, this probably won't work. 

From: [http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)

Basically, in your "windows xp" section of menu.lst add
   map (hd0) (hd1)
   map (hd1) (hd0)

Unfortunately I haven't done this in grub so use at your own risk and read the linked web page.  I've done it in lilo though and it works.[/QUOTE]

i do the same thing with grub, works great for me.

---

### Post by alaistair on 2005-03-07
Ok I think I am getting the hang of this...

I have opened a root terminal window in ubuntu and navigated to the /boot section and typed grub, which displays the following:

 GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>

I then type in:

grub> map (hd0) (hd1)
grub> map (hd1) (hd0)

There was no response to say that I had made any changes of any kind, am I doing this the right way?

Thanks in advance

Alaistair

---

### Post by kamstrup on 2005-03-08
Sorry I didn't know just how *nube* you where. Sometimes people call themselves nube even when they know a heck of a lot more than I do :) (I don't consider myself that nube anymore =D)

[http://ubuntuguide.org/](http://ubuntuguide.org/) is a great place to learn everything you'll need (and more).

About you issues...
In you root terminal type 'gedit /boot/grub/menu.lst' or type 'sudo gedit /boot/grub/menu,lst' in a normal terminal (Apps->Sys.->Terminal). The file /boot/grub/menu.lst is the grub bootloader configuration file. Scroll down to the section looking like this...

title Windows NT/2000/XP
root (hd1,0)
savedefault
makeactive
chainloader +1

- it's probably allmost in the bottom of the file. Then add the lines

map (hd0) (hd1)
map (hd1) (hd0)

such that it looks like this:

title Windows NT/2000/XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1

The line 'root (hd1,0)' might have to be changed to 'root (hd0,0)' now, but trying it out wont hurt.

Save the file, reboot and watch the magic! (hopefully)

Cheers

---

### Post by alaistair on 2005-03-08
he he I should have been more specific about how 'truly' *nube* I really am!!

followed your instructions, which were exactly what I needed; both operating systems now boot without any problems.

thank you for patience and expert assistance. :-P 

on to the next hurdle...

Alaistair

---

