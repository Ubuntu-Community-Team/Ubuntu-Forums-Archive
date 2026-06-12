---
title: "[newbie] Need guidance for install replacing Mint"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by yawnG on 2011-02-15
Hello,

I have Win XP no sd1, Mint on sd5 and linux swap on sd6, and I want to install Ubuntu on sd5, where I have Mint. I'd like to know if the installer will create another swap partition or if it will use the existing one.
Also the installer asks me where to put the bootloader, but I don't even know what it is. Is it grub? What's the best place to put it? Can I choose a drive that I don't want erased?

Couldn't find any info about this on the web or here :(

Thanks in advance!

/y.

---

### Post by kn0w-b1nary on 2011-02-15
yes you can replace mint. i'm not sure about swap though. yes the bootloader is GRUB, but i'm not sure about how to setup to dual-boot as I've never done it.

Hope this helps!

---

### Post by yawnG on 2011-02-15
Thanks, but I know I can replace Mint. Grub sets up automatically. What I need to know is *where* to put it. It never asked me before with previous versions of Ubuntu...

---

### Post by kn0w-b1nary on 2011-02-15
this might help you:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Joe of loath on 2011-02-15
Put it on the MBR, or /dev/sda, depending on how it asks the question.

---

### Post by yawnG on 2011-02-15
> **Joe of loath said:**
> Put it on the MBR, or /dev/sda, depending on how it asks the question.
Ok, so that would be sda1 I guess? (I realize I forgot the "a" in the drives above).

Thanks!

---

### Post by kn0w-b1nary on 2011-02-15
/dev/sda is the drive, /dev/sda1 is the first partition on that drive. if you have windows on sda1 and load GRUB to it, you might lose windows. I don't know for sure, just a word of caution.

---

### Post by oldfred on 2011-02-15
You have to install to drive sda (or sdb if on a second drive).

If you have windows in partition sda1, installing grub to the partition will prevent windows from working. Windows has to have its boot code in the windows NTFS partition boot sector. Windows MBR and grub both jump to the windows partition boot sector to boot windows.

To understand how windows and all MBR(msdos) computers boot.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by yawnG on 2011-02-15
Thanks, wow didn't think it would be that complicated! If I got it right it's safer to install Grub on the linux part...

---

### Post by kn0w-b1nary on 2011-02-15
If you put GRUB at the beginning of the Linux partition you'll have to modify the windows boot loader accordingly.

---

### Post by yawnG on 2011-02-15
I guess the installer will take care of it, it always has in the past :)

---

### Post by Joe of loath on 2011-02-15
Stick it on /dev/sda, that's what I've always done and it's always worked fine.

---

### Post by yawnG on 2011-02-15
i already set it on sda5 which is my ext4 for currently installing ubuntu. since the installer didn't warn me i guess it won't be a problem, what do you think?

---

### Post by yawnG on 2011-02-15
ok, it didn't work :(

i got an "Error 15" message! :(

---

### Post by kn0w-b1nary on 2011-02-15
so windows sill works? you can always try putting GRUB on the MBR.

---

### Post by yawnG on 2011-02-15
i did a classic grub reinstall and it worked, thanks. now i messed with daniel richter's startup manager which has NO "exit without saving" button!!!

---

### Post by kn0w-b1nary on 2011-02-15
glad it's working!

---

