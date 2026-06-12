---
title: "Waiting for root file system..."
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by sedition on 2007-05-23
Hi all,

I have a Toshiba Libretto 110CT that I pulled the hard drive out of and put into my Toshiba S801 (did the following previously with Edgy and received no problem). I did a text only install from the alternate Feisty CD, reboot, logged in and everything was kosher. Then, I pulled the drive out and popped it back into my Libretto and booted. The trouble began with the cookie-cutter response, "/bin/sh: can t access tty job control turned off". The system would then drop to (initramfs), so I added ramdisk=8192 to grub, as some sites mentioned, but still no boot. I disabled "quiet splash" so I could see WTF is going on. After a long wait at the "Begin: waiting for root file system..." prompt I received the same /bin/sh message followed by (initramfs), preceded by a message stating that it couldn't find my root drive. Here's the clincher: I pop the drive back into the S801, and everything loads. Anyone have any ideas what else I could try? Here's the particular section of grub (unmodified) that I'm trying to load:

```

root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=6aa2338b9-4438-440b-b815-a95c7b1b4f1d ro quiet splash
kernel /boot/initrd.ing-2.6.20-15-generic 
quiet
savedefault

```

Thanks in advance,
-sed


So, I put 6.10 back on and everything went fine. After checking /boot/grub/menu.lst, I noticed that the first kernel line contained root=/dev/hda1 rather than the root=UUID=hex (?) stuff. I'll reinstall and let you know the deal in case it can help anyone else out.

---

### Post by ndefontenay on 2007-05-23
If you replace those lines you mention at the end of your message, is it loading properly?

---

### Post by sedition on 2007-05-23
No dice. After reinstalling 7.04, I tried changing the line in grub to utilize /dev/hda1 (as specified in 6.10) instead, but no load. I could easily reinstall 6.10 and just dist-upgrade, but any have any suggestions on my current install?

Thanks again,
-sed

---

### Post by irieken on 2007-05-24
Is the drive larger than 8GB? 

This is a shot in the dark; is it possible that you installed 6.10 on a partition smaller than 8GB, and now used the entire disk this time around?

The Libretto hardware itself won't support a partition larger than 8GB.

This is just a guess, but the MBR may read (grub comes up),then not have any support after.

Linux will be able to read partition larger than 8GB once kernel loads.

---

### Post by sedition on 2007-05-24
> Is the drive larger than 8GB? 
No, it's the standard 4.3GB drive that it was shipped with, but good thought.

> This is just a guess, but the MBR may read (grub comes up),then not have any support after.
An interesting thing to note is, though the MBR is read, it fails when (I believe) busybox/initramfs goes to mount the partition. What I don't understand is how it could work in one box, and then not the other, with no changes to grub. This would lead me to believe that either, A. some piece of hardware in the Libretto is no longer supported in 7.04, or B. there needs to be a change in grub's config to compensate for some difference in hardware. During 7.04 installation, I noticed that /dev/sda is utilized rather than /dev/hda as in 6.10. I'm curious as to what might happen if I were to install 6.10 and upgrade to 7.04. I imagine that it would definitively answer the question of unsupported hardware in the revision of these programs, or simply a change in grub config. I think I'll go this route tonight and post the results. ;)

This could get interesting...

---

### Post by irieken on 2007-05-24
I also have an Libretto 110CT, so I hope that you clear up your issues; I want to run Feisty on mine;)

Make sure to set the default X color depth to 16 bit, or redrawing the screen will tear your performance to shreds.

---

### Post by irieken on 2007-05-24
Try changing "root=UUID=6aa2338b9-4438-440b-b815-a95c7b1b4f1d" to your root partition. IE "root=/dev/hda1".

Good luck.

---

### Post by irieken on 2007-05-25
I tried installing Feisty on my libretto last night and had the same problem that you are having.

I tried changing the "root=" bootarg, but it didn't help. I even tried installing the i386 kernel, which didn't help either.

---

### Post by sedition on 2007-05-25
Yep. Tried that and even the missing "boot" line in grub, but to no avail. I even re-installed 6.10, apt-get dist-upgraded to 7.04, but after reboot, no love. Seems that whatever loads after the kernel and tells the root partition to mount can't detect something in the Libretto's  hardware, as my grub config did not noticably change from the original 6.10 install. I seem to recall hearing something about Feisty using a replacement for init for faster boot times, so maybe that's it?

---

### Post by irieken on 2007-05-26
I've made some progress!

In this post: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123)
I found a message by Alf Lervåg  that was very helpful.

The gist was this: When you get dropped to Busy Box prompt, type in:
modprobe ide-disk; modprobe ide-generic; cat /sys/block/hda/dev; mknod /dev/hda1 b 3 0

Then press ctrl+D, and your machine will boot!:D

---

### Post by roggerdavid on 2007-06-01
GREAT NEWS! So how is 7.04 looking on the 110ct? Is it better that 6.10?

---

### Post by irieken on 2007-06-05
It was too slow to be usable, and I lost patience trying to do anything with it; hoping that someone else will give it a shot... Or I will just wait for Fluxbuntu:)

---

### Post by sedition on 2007-06-05
irieken,

Did you ever get it to boot without the commands? I'm going for a custom install from the server installation and adding the blackbox wm, myself. ;)

---

### Post by roggerdavid on 2007-06-08
Well ... I been trying to install elive, puppy, and slackware, but I've not been able to get any of them to load completely. The only one that loaded well but i had problem installing the wireless cards was DSL. I might try ubuntu 6.10 to see if i can get the wireless card working. Tonight will be my last attempted with slackware. I love this 110ct laptop. Godspeed to all.  :D

---

