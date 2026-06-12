---
title: "GRUB &quot;Error 15&quot; -- one thing to check for"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by jonrkc on 2005-05-25
There are dozens of posts here (and elsewhere) about GRUB failing to boot, with an Error 15 (file not found) right about at stage 1 of the process.

I spent about seven hours reading posts here and on other forums and tried various suggestions and I always got Error 15 even though GRUB reported there were no errors after it installed the boot record to the MBR.

Finally I was looking at my notes for one last time and read what I had very carefully copied from the screen:

```

Kernel /boot/vmlinuz  root=/dev/hdb1  ro  acpi=on  resume=/dev/hdd5  splash=silent

Error 15: File not found

Press any key to continue...

```

Suddenly it hit me: The file was not found for good reason.  I'd read that message a dozen times or more, and found the kernel file in the right location, but never noticed that in /boot it has its FULL NAME, and what GRUB was looking for was just "vmlinuz"!

So, assuming that GRUB probably doesn't understand about symlinks, I copied the kernel, giving it the short name.  

I was able to boot without a problem for the first time from this new drive.

It's too late to test if a symlink would work (and save disk space...) but I'll experiment with that tomorrow.

Meanwhile I hope maybe this post will save somebody seven hours of beating their head against the monitor as I did.  It is not good for the monitor.

P. S.  I had to edit /boot/grub/menu.lst extensively to get the right drive designations.  I don't doubt that there's a way to avoid that by using the right utility programs with GRUB, but I did it by hand and it worked.  (I had copied everything from a smaller disk to a much larger one, so the references were all still to the smaller disk.)

---

### Post by Kamping_Kaiser on 2005-05-25
[QUOTE=jonrkc]There are dozens of posts here (and elsewhere) about GRUB failing to boot, with an Error 15 (file not found) right about at stage 1 of the process.

I spent about seven hours reading posts here and on other forums and tried various suggestions and I always got Error 15 even though GRUB reported there were no errors after it installed the boot record to the MBR.

Finally I was looking at my notes for one last time and read what I had very carefully copied from the screen:

```

Kernel /boot/vmlinuz  root=/dev/hdb1  ro  acpi=on  resume=/dev/hdd5  splash=silent

Error 15: File not found

Press any key to continue...

```

Suddenly it hit me: The file was not found for good reason.  I'd read that message a dozen times or more, and found the kernel file in the right location, but never noticed that in /boot it has its FULL NAME, and what GRUB was looking for was just "vmlinuz"!

Meanwhile I hope maybe this post will save somebody seven hours of beating their head against the monitor as I did.  It is not good for the monitor.
[/QUOTE]

Sometimes it takes way to long to find the right info, doesnt it?.
one thing you can do on older BIOSs (not sure about new ones) is to manualy set the hard drive parameters, not use "auto".
If using "IDE hard drive detection" (or whatever your BIOS calls it) press "2" and then ok, not use the defaults (which has 0s in the line). This has - if i am remembering the right fix - solved our problems at ITShare.

OH, and thanks for that vmlinuz tip, might look into it. ;)

---

### Post by jonrkc on 2005-05-26
I did try using a symlink to point GRUB to the right kernel, and it worked.  I wasn't sure a fairly low-level process like GRUB would be equipped to understand symlinks.  So if space is precious on your system, you can save a bit by doing, in /boot/, this:

```

ln -s vmlinuz[and the rest of its full name] vmlinuz 

```

It's also a neater way to do it, though if you looked under my desk you'd discover that neatness means very little to me.

---

