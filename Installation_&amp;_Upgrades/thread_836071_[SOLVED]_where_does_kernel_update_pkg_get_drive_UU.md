---
title: "[SOLVED] where does kernel update pkg get drive UUID?"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by evanb on 2008-06-21
A few weeks ago I swapped hard drives in my system running 64-bit Gutsy by essentially copying the partition from one drive to another. This worked fine, except that the new drive had a different UUID and I had to edit menu.lst to use the new one so Grub could find the kernel image.

All was well until this evening, when a system update installed a new kernel (2.6.22-15), and the package installer dredged up what I presume is the old drive's UUID from some place and stuck in in the menu.lst it created. I would like to find that place and change it to the correct UUID so I don't have to spend another couple of hours figuring this out again the next time it happens.

Can someone enlighten me?

---

### Post by louieb on 2008-06-21
Look in the automagic section of menu.lst. you want to change the **kopt** option. Be sure to read and follow the editing instructions and the beginning of the section. 

```
# kopt=root=UUID=fdd1413c-1ad8-4353-be07-dcda96b8a21d ro

```

---

### Post by evanb on 2008-06-21
Ah, I see. Hidden in plain sight. :)

With the magic word 'kopt' I was able to find this useful explanation of grub as used by Ubuntu:

[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

Thanks for your help.

---

### Post by mhousel on 2008-06-21
I have a similar problem, I think,

I re-partitioned and moved Ubuntu to a new partition using LVPM but now Ubuntu won't start up and ends up at initramfs

I see that the mounting of the root file system does not show OK and I'm guessing it's because the UUID is no longer correct.

So, where do I find the correct UUID of the partition that Ubuntu is installed in to change in the kopt line described above?

Thanks

---

### Post by lswb on 2008-06-21
In a terminal try 

   sudo blkid

It should print out the uuid of all installed block devices. After you change menu.lst check /etc/fstab also. Your problem may really there rather than in grub.

---

### Post by mhousel on 2008-06-21
What should fstab look like? This is what is in mine. 

union / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda4 swap swap defaults 0 0

Also, the UUID's look totally different.

OLD = 54D4865ED48641EA

NEW = 421dbea3-62ab-4da4-9f29-c330d286b3a0

Should menu.lst entries look something like this?
Nowhere can I find an ubuntu/disks directory.

# kopt=root=UUID="421dbea3-62ab-4da4-9f29-c330d286b3a0" loop=/ubuntu/disks/root.disk ro

...
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID="421dbea3-62ab-4da4-9f29-c330d286b3a0" loop=/ubuntu/disks/root.disk ro splash
initrd		/boot/initrd.img-2.6.24-19-generic
...

---

### Post by lswb on 2008-06-21
mhousel, The 1st line in in your fstab:

union / unionfs rw 0 0

shows that / is a disk of type "unionfs" and that device "union" is being mounted as root. The problem is, I don't see a unionfs type anywhere in the documentation for mount or fstab, and the name "union" is not correct for a disk device. What is the LVPM program you mentioned?

Also, normally a linux /etc/fstab will have a line that mounts /proc and I don't see that either, did you just leave it out when you posted?

I suggest editing fstab like this:
comment out the "union" line (put a # character at the start of the line"

Add this line just above or below it:
UUID=421dbea3-62ab-4da4-9f29-c330d286b3a0 / ext3 relatime,errors=remount-ro 0 1

I've cut and pasted the uuid you showed in your post, make sure your fstab matches the output of the blkid command for the disk being booted.

If the first non-comment line in your /etc/fstab does not begin with "proc", put this line at the top:

proc  /proc   proc    defaults   0   0

If you still have problems start a new thread since this one is marked SOLVED.

Good luck.

---

