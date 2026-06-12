---
title: "Encrypted LVM Blank Screen"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Enjoi4586 on 2011-05-19
Hello everyone, I just performed a fresh install of Ubuntu 11.04, Encrypted LVM install. I am getting a blank screen during boot, but can still type my passphrase and boot like normal.  I've been reading through the stickies at the top of this section with no luck on how to resolve it.  I'll start with my original issue and steps taken so far.

I performed a fresh install of Ubuntu 11.04 Alternate install and used the guided full disk encrypted LVM option on my Dell XPS M1530.  After finishing the install -with no problems- I rebooted to a screen that said "Error: No video mode activated".  I rebooted again, to get to the Grub selection screen where I attempted to boot (again) normally.  After selecting the normal boot option, I went to a blank screen where it did nothing.  I then tried to boot to rescue mode, where I could sucessfully put in my passphrase and decrypt my LVs.  I looked around a little bit and found a few sites suggesting this might be the solution:

```
cp /usr/share/grub/*.pf2 /boot/grub/
```

I did that and then did performed a Grub update

```
sudo update-grub2
```

To an extent, that worked in enabling me to boot the OS.

 I'll try to explain this next part the best I can, I'm not really sure exactly what happened.  It went to a graphical luks passphrase screen sort of mangled up, but after pressing the up and down arrow keys a few times, the screen looked like what I presume it should look like.  I entered my passphrase, booted it up normally.  Now after rebooting, it goes to a slightly off black screen, where I just type in my passphase and it boots up.

Is there any way to solve this?  Thanks everyone.

---

### Post by Enjoi4586 on 2011-05-24
My post doesn't seem to be getting any love, is there any information that I can provide that will make my post more diagnosable?  

Again, it boots up, just not with any graphics or viewable text.

---

### Post by barbobot on 2011-06-18
I have this same problem. However I am able to put in the password during the blank screen and get into the system. I'll post again if I find a real solution.

---

### Post by bobbieboucher on 2011-07-29
Wish I'd read these posts about 25 minutes ago...

I'm having the same issue after a clean alternate install of 11.04 using this LVM guide:

[http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/)

---

### Post by scorbett on 2011-08-07
Same problem here, fresh install of 11.04 with encrypted LVM, boots to a blank screen and proceeds to do absolutely nothing. Apparently this is a known issue:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/745960](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/745960)

Something about the grub config file not being created by the installer. Several people on that bug link claim that booting from the install cd and selecting "boot from first hard disk" allows them to bring up the system and then manually repair the grub config, but I have not had any success with this. 

Does anyone have a workaround for this? It's extremely annoying.

---

### Post by scorbett on 2011-08-09
Tried again with a fresh install of ubuntu 10.10 using the alternate installer - exact same problem.

---

### Post by shizow on 2011-09-09
same problem here, one can enter the passphrase in the darkness and it boots

same problem in this thread [http://ubuntuforums.org/showthread.php?t=1748332](http://ubuntuforums.org/showthread.php?t=1748332)

---

### Post by bakinsoda on 2011-09-15
I too had this blank screen issue for my encrypted LVM setup.  I found out that grub was installed on my usb installation drive instead of my hard disk.  After re-installing grub onto my disk, I no longer get the blank screen.  See my adventures [here]("http://blog.nguyenvq.com/2011/09/15/backup-re-install-ubuntu-with-full-disk-encryption-and-restore-all-files-and-settings/").

---

### Post by Mountaingod on 2011-10-17
Same problem here with Oneiric ( 11.10 ) , and dm-crypt (i.e. non LVM encrypted) root partition + random-key encrypted swap.

Originally, I got the "no video mode activated" error followed by a text-based prompt for password. The behaviour now is exactly the same as #27 here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802")

Based on the above links it's something to do with the graphical password prompt using incorrect display settings...

FWIW, I'm on a Toshiba Satellite C660 (which has integrated intel i3 / HD graphics).

---

