---
title: "First Linux Dual boot (help a noob, win a cookie)"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by InsaneDane on 2007-12-13
So, after acquiring a particularly nasty virus in XP, I decided it was about time for a fresh format, and to dual boot with ubuntu (7.10).

After a bit of experimenting with everything from USB vs. PS2 keyboards to swapping around the order of the hard drives so GRUB would recognize the correct HDD, I've reached an impass.

the GRUB menu file is incorrect, (lists (hd0,0) instead of (hd0,2)), but I can correct that each time at the grub menu until I successfully boot linux as root and change it.

What has me hung up is that after grub seemingly works, and the Ubuntu splash screen displays, it dumps me into BusyBox.

Here is my grub entry for Linux after the (hd0,2) fix:

> root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=785C94795C94343A ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

I get the feeling that whatever I'm missing is incredibly simple. What is it?

---

### Post by src2206 on 2007-12-13
Did you try to reinstall GRUB? BTW, in which partition Ubuntu is installed actually? "cause if you still have XP, hd0,0 should have XP instead of Ubuntu unless you have formatted and decided to install Ubuntu at the very first partition of your HDD!

---

### Post by InsaneDane on 2007-12-13
XP is installed to 0,0. Ubuntu is installed to 0,2.

Oh. And I forgot to mention the strange part. Once GRUB loads busybox, if I "cd /root" then "ls", the files listed are from the XP partition.

---

### Post by src2206 on 2007-12-13
Can you boot in your XP as usual?

---

### Post by InsaneDane on 2007-12-13
Yup. XP works fine. I'm going to try reinstalling Grub, per:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by src2206 on 2007-12-13
Good idea :)
BTW, as I have done, you may also like to install the GRUB on a floppy drive so not to mess up your Windows MBR (though I think that you already have done that). ;)

---

### Post by Achetar on 2007-12-13
> **InsaneDane said:**
> So, after acquiring a particularly nasty virus in XP, I decided it was about time for a fresh format, and to dual boot with ubuntu (7.10).

After a bit of experimenting with everything from USB vs. PS2 keyboards to swapping around the order of the hard drives so GRUB would recognize the correct HDD, I've reached an impass.

the GRUB menu file is incorrect, (lists (hd0,0) instead of (hd0,2)), but I can correct that each time at the grub menu until I successfully boot linux as root and change it.

What has me hung up is that after grub seemingly works, and the Ubuntu splash screen displays, it dumps me into BusyBox.

Here is my grub entry for Linux after the (hd0,2) fix:



I get the feeling that whatever I'm missing is incredibly simple. What is it?

It is, boot into ubuntu, and run update-grub. Whoops, I misunderstood you.  Um, boot into another OS and manually edit your menu.lst (if it is Windows see [here ]("http://www.fs-driver.org/")to edit your Ubuntu files in windows) to reflect your setup.

---

### Post by InsaneDane on 2007-12-13
Okay, done. Same problem. Didn't even change the Grub menu file to (hd0,2).

---

### Post by InsaneDane on 2007-12-13
> **Achetar said:**
> Um, boot into another OS and manually edit your menu.lst (if it is Windows see [here ]("http://www.fs-driver.org/")to edit your Ubuntu files in windows) to reflect your setup.

Will do. But that will only solve the problem of having to tell it the hard drive every time if I'm not mistaken. I'll give it a shot though.

---

### Post by src2206 on 2007-12-13
I could never master the courage to use it though..Windows is so fragile you know :/, and I do not understand why this software emphasizes on Ext2 file system still, though its FAQ says that it can access Ext3 :o

---

### Post by InsaneDane on 2007-12-13
Yup. Fixed the (hd0,0)->(hd0,2) problem, but busybox still does the same thing.

---

### Post by InsaneDane on 2007-12-13
Thanks for your help everyone. Eventually found an answer here:
[http://ubuntuforums.org/showthread.php?t=234641](http://ubuntuforums.org/showthread.php?t=234641)
Changing my root= statement to "root=/dev/hda3"

I've got my dual boot up and running!

---

### Post by src2206 on 2007-12-13
Congratulations :)

---

### Post by Achetar on 2007-12-24
W00t 4 U!!

---

