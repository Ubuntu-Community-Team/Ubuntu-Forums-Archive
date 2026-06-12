---
title: "Installed Lucid Lynx but it won't boot up. Getting error 2 message?"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by Macfunky on 2010-05-21
I have just installed Lucid Lynx as after a live run of it i thought it was about time to upgrade. Everything ran smoothly in the live version so i backed up my files and installed it. When i went to boot i get this -

Grub loading, please wait ...
Error 2

The strange thing is it seems to be specific to the computer. I have an older, lower speced desktop, computer that i tried the hard drive in and it worked fine. Problem is its too low speced for what i want so it seems the install went ok but its something with the computer? Anyone know what could be happening and be able to help me to be able to boot into the install?

---

### Post by byStanderone on 2010-05-21
...seems like you have to reinstall grub:
-boot from your live cd

-determine where your system is installed, either by using fdisk -l
  or blkid on a terminal, or gparted if you want (might be sda1,or   sda5,..defends where you've installed it)

-mount that partition: sudo mount /dev/sda5 /mnt (use yours instead of sda5)

reinstall grub: sudo grub-install --root-directory=/mnt /dev/sda
                                      (again use yours,w/o the number)

-unmount the partition: sudo umount /mnt

-reboot

---

### Post by Macfunky on 2010-05-21
Thanks for the help but i am a newbie. Could you break it down into easier to understand steps and i will give it a go. Also why would i lose grub? Is grub not installed with the operating system as well?

---

### Post by Macfunky on 2010-05-21
Ok Gparted told me that it is installed on sda1. I tried to mount that partition but it won't mount. Output -

ubuntu@ubuntu:~$ sudo mount/dev/sda1/mnt
sudo: mount/dev/sda1/mnt: command not found

Just noticed that my drive isn't even showing up in Places. Whats going on?

---

### Post by byStanderone on 2010-05-21
...u got to have spaces on the syntax:  sudo mount /dev/sda1 /mnt

copy the command line and paste it on the terminal....

---

### Post by paulb42 on 2010-05-21
I think you left out some spaces

sudo mount /dev/sda1 /mnt

---

### Post by byStanderone on 2010-05-21
...grub is there actually but it is being pointed to a different direction, the reason why you are not able to boot...there are other ways in solvingthe problem...but i guess that would be complicated for you at the moment, but later as you go along you'd be doing fine.

---

### Post by Macfunky on 2010-05-21
If there is something wrong with grub then why is the hard drive loading up into ubuntu fine on my other computer? Also why isn't it mounting the partition when the terminal and gparted picked up on it fine? Also seeing as the other computer is working with the hard drive would it work if i re-installed grub on that computer?

---

### Post by Macfunky on 2010-05-21
Ok i got this message and i'm not sure what to do -

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

---

### Post by byStanderone on 2010-05-21
...ok, disregard the infos i posted...will review your post, seems your setup is different than what i thought. hold on.

---

### Post by byStanderone on 2010-05-21
...for the meantime, would you post some more infos about your desktop, like if you are dual booting with what 'os' and other specs bout your box if possible....

---

### Post by Macfunky on 2010-05-27
Bump. . .

Anyone able to help me out with this? Still haven't figured out what is up

---

