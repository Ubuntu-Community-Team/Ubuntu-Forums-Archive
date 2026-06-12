---
title: "A Tale of Two OSes"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by SydneyMyers on 2009-12-04
Hello to all Ubuntu-ers! :)

Now here is my current predicament.

I decided to try the new Ubuntu 9.10. My volumes were as follows:
C: 50GB - Windows 7
D: 100GB - Stuff
E: 100GB - Stuff

I shrunk D: by 15GB and installed Ubuntu 9.10 in that free space. I should note that I chose to install Grub in the MBR.

I played around with Ubuntu a little bit and also created my own OpenPGP key.

Then I decided to get rid of Ubuntu and continue my life as a windower (for the time being, at least). So I used the "Reinstall Vista Bootloader" option in EasyBCD. However, I remembered that I'd forgotten to export my OpenPGP key and now I'm looking for a way to boot into Ubuntu for one last time to export it.

Can any of you help me? Over the last few days I've been trying everything I could Google up, but to no avail...

---

### Post by dstew on 2009-12-04
If the Ubuntu system is still on your partition, you can use grub to boot it. If you used grub 1.97 (also known as grub 2) use the mkrescue command, as shown in the post by linus72 in [this thread]("http://www.linuxquestions.org/questions/linux-general-1/how-to-i-make-a-bootable-cd-that-contains-grub2-766336/"). Boot the grub floppy, and you get a command line. You can boot your Ubuntu system from the grub command line using the **linux**, **initrd** and **boot** commands. You will need to search around for the correct linux kernel and initrd arguments using the **ls** command. Use the tab-complete feature also to list possible arguments for the commands. I have to go, can't be more complete, see you later.

---

### Post by namok on 2009-12-05
Try it [Super Grub Disk]("http://www.supergrubdisk.org/index.php")

---

### Post by SydneyMyers on 2009-12-05
Hi, dstew. I tried your suggestion and everything works fine and after the 'boot' command, linux starts booting (I think) until it stops at 'Waiting for root file system' and after a while it says 'Gave up waiting for root filesystem' etc and drops me to a shell.

namok, tried your SGD. I go to Advanced -> GNU/Linux -> Boot Gnu/Linux and after I specify the kernel and initrd, somehing happens for half a second and my PC reboots and nothing has changed.

---

### Post by darkod on 2009-12-05
I think it's even better idea to simply start with the ubuntu cd, select Try Ubuntu option and that will run it from the cd. It can see your hdd, most probably you will have it in Places, but you just need to mount the partition you want to "see". Then just copy what you want to usb stick or usb hdd, and that's it. In theory... :) Don't forget, the LiveCD is giving you fully running ubuntu from the cd.

---

### Post by SydneyMyers on 2009-12-05
> **darkod said:**
> I think it's even better idea to simply start with the ubuntu cd, select Try Ubuntu option and that will run it from the cd. It can see your hdd, most probably you will have it in Places, but you just need to mount the partition you want to "see". Then just copy what you want to usb stick or usb hdd, and that's it. In theory... :) Don't forget, the LiveCD is giving you fully running ubuntu from the cd.

I thought of that from the beginning. But, as I need my OpenPGP key, I do not know how or where to find it. I suppose it's in some secret database somewhere in Ubuntu. This is another line of thought and I would be grateful if anyone could assist.

---

### Post by darkod on 2009-12-05
If you create a thread with title like that question, and possible in another section of the forum, people who know more about it are more likely to open to read it. Tell them what you need with the thread title.

PS. Can this help you:
[http://www.24hourapps.com/2009/02/backing-up-and-restoring-openpgp-keys.html](http://www.24hourapps.com/2009/02/backing-up-and-restoring-openpgp-keys.html)

---

