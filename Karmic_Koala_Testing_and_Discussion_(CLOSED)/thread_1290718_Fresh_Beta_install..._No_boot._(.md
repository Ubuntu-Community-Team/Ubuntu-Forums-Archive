---
title: "Fresh Beta install... No boot. :("
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Arabica Bean on 2009-10-13
Okay, I originally upgraded my laptop from 9.04 to 9.10 but suprise suprise, without success, so I downloaded the beta iso, and freshly installed Karmic instead. When GRUB2 selects the default kernel, (2.6.31-11), all I get is a blinking cursor.... nothing else. When I boot into the recovery mode, I get the usual flying text for two seconds, and then it hangs with a blinking cursor. 
The last line is something like "scsi 3:0:0:0: CD-ROM - Optiarc"......

I have reinstalled twice and to the same effect. Any ideas people? Thanking you in advance for any help recieved.

:)

---

### Post by kansasnoob on 2009-10-13
Well, we're on kernel 2.6.31-13 now so maybe an update would help .......... but no guarantee! (It won't break anything.) We can do that by mounting and using chroot but first of all I need some info.

If you can get on the Internet with the Live CD I need to see the output from Terminal of:

```
sudo fdisk-l
```


BTW that's a lower case L. And I'd appreciate any info you can provide regarding your setup if you're multi-booting or such.

---

### Post by Arabica Bean on 2009-10-13
I'll try to update via chroot, and report back with any info I have. Expect a reply soon!

---

### Post by kansasnoob on 2009-10-13
> **Arabica Bean said:**
> I'll try to update via chroot, and report back with any info I have. Expect a reply soon!

Ah, so you know how. That's a good thing!

---

### Post by VMC on 2009-10-13
> **Arabica Bean said:**
> I'll try to update via chroot, and report back with any info I have. Expect a reply soon!

Also, if it fails again, give us some of your specs.

---

### Post by Arabica Bean on 2009-10-14
Okay I chrooted, and updated, without any major hickups, although dpkg did have a few problems installing pulseaudio....

I booted back but with the new 2.6.31-14 kernel, and in hangs in the same place. Shame really because the netbook i'm typing on is running Karmic without problems.

I have no other OS installed. MY partitions are...

/dev/sda1 - Root ext4
/dev/sda5 - home ext4
/dev/sda6 - swap


I am installing on an advent 7201, which has an Intel Celeron, 1GB of Ram, and an ATI Radeon graphics card.

Thanks in advance.

---

### Post by VMC on 2009-10-14
> **Arabica Bean said:**
> ... and in hangs in the same place. ...
What place would that be. What's outputted just before at hangs.

Use recovery mode and look in home directory at both ".xsession-errors" and ".xsession-errors.old" for any clues.

---

### Post by Arabica Bean on 2009-10-14
> **VMC said:**
> What place would that be. What's outputted just before at hangs.

Use recovery mode and look in home directory at both ".xsession-errors" and ".xsession-errors.old" for any clues.

Sorry.  On normal boot, nothing happens, it just shows the blinking cursor. In recovery mode, there does not seem to be any error messages on it. About two seconds into boot, it says "ata2: SATA link down (SStatus 0 SControl 300) and there are a few more lines. The last line to show is the "scsi 3:0:0:0" line that's in my previous post.

As regards .xsession-errors and the old one. They don't exist, as I haven't been able to log into the account yet.  

Still lost.

---

### Post by Arabica Bean on 2009-10-14
Just a quick note, I have managed to access the /var/log directory. This is where I lack knowledge in Ubuntu. Can someone point me in the right direction to what logs I should look in?? Basically, it hangs in the boot process two seconds in, so it hasn't gotten as far as running gnome or anywhere near that. When I say hang, I don't mean that it freezes, it just has the blinking cursor.

---

### Post by ranch hand on 2009-10-14
Try the /var/log/gdm directory.

I would just start at the beginning and rummage through them all.  I am fairly new at this too and find that I actually learn a few things doing that.

You will find the one with the failure in it, I believe fairly early in the files.

---

### Post by Arabica Bean on 2009-10-14
I've looked through all the log files, and to no avail. I've decided to return to Jaunty for the time being.  Thank you all for your help.

---

