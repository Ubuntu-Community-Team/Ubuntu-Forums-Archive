---
title: "Partitioning with SSD and HDD"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by Giraffemonster on 2012-12-23
Hey all,

I have a 60GB Mushkin SSD, and a 1TB Seagate Barracuda. After using Xubuntu for I think two years, I installed Windows 7 as an only OS for gaming. Now I'm kinda bored with that and I'd like to go to Debian with KDE. I'm pretty sure this is the same for all distro's though.

I'm planning to dual-boot Debian just to see if everything's alright and the graphics drivers don't bug me too much. Right now, my SSD has 35.3GB available.

So my real question, I guess, is what partitions would be best to put on 35.3GB of SSD space? Heard about "write-bombing", yet I still sometimes see people mention putting /tmp on there, so it'd be helpful to hear more about that.

And if I happen to get rid of the Windows 7 partition eventually, am I able to move more directories onto the SSD, or do I have to re-install Debian?

---

### Post by oldfred on 2012-12-23
I have a 64GB SSD and have two Ubuntu installs on it. I also keep my /home inside / (root) but have all data linked to my data partitions on my rotating drives.

Right now I have 12.04 and 12.10 on my SSD, and probably will keep 12.04 as my working install for a while. Something about spouse complaining about changes every 6 months. :) But I have 13.04 on my rotating drive and will install it to the SSD when it is final.

         Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)


The main things I did, I have a swap on rotating drive but with 4GB of RAM almost never use any swap:
       
 With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

    
Some also discuss mounting tmp locations but I have not.

---

### Post by cybrsaylr on 2012-12-23
Did something similar. Here's what I did and it runs fine.

Have a 128GB SSD with 12.04 and a 2TB HDD partitioned in half with W7 on the front and the second partition for mass storage. 

At first I didn't even use a boot loader. Had it set to boot directly up to Ubuntu because W7 is seldom used anymore. If W7 was desired all I did was hit F12 when powering on, during the Dell splash screen, then select from the F12 boot options, the HDD and W7 booted up.

This was working fine for a week and then to my surprise, during one of the Ubuntu updates the GRUB boot loader was installed! Now I see the usual GRUB boot loader which was auto configured for my 2 drive setup. Was really surprised to see boot loader installed like that.

---

### Post by MG&amp;TL on 2012-12-23
> **cybrsaylr said:**
> ...and then to my surprise, during one of the Ubuntu updates the GRUB boot loader was installed! Now I see the usual GRUB boot loader which was auto configured for my 2 drive setup. Was really surprised to see boot loader installed like that.

Side note: I had something similiar and this happened: did some digging and found that when the 'grub' program is updated, it's post-upgrade script includes re-installing itself, which in the process resulted in the other OSs being detected on the second disk. Be wary of updates. :)

---

### Post by cybrsaylr on 2012-12-24
MG&TL, thanks for the explanation. 
Was curious about how that happened.

---

### Post by Giraffemonster on 2012-12-24
Thanks for the replies. I don't think I'm going to have any trouble with GRUB, since I'm not sure how often I'll need to boot up in Windows. That's pretty interesting though, I might consider just automatically booting Debian if everything's fine.

And the links were helpful too. So, would this work?

SSD (55.7GB of logical space)
Around 20GB of Windows 7 files
10GB of unpartitioned space for over-provisioning.
Should be 25.7GB to {
/bin
/sbin
/usr
/lib
/opt
/etc
/boot
}

HDD
Everything else on Linux
Windows data partition
/swap (I have 8GB of RAM, should I have /swap in the first place?)

On the side, when installing programs through .deb's, can I specify the installation directory? Games from the HIB might take a bit too much space to all fit on the SSD. On Windows, all of my bigger games (Bigger than 500MB) are on the HDD.

If that's not possible though, it's all good. I can just use the .bin based installers instead.

---

### Post by darkod on 2012-12-24
> **cybrsaylr said:**
> MG&TL, thanks for the explanation. 
Was curious about how that happened.

There is nothing to be wary about. Grub2 automatically detects all other OSs to help the user instead of letting him make the entries and commands manually.
If you had the win7 disk disconnected during ubuntu install, it couldn't see win7 and make an entry for it.
On next grub2 update it will run the update-grub as part of the update, which will detect all other OSs and add them to the boot menu.

If you don't want windows or any other OS detected automatically (including any linux OS except the main ubuntu), simply make the os-prober script unexecutable and update the grub.cfg again after that so that the change take effect:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

After that there will be no win7 in the grub boot menu. You can make it executable again with the same command using +x instead of the -x.

---

### Post by cybrsaylr on 2012-12-24
> **darkod said:**
> If you don't want windows or any other OS detected automatically (including any linux OS except the main ubuntu), simply make the os-prober script unexecutable and update the grub.cfg again after that so that the change take effect:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

After that there will be no win7 in the grub boot menu. You can make it executable again with the same command using +x instead of the -x.

Thanks, nice to know.

Kinda liked bypassing GRUB and going directly into Ubuntu since W7 is very seldom used. At least I now know how to avoid that several second delay that GRUB causes if I decide to bypass GRUB.

---

