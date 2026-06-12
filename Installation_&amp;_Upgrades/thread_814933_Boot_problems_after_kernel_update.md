---
title: "Boot problems after kernel update"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by misja on 2008-06-01
Hi,

I have had ubuntu installed on my machine for one year now, and upgraded to Hardy last month without problems.
A couple of days ago the update manager informed me that there were new updates. I installed them; on of them was a kernel update to 2.24.17.
I got no error messages; at the end I was given a list of options about what to do with grub's menu.lst file; I chose to keep my old one and add the changes by myself. The reason for that is that grub switches my 2 harddisk around so that I can't boot.
After I added a line for the new kernel to my menu.lst I restarted.
Then, after restarting, I ended with a command prompt. Above it said something like 'kinit: trying to resume from image ...' and some other stuff from kinit. I don't know the entire text, because after a few seconds X was started anyway, but then I got the message that my nvidia driver was not found.
So from then on I have been working in low resolution mode.

For the past 2 days I have been trying to fix this; first I thought that the (proprietary) nvidia-driver was the problem, so I uninstalled all nvidia drivers, re-installed them, also tried envy, finally even installed the nvidia driver from the website, but nothing helped.
When I checked the xorg.0.log file there are no errors there though. 
So that led me to believe that perhaps something else in the boot process had gone wrong, because of which the nvidia drivers were not loaded properly.
I really wouldn't know what to look for though. I checked the /var/log/dmesg file but it contains no errors.

The only 'solution' I could still think of is re-installing ubuntu but I really don't feel like because setting up my complete system will take days..
Can anybody give advice on what to do?

Thanks,
Misja

---

### Post by Pumalite on 2008-06-01
You could check your UUID's:
blkid
(against)
cat /etc/fstab
(sgaints)
cat /boot/grub/menu.lst

---

### Post by misja on 2008-06-03
Thanks for the tips.
There were no differences between grub's menu.lst and the other files.
blkid and fstab had a difference: The UID of my swap partition was different. So I changed fstab's uid so that it matched blkid's. Restarted, but this didn't make any difference.

So finally I decided to reinstall Hardy :( . So far this went without any problems.

---

### Post by misja on 2008-06-03
Well.. 
So I installed Hardy, installed all updates, then enabled restricted drivers so that the Nvidia video driver could be used, and everything worked fine, also after a restart.
Then today I started my pc to continue the installation, but never got to that point :( 
The Ubuntu startup progress bar was showing, but it stayed there a very long time. Finally I ended up in a shell that I've never seen before: Some 'initramfs' shell. It said I could type 'help' to get a list of options.

I have a second disk in my pc with Windows 2000 on it, I tried to boot from that and that went fine.
Then today, when I was writing this mail, I tried to start Ubuntu again to see exactly what shell I would get into, and then Ubuntu started normally again!

So my guess is now that something is wrong with the disk where Ubuntu is on. I would like to do some check but can't find any program that would check my disk on Ubuntu.
Does anybody have any tips?

Thanks again,
Misja

---

### Post by Pumalite on 2008-06-03
systemrescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by misja on 2008-06-03
Thanks for the link. I have tried the smartmonitor harddisk utility already and tried it. All tests have run without any error ...
Also I checked the dmesg file from yesterday when my computer did not boot succesfully: No real errors, except for the following lines:
               sd 3:0:0:0: [sdb] Attached SCSI disk
[   32.462582] Attempting manual resume
[   32.462585] swsusp: Resume From Partition 8:5
[   32.462586] PM: Checking swsusp image.
[   32.462746] PM: Resume from disk failed.

I did some googling and found quite a few posters having the same message and similar problems as I have. What's more, most of them started to have their problems in Ubuntu 8.04... It seems to be related to the following bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414)

Really annoying, especially since this bug was reported in February already and the recent kernel update to 2.6.24-17 only seems to have made it worse ! As was the case on my pc .. :mad::mad:

So I guess there is not much I can do about it right now, or perhaps choose another OS ..

---

### Post by Pumalite on 2008-06-03
Sorry you have problems. My 4 Hardies are running fine. I guess is a matter of hardware.

---

### Post by Pablo Pablovski on 2008-06-03
I had the same problem when I first upgraded to Gutsy. It turned out to be some issue with the kernel version. In the Grub menu, try booting using the 2.6.24.17-_generic_ kernel.

---

### Post by ubiqus on 2008-06-13
booting the 2.6.24.17-generic kernel made this issue go away. Is there a bug posted for this. The buf Misja reports above doesn't seem to match.

---

### Post by Charlypv on 2008-06-16
> **misja said:**
> Hi,

I have had ubuntu installed on my machine for one year now, and upgraded to Hardy last month without problems.
A couple of days ago the update manager informed me that there were new updates. I installed them; on of them was a kernel update to 2.24.17.
I got no error messages; at the end I was given a list of options about what to do with grub's menu.lst file; I chose to keep my old one and add the changes by myself. The reason for that is that grub switches my 2 harddisk around so that I can't boot.
After I added a line for the new kernel to my menu.lst I restarted.
Then, after restarting, I ended with a command prompt. Above it said something like 'kinit: trying to resume from image ...' and some other stuff from kinit. I don't know the entire text, because after a few seconds X was started anyway, but then I got the message that my nvidia driver was not found.
So from then on I have been working in low resolution mode.

For the past 2 days I have been trying to fix this; first I thought that the (proprietary) nvidia-driver was the problem, so I uninstalled all nvidia drivers, re-installed them, also tried envy, finally even installed the nvidia driver from the website, but nothing helped.
When I checked the xorg.0.log file there are no errors there though. 
So that led me to believe that perhaps something else in the boot process had gone wrong, because of which the nvidia drivers were not loaded properly.
I really wouldn't know what to look for though. I checked the /var/log/dmesg file but it contains no errors.

The only 'solution' I could still think of is re-installing ubuntu but I really don't feel like because setting up my complete system will take days..
Can anybody give advice on what to do?

Thanks,
Misja


I have the same problem running ubuntu 8.04 
Have you have any suggestion?

---

### Post by ric.guerreiro on 2008-09-05
Hi,
I have installed ubuntu Hardy Heron a few months ago. I have installed all the updates till i got to the kernel 2.6.24.19 version. So far so good.
Then, after another update, i was asked to restart the computer so that updates could take effect. I chose the latest kernel version and, after loggin in the screen went white and no signs of ubuntu. I restarted the computer and managed to log in with the previous kernel version 2.6.24.18.
A few day later, and after some other updates, i had the same problem i have had before with the 2.6.24.18. So now i am back with the 2.6.24.17.
Any suggestion on how to unistall ana re-install again the latest kernel version?

Cheers

---

