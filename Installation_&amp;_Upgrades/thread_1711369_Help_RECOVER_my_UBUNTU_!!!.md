---
title: "Help RECOVER my UBUNTU !!!"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2011-03-21
I had **Ubuntu 10.04 64 bit** installed on my system with dual boot option (win vista).

Everything was working fine except printing to my HP printer. So I tried to** remove / uninstall everything related to HP**. 

Unfortunately, this had **too many dependencies** which I did not notice and went ahead with the uninstall. Looks like a lot of important files got removed. ](*,)

Now grub shows **only** Win Vista & MemTest86 - **No more Ubuntu** :sad:.

When I booted with an Ubuntu Installation CD and launched GParted, I saw that the Ubuntu partition showed 70% full which indicates that the data seems to be still there.

Could you please tell me how I could boot into my **beloved** Ubuntu - without losing my data?? :confused:


Thanks a lot for any information.

---

### Post by neakveaknoreak on 2011-03-21
[SIZE=3]ok mayb i could help but not sure... m just noob to linux. but ive just solved similiar problem but with Ubuntu 10.10 but it uses grub2 as 10.04. did u mean u install Ubuntu first and then Vista after? if yes mayb ur grub is overwritten.
follow this step:
-use ur Ubuntu live cd and boot to ubuntu live mode
- run in terminal ( system> administration>terminal) type:
  sudo fdisk -l
  u would see ur linux partition let's say /dev/sda1
- mount to ur Ubuntu partition(linux) type: 
  sudo mount /dev/sda1 /mnt
-install grub to mbr type
 sudo grub-install --root-directory=/mnt /dev/sda
-reboot to ur ubuntu  (but not with Ubuntu CD)
-refresh grub tyep: sudo update-grub
that's all hope it can help:P
[/SIZE]

---

### Post by cipherboy_loc on 2011-03-21
That works, or you could do:

```

sudo fdisk -l
sudo mount /dev/sda[ubuntu drive number] /mnt
sudo mount -t proc none /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt /bin/bash
sudo update-grub2
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
cd
sudo umount /mnt
sudo reboot

```

Then reboot into Ubuntu and run `sudo update-grub2` again.

Cipherboy

---

### Post by GeorgeOfTheBush on 2011-03-21
Thank you very much for your replies.

I get **an error** shown below. am i going wrong somewhere?

```

ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo update-grub2
[B]sudo: unable to resolve host ubuntu
sudo: update-grub2: command not found[/B]

```

---

### Post by Dutch70 on 2011-03-21
Try just using this one...
```
sudo update-grub
```

---

### Post by GeorgeOfTheBush on 2011-03-21
Thanks Dutch70.

I guess the problem is not with the** update-grub **command.

The problem is with **sudo chroot /mnt /bin/bash** which changes the user prompt to **root@ubuntu** as against **ubuntu@ubuntu**.

I am just stuck here. 

any other suggestions please ?

---

### Post by Hakunka-Matata on 2011-03-21
I'm guessing you do not need to use the **sudo **command any longer.  You are root, so you have root (superuser) privileges by default.

oops, just tried that, think I'm wrong - sorry

---

### Post by Hakunka-Matata on 2011-03-21
[http://ubuntuforums.org/showthread.php?p=10095234](http://ubuntuforums.org/showthread.php?p=10095234)

look at post #14 in particular

---

### Post by cipherboy_loc on 2011-03-21
Try:

```

echo "$PATH"

```

If it is in it, you will have to re-install grub2 and a bunch of other services. Look at your log (/var/log/apt/history.log, /var/log/apt/history.log.1.gz, etc) should tell you what you removed/installed.


Cipherboy

---

### Post by jonnyboysmithy on 2011-03-21
What you could also try is to reinstall ubuntu.

when you reinstall you'll have to manually specify partitions and mount points making sure it uses your home folder as home folder, that way you will still have all your documents program settings backgounds pictures email etc etc....
just be careful not to erase the homefolder, or else you may have a problem:-k

---

### Post by Hakunka-Matata on 2011-03-21
You can boot to the LiveCd evidently.  So..

[LIST]
[*]Boot to the Live CD
[*]Open a Terminal
[*]```
sudo fdisk -l
```  Post the output
[*]```
sudo blkid
```  Post the output
[*]Go to the 'bootinfoscript' URL in my signature, do as it says and post the output afterwords.
[/LIST]
That will help us understand your current configuration

---

