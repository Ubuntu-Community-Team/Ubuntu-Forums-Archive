---
title: "Upgrade 11.10 to 12.04 hung, resulting in unuseable Ubuntu"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by hornist on 2012-04-29
This is probably fairly basic stuff, but I'm quite a novice user, so bear with me.

I attempted the upgrade from 11.10 to 12.04 from within the Update Manager. It took many hours to do the downloading, so I left it overnight. When I came back to it it was somewhere near the beginning of the 'install' part of the process, with the status bar almost at the very left hand end and showing that it was installing 'busybox-initramfs'. It made no progress beyond this point, so it seems the install had frozen at this point.

I had to shut down, and now can't restart Ubuntu (I guess it's partially upgraded or something).

So my question is how to get out of this. I'm guessing the solution will involve doing an install from the 12.04 CD, but as far as possible I want to restore my working Ubuntu (with 12.04), not do a clean install. I certainly want to keep my files, which I'm sure is no problem, but also want to retain the list if installed applications and their settings.

Can anyone advise on the best way to proceed with repairing Ubuntu?

Many thanks in advance.
Paul

For info, system is an Acer Aspire M3920, intel i5 processor, dual boot Windows XP (running on its own physical disk transplanted from previous computer) and Ubuntu (installed clean onto the computer's main HDD).

---

### Post by darkod on 2012-04-29
When it boots do you get the grub menu at least?

If you select to boot into the ubuntu recovery mode, can you?

---

### Post by rafrafroufi on 2012-04-29
And if you can, try the following:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

If, as it seems, you have already downloaded all the packages for upgrading, then a sudo dpkg -i /var/cache/apt/archives/*.deb should do the trick.

Let us know!

---

### Post by darkod on 2012-04-29
> **rafrafroufi said:**
> And if you can, try the following:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

If, as it seems, you have already downloaded all the packages for upgrading, then a sudo dpkg -i /var/cache/apt/archives/*.deb should do the trick.

Let us know!

Usually for a stopped upgrade you would run:
sudo dpkg --configure -a

to finish configuring all packages. Are those commands you wrote the same?

I guess you would need to finish the configuration first before trying update and upgrade.

---

### Post by LinuxFan999 on 2012-04-29
I would recommend doing a clean install of Ubuntu 12.04 from the live CD. You can back up your data while running the CD.

---

### Post by JohnAspinall on 2012-04-29
> **rafrafroufi said:**
> ...
If, as it seems, you have already downloaded all the packages for upgrading, then a sudo dpkg -i /var/cache/apt/archives/*.deb should do the trick.

Let us know!

A question, if I may, about this approach.
Does the presence of lots of deb files sitting in /var/cache/apt/archives indicate an incomplete install?

(I'm trying to debug my own upgrade.)

---

### Post by whiskers751 on 2012-04-29
GUIDE TO RESTORING

Step 1: boot from LiveCD
Step 2: run commands:
```
sudo mount /dev/(drive and partition with Ubuntu on) /mnt
sudo chroot /mnt
dpkg --configure -a
exit
```
Step 3: reboot ;)

Donations welcome if this helped in Bitcoins:
1Cga9Zi4tHiY99z1UT1yuuXAq2uqdJB6ow

---

### Post by hornist on 2012-04-30
Many thanks for the responses.
To provide a bit more information (esp. to darkod and rafrafroufi):
Yes, I can get into the Recovery Menu. It initially shows 'read-only'.
If I try the option 'dpkg' I get various errors which scroll off the screen. It says I should use 'dpkg --configure -a' to correct.
Menu now says 'read/write'.
If I use the 'root' option to get a shell prompt, and try 'sudo apt-get install -f' I get:
   Not using locking for read only lock file /var/lib/dpkg/lock
   dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'
And if I type this command I get
   error: unable to access dpkg status area: Read-only file system
even though the Recovery Menu says 'filesystem state: read/write

If I try to do a normal boot then I get a
   ..................'GLIBC_2.14' not found..........
   General error mounting filesystems

Not sure if that clarifies things further, but thanks in advance for any additional help!
Paul

---

### Post by climberjc on 2012-05-02
Might want to look at:
[http://askubuntu.com/questions/125649/reboot-during-update-glibc-error](http://askubuntu.com/questions/125649/reboot-during-update-glibc-error)

---

### Post by whiskers751 on 2012-05-02
```
mount -o remount,rw /dev/(DRIVENAME) /
```

---

