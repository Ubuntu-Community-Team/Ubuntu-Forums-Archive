---
title: "Ubuntu 12.10 Grub problem"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Topnol on 2012-10-19
I have attempted an upgrade to Ubuntu 12.10 on a PC with dual boot Ubuntu/ Windows 7. The PC has a SSD Drive and a normal hard drive installed.
On reboot after installation I get a black screen with the follow message:

error:file not found
grub rescue >

Can anybody advise a solution :confused:

---

### Post by darkod on 2012-10-19
At the rescue prompt, what is the output of:
ls (small LS)

---

### Post by Topnol on 2012-10-20
> **darkod said:**
> At the rescue prompt, what is the output of:
ls (small LS)
   Thanks for your response
The output is as follows:

(hd0) (hd0,msdos2)(hd0,msdos1)(hd1)(hd1,msdos7)(hd1,msdos6)(hd1,msdos5)(hd1,msdos1)(hd2)(hd2,msdos1)(fd0)(fd1)

---

### Post by darkod on 2012-10-20
That shows three disks, hd0, hd1 and hd2, not only two.

Basically, you need to check which one is your ubuntu root partition, if you don't know. Do you know where is ubuntu installed?

If you don't, my first guess would be (hd1,msdos5). Try to list the files on it with:
ls (hd1,msdos5)

In the list of files (it should be short) do you see vmlinuz and initrd.img?

If that is not the partition, try looking in the others one by one changing the hdX and msdosY in the command. Check only the existing partition reported by the original ls command.

---

### Post by Topnol on 2012-10-20
I am getting an 'unknown command' when I try these !

---

### Post by Topnol on 2012-10-20
I have an external hard drive connected which I use for back up and the storage of photos.  I have disconnected this and ls now reports only hd0, hd1 and fd0,fd1
regards

---

### Post by darkod on 2012-10-20
Hmm, are you trying the ls as before (small LS)?

It shouldn't say unknown command. Alternatively, if that still doesn't work, can you burn a 12.10 cd and boot into live mode with it?

---

### Post by Topnol on 2012-10-20
I will try and burn a 12.10 disk from my laptop.  I have a live 12.4 disk is that any good ?
What actions should I carry out when I have boot my PC with the disk.
Many thanks

---

### Post by darkod on 2012-10-20
You can use the 12.04 to take a peek at the files, but for grub2 repair you will need to use a 12.10 cd.

When you load live mode to take a look, open the root partition and look for /boot/grub/grub.cfg and /boot/grub.core.img. If they are there, good.
Then look in /boot and check if the kernels are there.

If all that goes good, you will need the 12.10 cd to try grub2 repair. When you boot it into live mode, mount the root partition and reinstall grub2 to the MBR of the disk:
```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```

Then reboot without the cd and see how it goes.

---

### Post by Topnol on 2012-10-21
Followed your advice and burnt a 10.12 disk and used it to enter the code you passed and 'grub' was installed and every thing works fine.
Thank you very much for you help and advice. :)

---

