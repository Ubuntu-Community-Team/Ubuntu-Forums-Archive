---
title: "Tried updating to 12.04, it crashed and now I can't access Linux at all."
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by insanity99 on 2012-05-16
I was on the 11.10, I clicked the upgrade button and it did all the steps, up to the actual installation, before clean up and restart. It crashed during install, my mouse stopped moving and the progress bar had not moved for several minutes. I could press the Windows key to bring up the dash, but nothing would open.

I rebooted and now I can't boot Linux at all. it takes me to a black screen and I have to press CTRL + D to go back to the boot select.

I tried recovery mode and tried repairing broken packages and fail safe mode.

What can I do?

---

### Post by darkod on 2012-05-16
So, you can load recovery mode? And it works correctly?

---

### Post by insanity99 on 2012-05-16
> **darkod said:**
> So, you can load recovery mode? And it works correctly?

You mean the menu with all the options like repair, clean, fail safe mode and system summary. Yeah I can access that but that seems to be all.

---

### Post by darkod on 2012-05-16
After you select recovery mode, in the menu that appears, do you have Networking?

Select that first so it activates the network.

Then select Drop to root shell.

That should load a command prompt.

The first thing to try would be if any packages need to finish being configured:
dpkg --configure -a

See how that goes.

---

### Post by insanity99 on 2012-05-16
Thanks. It says something like eth0 Link is down. And typing commands does nothing.

---

### Post by darkod on 2012-05-16
The network is not working. Did you activate Networking from the menu first?

If you are using cable and dhcp on the network, in most cases it should work.

---

### Post by insanity99 on 2012-05-16
Well I am not wired, I'm on wireless. 

Yeah I choose the networking option on the recovery mode.

---

### Post by darkod on 2012-05-16
It's best to connect with a cable temporarily. Not sure if recovery mode can use your wi-fi card correctly.

If you boot into live mode with the cd, does the wireless internet work? In that case you can possibly enter the installation with chroot and try running the dpkg command like that.

---

### Post by insanity99 on 2012-05-28
I still don't know how to fix this.

---

### Post by darkod on 2012-05-28
Did you connect to the internet with a cable?

---

### Post by insanity99 on 2012-05-28
> **darkod said:**
> Did you connect to the internet with a cable?

No I don't have one. However I have gone on the live USB and wireless works, after entering my network password.

---

### Post by darkod on 2012-05-28
It would be easier to do it from recovery mode but if your wireless doesn't work in it, the only way is a wired connection.

Otherwise, to do it from live mode where the wireless is working, you will have to enter the installation with chroot and try it like that.

If you don't know which is your root partition, you can check with:
sudo fdisk -l

After you find it out (lets assume it's /dev/sda5, replace it with your root partition in the first command), try the chroot with:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Try to finish the configuration of pending packages:
```
dpkg --configure -a
```

Exit the chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and try to see if it helped. If you are lucky, this would finish the stopped upgrade process.

Don't forget to use your root partition instead of /dev/sda5 in the first command, if it's different.

---

### Post by insanity99 on 2012-05-28
Hey it seems sda5 is my root also. I tried doing what you suggested and I got these errors: [http://paste.ubuntu.com/1011378/](http://paste.ubuntu.com/1011378/)

---

### Post by insanity99 on 2012-05-29
Okay I used a program called boot repair. This enabled me to get back into ubuntu, 11.10 again.

When I open the update manager it said it could not update and there was a partial update option. Clicking partial update shows an error, saying the tool can't update to 12.04.

So I cancelled that and did an update, it took a really long time and I thought maybe it was doing the upgrade. But after restart it's still 11.10 but the update manager just crashes as soon as I open it.

So how can I do the upgrade now?

EDIT: Okay it's a pretty confused OS right now, tried bringing up the power settings and got this: Sorry Ubuntu 12.04 has an internal problem.

---

### Post by darkod on 2012-05-29
Even if you can boot the 11.10 kernel the system will be neither here nor there, because of the started (and failed) upgrade to 12.04.

You can try the chroot procedure again, but instead of running that dpkg command, try with:
apt-get install -f (I think that was the correct syntax to run)

That can try fixing broken dependancies.

When an upgrade fails it usually leaves a system very confused, so often a clean install is much faster.

---

### Post by insanity99 on 2012-05-30
I got this message:


neil@neil-K52F:~$ sudo mount --bind /proc /mnt/proc
neil@neil-K52F:~$ sudo mount --bind /dev /mnt/dev
neil@neil-K52F:~$ sudo mount --bind /sys /mnt/sys
neil@neil-K52F:~$ sudo chroot /mnt
root@neil-K52F:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjna-java junit4 libappframework-java libxine1-x anthy libasm2-java
  libnb-platform-devel-java libswingx-java libswingworker-java
  libubuntuone1.0-cil libxine1-console dockmanager libxine1-misc-plugins
  libanthy0 anthy-common libhamcrest-java libini4j-java
  libnb-svnclientadapter-java libxine1-bin libnb-platform12-java libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 600 not upgraded.
root@neil-K52F:/#

---

### Post by insanity99 on 2012-05-31
Okay how can I do a clean install without losing my home partition?

---

### Post by darkod on 2012-05-31
If you have it as separate partition, you use the manual method to install (Something Else), select the / partition, click the Change button and use it with the filesystem you want and mount point /.
You select the /home partition and use it with the same filesystem, mount point /home.
The swap partition is used as swap area, it doesn't use a mount point.

That should be it. The user created during the install should be the first user created in the old installation. You can create other users later.

---

### Post by insanity99 on 2012-06-01
Thanks that worked. Shame I didn't just do that last week. Thanks for the support. :D

I'm loving Unity and HUD right now, but my brother hates it, anyway to set it up so you can choose Gnome at login again? Like you could in the previous version, or the one before that.

---

### Post by darkod on 2012-06-01
sudo apt-get install gnome-panel

After you install that, each user at the login screen can select Gnome Classic by clicking the ubuntu logo next to the username. It also remembers your last choice so once you select it you only type the password next time.

That way you can use Unity and your brother gnome classic which is very similar to the older gnome interface.

---

