---
title: "Freeze at boot"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by Romanouche on 2012-01-06
Hi,
I installed Ubuntu 11.10 64 on a HP Z210 workstation (i7 2600 CPU, NVidia Quadro 2000).
I had trouble starting the installation process or any item from grub menu as whatever I selected, I got a frozen black screen. I managed to install by adding the nomodeset parameter to the grub item command line using the manual mode (pressing 'e' on grub screen, modifying the command line by adding 'nomodeset', and pressing F10).
The installation was fine but now the computer won't boot.
It freezes on a black screen with a blinking cursor.
I guess there is still a problem with the graphic card.

I tried advice from post [http://ubuntuforums.org/showthread.php?t=1743535:](http://ubuntuforums.org/showthread.php?t=1743535:)
As grub menu did not appear at startup I pressed Shift key multiple times but nothing happenned.
I booted the Live CD using the nomodeset option.
When I did the ubuntu installation, I installed on different partitions :
/boot (sda1)
/ (sda2)
swap (sda3)
/usr (sda4)
/var (sda5)
/tmp (sda6)
/home (sda7)

I commented out /etc/default/grub/ GRUB_HIDDEN_TIMEOUT=00 and added nomodeset option to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".
I saved the file.
I created dirs in /mnt in order to mount the different partition from the installed ubuntu:
mkdir /mnt/boot
mkdir /mnt/usr
mkdir /mnt/var
mkdir /mnt/tmp
mkdir /mnt/home

Then I mounted the partitions to corresponding directory:
mount /dev/sda1 /mnt/boot
mount /dev/sda2 /mnt/
mount /dev/sda4 /mnt/usr
mount /dev/sda5 /mnt/var
mount /dev/sda6 /mnt/tmp
mount /dev/sda7 /mnt/home

Then did some binding:
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

Then chroot to /mnt:
sudo chroot /mnt
I updated grub:
update-grub
Everything seems fine:
Generating grub.cfg...
done

I reboot but still block on the blinking cursor.

I reinstalled grub using the same kind of process. But got still the same thing.

Then I modified /etc/default/grub with what's advised in [http://ubuntuforums.org/showpost.php?p=11547960&postcount=845](http://ubuntuforums.org/showpost.php?p=11547960&postcount=845).
I changed GRUB_CMDLINE_LINUX_DEFAULT to GRUB_CMDLINE_LINUX_DEFAULT="vga-791"
and added GRUB_GFXPAYLOAD_LINUX=text at the end of the file and saved it.
Updated grub.
Rebooted.
Still the same black screen with blinking cursor. I tried again multiple press on Shift key. Nothing moved.

What should I do to try fix this?

Regards
Rom

---

### Post by Michl on 2012-02-18
Well,let me stab into the dark a little, since noone
else is helping.  How did you do the install?  Did
you try running the live CD and then installing from
the running live CD?  I think that usually works best.

By the way, maybe some of this is helpful:

[http://h71028.www7.hp.com/enterprise/us/en/os/linux-Z210-workstation.html](http://h71028.www7.hp.com/enterprise/us/en/os/linux-Z210-workstation.html)

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=at&taskId=130&prodSeriesId=5053190&prodTypeId=12454&objectID=c02786400](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=at&taskId=130&prodSeriesId=5053190&prodTypeId=12454&objectID=c02786400)

For what it is worth, the z210 is available with Suse 11 preloaded.

---

### Post by YannBuntu on 2012-02-21
Hello
i would try this: run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), click "Advanced options", go to "GRUB location" tab, select "Purge and reinstall GRUB", then go to "GRUB options" tab, and select "Add kernel option: nomodeset", then apply.

---

### Post by ZDemon on 2012-06-19
Hi,

I have a z210 too. I solved the problem by editing /etc/default/grub and adding "nomodeset" to the default options.

Then i run this command using a LIVE CD.
```

sudo install-grub [YOUR_HD] --boot-directory=/media/[YOUR_MOUNTED_LINUX_PARTITION]/boot
sudo grub-setup [YOUR_HD]

```

Typically, [YOUR_HD] should be /dev/sda, which is the HD you installed Ubuntu on.
and [YOUR_MOUNTED_LINUX_PARTITION] should be its label or UUID. Just "ls /media" to find out.

Then after reboot, GRUB works. Hopes this helps others.

---

