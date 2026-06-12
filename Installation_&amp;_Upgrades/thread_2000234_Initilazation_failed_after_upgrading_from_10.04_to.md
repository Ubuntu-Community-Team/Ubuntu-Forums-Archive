---
title: "Initilazation failed after upgrading from 10.04 to 12.04"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by miniplazma on 2012-06-09
After upgrading and restarting system I get following message when Ubuntu is booting:
Command line 'dbus-launch-autolaunch=a0fd8441ac91a7ec2ff97e394f185fab -- binary-syntax --close -stderr' exited with non-zero status 1: Autolaunch error: X11 initialization  failed.
udevd[401]:specified group 'colord' unknown

After that message asks me would I like to skip mounting or manual mount for every partition.

---

### Post by miniplazma on 2012-06-10
Does anyone know what is the problem?
I tried changing /boot/grub/grub.cfg and /etc/default/grub
(changed every "quiet splash" into "quiet text") but still get the same error massage.
Is it problem with Plymouth or something else?

---

### Post by miniplazma on 2012-06-14
Any solutions?  :confused:

---

### Post by say42 on 2012-06-16
I had the same problem. In my case Precise actually didn't install completely before asking to reboot after setup. After rebooting I saw old grub menu and no new kernel in it.
May be you have another problem but anyway try to fix installation:
1) Boot from Live CD
2) Mount linux system partition (where your system installed) to /mnt: 
```
sudo mount /dev/sdaX /mnt
```3) mount virtual filesystems:
```
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
```4) chroot into the system device
```
sudo chroot /mnt
```5) 
```
apt-get install -f
```Steps 1-4 I got from [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by sfeu on 2012-07-18
Hey there,

I can confirm that this bug , which happend to me as well after i upgraded from 10.04 to 12.04. 

In my case i was not required to start a live CD. It was enough to choose M for manual recovery, remount the root filesystem, start the network interface and continue the installation using the follwing commands:

mount -o remount,rw /

ifconfig up eth0

dhclient eth0

apt-get install -f

If more people run into this problem, we should submit a bug report - i think its a serious one - especially as it seams to happen for people that do LTS upgrades only...


cheers,
Sebastian

---

### Post by MdMax on 2012-08-10
Thank you Sebastian, your commands helped a lot. I had the same problem.

Cheers.

---

### Post by JGMS on 2012-09-06
Hi all,

I experienced the same problem during upgrading from 10.04 to 12.04.
A long list of error messages occured during the upgrading process, which continued despite of this until a certain point when it stopped, messaging "Processing was halted because there were too many errors." Restarting the system was no longer possible, and the same error message about "...X11 initialisation failed.\n" as mentioned in the previous posts appeared. Thereafter the option "S" or "M" to deal with the unmounted disk appeared. However, the system was dead after this, so did not react on keyboard entries.

Does anyone know how to solve this.

---

### Post by PLaci1982 on 2012-10-10
Just one comment:

Not ```
ifconfig up eth0
``` but ```
ifconfig eth0 up
```

---

### Post by Koraq on 2012-12-07
Kudos and thanks to sfeu & say42 for the helpful suggestions! 

This is a major bug! I frankly considered just wiping my whole HD after the event and installing Fedora. How come it's happening on a LTS? 

Anyway.

I had some problems with the 'apt-get install -f', with libphonon1-dev not installing. I solved it by use of 'apt-get download <package>' and 'dpkg -i <package>' and when needed adding in '--force-all'. That way I got a machine that can boot again! Now I have a broken kde, but at least I can do a full backup before I re-install everything. 

I was at my wits end. *Many thanks* again to the participants of this thread.

---

### Post by sureshvv on 2013-03-30
Thanks. Helped me.

---

### Post by karlwilbur on 2013-04-17
Thanks, say42! This was able to get me rolling again. I have more issue to resolve but at least I have a "working" environment.

FWIW, here is the next thing I ran into:
[http://askubuntu.com/questions/231525/12-04-lts-upgrade-error-on-libuuid1](http://askubuntu.com/questions/231525/12-04-lts-upgrade-error-on-libuuid1)

---

### Post by julotte on 2013-08-19
Thank you so much guys, it worked for me. 

I didn't need a live CD either. I just did the following:

mount -o remount,rw /
apt-get install -f

Thanks again!

---

