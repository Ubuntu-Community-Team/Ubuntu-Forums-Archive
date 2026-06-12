---
title: "regular update now can't boot from HD or CD"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by mnoyes on 2010-10-07
I updated my Ubuntu 10.04 on Dell 1330 and on the next boot it failed. I get a series of messages, the main point seems to be that it can't find the files it needs to mount.

I tried booting from the live cd I used to install 10.04, but it can't boot either due to wrong user id error and maybe trying to boot from wrong kernel?

At this point I am willing to just wipe the hard drive and do a fresh install but how to do that if I can't run the install cd?

Or is there a way from initramfs to solve this?

I tried mount /dev/sda1/mnt but it says cannot read /etc/fstab no such file...

By the way, the update included these files, in case that helps: 
dmsetup
libdevmapper

---

### Post by drs305 on 2010-10-07
There seem to have been a rash of update failures in the past week that result in being unable to boot. In the cases I've dealt with, purging and reinstalling Grub2 has solved the problem.

Of course, you have to be able to boot from the LiveCD. Are you sure you are using the same CD as originally? The first thing that comes to mind is a mixup of a 64-bit CD on a 32-bit system.

The username, password or kernel shouldn't come into play on a LiveCD as it is independent of the system (aside from system compatibility issues such as architecture) . Make sure that the system is in fact booting the CD and not from the hard drive. You may have to change the boot order in BIOS.

*If* you can get to the Ubuntu Desktop, here is the link for purging and reinstalling Grub2:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by mnoyes on 2010-10-07
Thanks for the speedy and helpful reply.

It is the same CD I used to install 10.04, so I know the CD works and the drive works (or have worked).

It is trying to boot from the CD (I made the CD the first entry in the BIOS boot order) and looks like it's booting fine, then the CD just hangs. If I hit escape or a function key I see the code and this is the gist:

(process 410: GLib warning getpwuid_r(): failed due to unknown user id
killed

then several more lines and it seems to stop here:

W: skipping nonexistent file /cdrom/dists/lucid/main/binary-i386/Packages
W: skipping nonexistent file /cdrom/dists/lucid/restricted/binary-i386/Packages

---

### Post by drs305 on 2010-10-07
I did a quick search for the exact error message you are getting and found some hits - preliminary results suggest a bug in 10.04 CD with certain hardware. One user was able to boot by hitting the ESC key, which revealed the "Try Ubuntu" option.

Perhaps you will find something more specific or can try the 10.10 CD, which has reached Release Candidate status.

---

### Post by mnoyes on 2010-10-07
Thanks, I saw that too. I wonder -- the CD is one I burned from the iso on the drupal site and it worked before, so doesn't that suggest the problem is elsewhere?

I will try the 10.10RC idea, though I'm not excited about the prospect of new bugs to deal with...

Is it me, or is this a pretty big problem? I'm a committed Ubuntu user who has had to resolve lots of issues since I started using Ubuntu, but if I weren't, this kind of thing would put me off Ubuntu for sure. It's just luck I didn't update the machine I'm typing on now -- I'd really be SOL. If this happened after upgrading to a beta or RC, okay. But this was a routine update...

---

### Post by drs305 on 2010-10-07
I'd agree that a CD that boots once should boot the next time. A hardware failure can't be ruled out, but you'll probably know if you try another CD.

The update failures surprise me mostly in that I haven't seen anyone come up for a reason that Grub2 is breaking. Normally by now someone has been able to isolate the problem. And although I mention Grub2, I'm not trying to blame the bootloader. There was a grub update recently but from what I know the grub packages were not the ones that had been updated when the failures occurred.

---

### Post by mnoyes on 2010-10-07
Is there a way to update (or revert) grub from initramfs?

---

### Post by mnoyes on 2010-10-09
Still haven't found the solution. I couldn't boot from the internal CD drive, so I used netbootin and made a bootable USB stick with the 10.04.1 ISO. 

I get this error:

/init: line 7: can't open /dev/sr0: No medium found
unable to open '/dev/sda'

any ideas?

---

### Post by presence1960 on 2010-10-09
> **mnoyes said:**
> Still haven't found the solution. I couldn't boot from the internal CD drive, so I used netbootin and made a bootable USB stick with the 10.04.1 ISO. 

I get this error:

/init: line 7: can't open ***_/dev/sr0: No medium found_***
unable to open '/dev/sda'

any ideas?

that is your CD/DVD drive. Check cables on drive, try cleaning as the lens may be dirty.

---

### Post by mnoyes on 2010-10-09
Hmm, I entered bios setup and removed the CD drive from the boot sequence, just USB (1st) and HD. Still get the same message...

(thanks for your help, by they way)

---

### Post by presence1960 on 2010-10-09
once in a while I have a problem with unetbootin and have to redo the image on the stick. Give that a try and see what happens.

---

### Post by mnoyes on 2010-10-14
I finally got a Canonical Ubuntu disk (from a Japanese Ubuntu magazine) and installed 10.04. Worked fine. Then upgraded to 10.10. So far, so good.

I still wonder if others with Dell laptops/netbooks experienced similar problems after a regular update and what the cause/solution really are? Of all the things I've had to adjust/fix as a Dell ubuntu user, this one definitely makes it harder to recommend Ubuntu to an inexperienced user. I'm happy with Ubuntu and like 10.10, but I can't imagine someone new to Ubuntu being willing to deal with the complete crash of their machine and having to wipe/reinstall...

---

