---
title: "can grub boot chain from one hd to another?"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by moshuptrail on 2012-12-17
I have this old HP desktop.  It has two HD's, C and D.  

A long time ago I had installed Ubuntu 10.x on drive C after Windows XP.  Later I ran out of space on C and installed Ubuntu 12.10 on drive D but the system insists on booting from drive C.

So each time I update 12.10 I must then boot 10.x and run update-grub in order to update the boot.cfg with the entry for the new kernel for 12.10 on the D drive.  Grub picks it up in the "other_os" section.

Each time I boot, I must scroll down all the way to the end to find the "other_os" (my 12.10 Ubuntu on the other HD) There's really no way to set a default.

Running update-grub while booted on the 12.10 Ubuntu (drive D) has no effect as that boot.cfg is not being used bu grub.

Is there any way to "chain" from the boot on drive C to drive D?

Or am I going about this all wrong?

I suppose I could re-strap the hard drives so the BIOS would switch them.  Ugh.

---

### Post by dino99 on 2012-12-17
hopes your both OS use the same grub2 (grub-pc) because it is known to be disturbed if grub1 (grub-leagacy) is still around with its oldish menu.list.

If several grub installation exist, then one is the master and need to be re-run to update changes made on an other OS partition.

---

### Post by darkod on 2012-12-17
There are few things you could do, depending what you consider easy and what do you wish to end up with. Yes, grub can chain to another grub/hdd.

Try something like this in your 10.04. Create a copy of 40_custom which would be above the 10.04 ubuntu entry (if you want to, if not skip this step):
```
sudo cp /etc/grub.d/40_custom /etc/grub.d/06_custom
```

Open that file for editing (or the 40_custom if you skipped the above step):
```
gksu gedit /etc/grub.d/06_custom
```

Make a simple chainload entry which should be like:
```
menuentry GRUB2 on HDD2 {
set root=(hd1)
chainloader +1
}
```

Run update-grub to recreate new grub.cfg. Reboot and you should see that entry on the top (that was the point creating the 06_ file). Check if it works.

---

### Post by moshuptrail on 2012-12-17
That looks like it would do the trick!  Very clever.

Is that chainload entry EXACTLY how it would look, or do I need to modify it for my system?

---

### Post by darkod on 2012-12-17
You shouldn't need to modify it. The first boot disk is hd0, and the second hd1. You want to jump to hd1 and then use the chainloader +1.

Only note that I first put by error "chainload +1". It should be "chainloader +1".

Also I am not sure if the title GRUB2 on HDD2 should be in " " marks or not. Try it without first then with.

---

### Post by oldfred on 2012-12-17
I use the commands as Darko has posted.

But I also use these:
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

I also learned from Ranchhand as Cavsfan mentions, except Cavsfan has documented it and many other features. This boots a partition as Ubuntu puts a link in / (root) for the current install. Then you do not have to run update grub in both systems.

 menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

When I specify a drive and use my flash drives to choose another MBR, I often have to use the e in grub menu as the boot drive is always hd0, then every other drive is numbered in SATA port order. But my flash drives seem to be somewhat random. Probably which drive BIOS sees first.

---

