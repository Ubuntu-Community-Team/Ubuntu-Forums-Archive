---
title: "Adding grub (both OS's present)"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by Eniliad on 2012-02-28
So, here's the deal.

When I installed the OS's on my system, I installed Xubuntu first on sdb. I later disconnected that drive in order to install Windows Vista on sda (I know, I know, but I like my games...) In order to change OS's, I currently need to go into BIOS and change the boot order for my hard drives. This... works... but it's quite annoying. I was wondering if it was too late to install GRUB and set up a way to select OS at startup. Like I said, both OS's are already installed, and both think they're the only OS on the computer.

The hdd and partition setup is as follows:

Windows has sda (160GB) and a partition at the very end of sdb (appx 175GB of 500) available to it.
Xubuntu has the entire rest of sdb.

If there's any more info you need, I'll be happy to give it.

---

### Post by lkraemer on 2012-02-28
You should be able to do that easily................but, I'm no
Grub/Grub2 expert.  

REF's:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
[http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub](http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub)
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)
[http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub](http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub)
[http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub](http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub)


lk

---

### Post by Mark Phelps on 2012-02-28
If you can boot from the Ubuntu drive, then GRUB is already installed on it.

Simply do the following:
1) Connect up both drives -- but continue to boot from the Ubuntu drive
2) Open a terminal in Ubuntu and enter "sudo update-grub".  That will regenerate the GRUB default config file and add entries.  Watch as it works, and you should see it find Windows.

When you reboot, you should then get a GRUB menu.

---

### Post by Eniliad on 2012-02-28
Hey guys, thanks for writing back. :)

Mark, I did what you suggested, but it didn't seem to mention Windows... when I rebooted, it booted directly to Xubuntu again and did not present an option. I ran sudo update-grub again, so I could show its output:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-3.0.0-16-generic-pae
Found kernel: /vmlinuz-3.0.0-16-generic
Found kernel: /vmlinuz-3.0.0-12-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Do I need to change it so that my Windows drive (sda) is the primary in order to get GRUB to work? Or is there a step I'm missing... or is there a config file I can edit?

---

### Post by darkod on 2012-02-28
Does xubuntu come with grub1 or grub2?

The auto OS detection works with grub2, but the /boot/grub/menu.lst file reported on your computer is used with grub1 and it shouldn't exist in grub2.

If you could run the boot info script from the link in my signature and post the results as explained there, it would be interesting to see if you have grub1, or grub2, or a mix of both.

---

### Post by Eniliad on 2012-02-29
Hello,

I've run the boot script as requested. I've uploaded the output to a Pastebin, here:
[http://pastebin.com/yN89ZzV1](http://pastebin.com/yN89ZzV1)

Thank you for the reply. :)

---

### Post by darkod on 2012-02-29
You have quite an interesting setup. You don't have grub2 on any MBR but instead it is on sdb1 and you seem to be booting it with the boot flag. I have never seen working like this unless it's chainloaded into windows bootloader, which in your case it is not the way you describe it.

Also, you do have a mix of grub1 and grub2 files which creates some confusion I guess.

It's best from live mode to enter your installation with chroot, clean up everything and reinstall grub2, putting it also on the MBR of /dev/sdb. If you would like to do this you need to boot with the cd into live mode and run:
To mount the partition and enter chroot:
```
sudo mount /dev/sdb1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

To completely remove grub1 and grub2, and reinstall grub2:
```
apt-get remove --purge grub grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sdb
```

To exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

That's it. Reboot and see how it goes. Note that if you boot from /dev/sda in BIOS you will still boot directly into windows, but if you boot from /dev/sdb you should get the grub2 boot menu with options for ubuntu and windows.

---

### Post by Eniliad on 2012-03-01
Hey guys! Sorry it took me a couple days to respond; I've been busy (unrelated). Anyway, had a bit of fun on this one. I booted into the CD and attempted to do what you guys said. This is the result, loosely recreated from memory (sorry, forgot to log it).

```
sudo mount /dev/sdb1 /mnt
```
This worked.
```
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
```
This did not. Each one in turn spat the same error, a variant on "this does not exist".
```
sudo chroot /mnt
```

This failed too. Against my better judgment I decided to truck on.

```
sudo apt-get remove --purge grub grub-pc grub-common
```

Done.

```
sudo apt-get install grub-pc
```

This failed because it couldn't figure out where to install to.

At this point, I rebooted my system into my Xubuntu installation and tried the installation again, as su. Lo and behold, it installed, and I now have a GRUB menu at startup.

So, to sum up what I did: I ended up removing GRUB via CD and installing it again via Terminal on my login. I'm not sure if that's what's supposed to work, but it did, it found Vista, and... I'm going to back away, hands in the air. "Don't... touch... it works..."

---

