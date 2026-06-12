---
title: "Can only boot with live CD"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by lenny8088 on 2007-06-14
After a bit of struggling I managed to get Dapper onto a Proliant ML570 that I want to use but now I can only boot successfully with the LIVE cd. Normal boot ends with
```
Non-System disk or disk error
replace and strike any key when ready 
```

And boot with rescue option ends in an ACPI error

Booting with LIVE CD works - but I got to believe there is a better way. I am thinking it's something with Grub but after fiddling with some grub tutorials I haven't gotten any where and I could use some assistance. 

How do I boot to the linux server without using the LIVE CD?

---

### Post by floke on 2007-06-14
Can you post the output of the following - from a terminal type

cat /boot/grub/menu.lst

And also of 'sudo fdisk -l'

---

### Post by lenny8088 on 2007-06-14
Booted with Live CD using linux acpi=off - then from graphical desktop (any way to make that go away?) I did the following.

cat /boot/grub/menu.lst
```
cat: /boot/grub/menu.lst: No such file or directory
```

Output from sudo fdisk -l
```
Disk /dev/ida/c0d0: 200.2 GB, 200293662720 bytes
255 heads, 63 sectors/track, 24350 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device                    Boot          Start            End                Blocks          Id      System
/dev/ida/c0d0p1                         1            18236          146480638+    83     Linux
/dev/ida/c0d0p2        *             18237      18358          979965             83    Linux
/dev/ida/c0d0p3                       18359      24350         48130740          83    Linux swap / Solaris
```

---

### Post by floke on 2007-06-14
Sorry - you need to mount your hard drive partition to check the menu.lst file.
(to make the desktop go away simply boot into recovery mode)

So - from the live cd: (might need to use sudo) - mkdir /home/ubuntu/here
then mount the partition - [sudo] mount [partition - looks like ida/c0d0p1 - so - 
mount /dev/ida/c0dop1 /home/ubuntu/here

and then

cat /home/ubuntu/here/boot/grub/menu.lst

should do it - though you'll know where you installed to so you might have to change the partition entry in the commands

---

### Post by lenny8088 on 2007-06-14
No problem.

Or rather - no problem mounting the partition. menu.lst not there though.

I mounted in /home/ubuntu/tmp so 
/home/ubuntu/tmp/boot/grub has the following files

default
device.map
e2fs_stage1_5
fat_stage1_5
jfs_stage1_5
minix_stage1_5
reiserfs_stage1_5
stage1
stage2
xfs_stage1_5

so just to be sure I mounted c0d0p2 at /home/ubuntu/tmp2

There was no boot directory there but there was a grub and that had menu.lst

cat menu.lst

gives me...
```
title: Ubuntu, kernel 2.6.15-26-386
root: (hd0, 1)
kernel: /vmlinuz-2.6.15-26-386 root/dev/ida/c0d0p1 ro quiet splash acpi=off
initrd  /initrd.img-2.6.15-26-386
save default
boot

title: Ubuntu, kernel 2.6.15-26-386
root: (hd0, 1)
kernel: /vmlinuz-2.6.15-26-386 root/dev/ida/c0d0p1 ro single
initrd  /initrd.img-2.6.15-26-386
boot

title: Ubuntu, memtest86+
root: (hd0, 1)
kernel: /memtest86+.bin
boot

```

---

### Post by floke on 2007-06-14
Why is grub pointing to c0d0p1 if its on c0d0p2?
Have you tried changing this around?
Could also - if this doesn't work - try changing the (hd0,1) to (hd0,2) (absolutely shouldn't work but did for me in the past).
Remember to back up grub first though!

---

### Post by lenny8088 on 2007-06-14
Sorry - but need details. Grub and I don't understand each other well.

How would I point grub to elsewhere? I've tried grub commands in the last few days but since nothing has happened (or so I would think) I am assuming I have it all ackbasswards. 

By backing up I assume you mean just copy the grub directory to somewhere else?

(and I really appreciate the help - thank you)

---

### Post by floke on 2007-06-14
Backup - just copy it with a different name - I always use the convention _backup[date]
so for me it wuld be

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup140607

(of course if its mounted you need to add the /home/blah blah stuff too)

To restore simply reverse the above.

So - to edit the menu.lst file you need to use 'sudo [name of editor] - eg nano or gedit or kate' - so e.g. 'sudo nano /boot/grub/menu.lst' - will open up an editor in the terminal - gedit will open up a text editor in a window etc. (sudo gedit /boot/grub...)

then change the entries you want to edit, save, and try rebooting

(to exit nano use ctrl-x)

good luck!

---

### Post by floke on 2007-06-14
sorry - to point grub elsewhere - change the c0p0d1 to c0p0d2 in the menu.lst file

---

### Post by lenny8088 on 2007-06-14
OK - so ...
I'll move (hd0, 1) to (hd0, 2) for each entry and then I'll change the c0d0p1's to c0d0p2's.

Here goes...

---

### Post by floke on 2007-06-14
NOOOOOO - don't change the (hda0,1) yet - this is just a guess if nothing else works!!!
S***! - Hope its not too late

Oh well

*sigh*

---

### Post by lenny8088 on 2007-06-14
No go.

Still get Non-System disk or disk error....

I tried with the flip of c0d0p1 to p2 and the (hd0, 1) to (hd0, 2) - which failed. So then I tried it with the drive/partition pair back to what it used to be. Still no go. 

Thoughts? 

-A

---

### Post by floke on 2007-06-14
Did you read my last post?
I would try changing the c0d0... without changing the hda stuff.

---

### Post by lenny8088 on 2007-06-14
Ixnay.

Restored the original and tried it again with the lesser changes first. Reboot. Non-System Disk. Then tried the drastic changes and still nothing. 

What it looks like is that I've got Grub all messed up yes? Should I reinstall? If so - how do i prevent it from happening again?

Feels like its so close.

---

### Post by floke on 2007-06-15
Right, when you boot do you even get the grub menu?
if so, you can press 'e' to edit the boot line - simply make the changes you want; press enter; then press 'b' to boot - this will save you time if you want to cycle through the possibilities to locate grub.

If not; how did you install it; and what grub configurations did you make to grub afterwards?

---

### Post by lenny8088 on 2007-06-18
When I boot with no disk in the drive? No, no grub menu - goes right to Non-System disk.

From more reading that I did this weekend it seems like Grub (and LILO) can't handle RAID 5 - it doesn't know what to look at. Something about Stage 1, Stage 2 and a Stage 1.5

Late Friday I reinstalled and didn't load Grub at all - figure I would try with a boot disk. Nothing. Previously I was installing with Grub on the first partition not on the MBR - which for this set up I had read was a bad idea.

---

