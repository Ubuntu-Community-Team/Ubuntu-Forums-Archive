---
title: "Installing Ubuntu 12.04 64-bit"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by pieter512 on 2014-03-19
Hi

I have an external sata hard disk with a 70GB Ext-4 partition, a 164GB ntfs partition, and a 16GB Linux swap partition. I had Ubuntu 12.04 32 bit installed on the 70GB partition, and everything worked fine. Then I tried to install the 64-bit version, since my laptop is 64bit (Dell inspiron 17R SE 7720). I formatted the 70GB and installed it with a pendrive, just like I did with the 32bit version, but now, every time I boot from the disk, I get this error:

[ 1.000438] Kernel panic – not syncing: No init found. Try passing init= option to kernel. See Linux Documentation/init.txt for guidance.

I tried installing it again, this time on my desktop, with the hard disk internally connected via sata, and the same error appeared. On the ntfs partition, I installed the Windows 8.1 32bit preview, and that works without any troubles.

How can I fix this?

Thanks in advance
Pieter

---

### Post by sudodus on 2014-03-19
Welcome to the Ubuntu Forums :-)

So you had a 32-bit system working on the same partition. Then the problem should be specific for the 64-bit system, or maybe, there is something wrong with the pendrive.

- Did you check the md5sum of the downloaded iso file? See this link.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- How did you flash the pendrive? Which tool?

- Did you try the same version (12.04 LTS) or did you try 13.10?

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
Pieter,

I've seen a couple of scenarios where I had similar issues.  In the first one, there was no symbolic link from /lib to /usr/lib in initramfs.  It was a simple re-install of the file system that fixed that.  The second was that the GRUB boot loader replaced the Windows boot loader.  It also wrote it to /dev/sda1 instead of /dev/sda.  I'm looking for the "fix it" link....  Ah, here is the one I used:  [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

-DM

---

### Post by pieter512 on 2014-03-19
Sudodus, thank you for your reply.

I didn't check the md5sum, so now I'm downloading a new iso. I used Universal USB Installer for this pendrive. For the new one, I will try using the "Startup disk creator" on my working Ubuntu machine. The iso was ubuntu-12.04.4-desktop-amd64. iso, and not 13.10.
I'll let you know if it works with the new iso!

---

### Post by sudodus on 2014-03-19
I think Startup Disk Creator or Unetbootin might work better than the Universal USB Installer.

See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

---

### Post by pieter512 on 2014-03-19
It works! It seems to be just a bad iso...

Thank you very much!

---

### Post by sudodus on 2014-03-19
Congratulations :KS

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

