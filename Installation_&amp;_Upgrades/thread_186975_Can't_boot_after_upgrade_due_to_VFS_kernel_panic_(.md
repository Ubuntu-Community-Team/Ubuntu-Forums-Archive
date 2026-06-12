---
title: "Can't boot after upgrade due to VFS kernel panic (can't open root device)"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Raptor Ramjet on 2006-06-02
Sadly after just doing an upgrade I can no longer boot my Ubuntu machine.  To perform the upgrade I did what I usually do (I started Ubuntu with 4.10 and have upgraded shortly after each release came out) by doing the following:

1 Edit "/etc/apt/source.lst" to replace "breezy" with "dapper".
2 From a terminal call "apt-get update".
3 Call "apt-get dist upgrade".
4 Reboot.

But this time it didn't "just work" and instead of booting I get a kernel panic with the last three error messages I get being:

	VFS cannot open root device "2101" or unknown-block(33,1)
	Please append a correct "root=" boot option
	Kernel panic - not syncing VFS: Unable to mount root fs on unknown-block(33,1)

If its of any use the machine is booted off /dev/hde (primary master of onboard RAID controller but not used in RAID mode) and when I originally installed Ubuntu (back at 4.10) I had to install LILO as GRUB couldn't boot the machine and I got bored of trying to get it to work (why bother as LILO just did the job ;)

For a quick investigation I've just booted the machine off a Knoppix CD and I was able to mount the disks and inspect "/etc/lilo.conf" which looks coorect as it has entries for:

	boot=/dev/hde
	root=/dev/hde1
	image=/vmlinuz
	
I can also see that the "/vmlinuz" symlink is pointing to the new kernel image so now I'm a bit stumped as to why the machine won't boot ?

If anyone has any ideas how I can recover I'd be most grateful !

---

### Post by mbobak on 2006-06-02
I'm still very much a Ubuntu newbie, but, if upgrade to 6.06 gave you a new kernel version (and I'm pretty sure it did) and you have LILO rather than grub, you need to run 'lilo' after the new kernel is in place and before rebooting.

Since you've already rebooted, I'm actually not sure what the solution is.

How can one boot from the CD and then run lilo for the installed system and not for the system that is booted from CD?

So, at least you know what went wrong....perhaps someone else can offer a solution?

-Mark

---

### Post by Ptero-4 on 2006-06-02
To boot off the CD and run lilo on the installed system you can do this:
go into a terminal in the LiveCD (for 6.06 users that is the "desktop CD") and type this.
```

mkdir /tmp/HD
mount -t fs /dev/hde1 /tmp/HD
chroot /dev/hde1 /bin/bash

```

And you're in your ubuntu system. From here you can run lilo and it will be run on the ubuntu you have installed on your HD.

---

### Post by Raptor Ramjet on 2006-06-03
Firstly thanks for the replies.

However LILO was definitely run after the upgrade as I was asked to confirm that it should be run.

But following on from Ptero-4s suggestion it all works fine apart from the chroot command which gives me the error:

"chroot: cannot change root directory to /dev/hde1: No such file or directory"

I've also tried using:

sudo chroot /mnt/HD /bin/bash 

But this gives the same result (obviously with the "/dev/hde1" part of the error message being replaced with "/tmp/HD")

However I am able to do 

ls /tmp/HD 

and this shows me the contents of the drive (i.e. my filesystem).  I was also able to create a file using 

touch /tmp/HD/test

so why chroot says /tmp/HD is not a directory is beyond me ?

So sadly I'm still stuck with an bootable machine and will be grateful for any further suggestions.

---

### Post by Raptor Ramjet on 2006-06-03
Oops that last line should have read:

*"So sadly I'm still stuck with an **un**bootable machine and will be grateful for any further suggestions."*

---

### Post by Raptor Ramjet on 2006-06-05
Well having used another machine to download a copy of the new Ubuntu install CD I booted from it, followed the instructions again, and it worked.

But as LILO was definitely run when I performed the upgrade I find the whole thing most strange.  Ho hum.

But my system boots again so cheers for the advice !

---

