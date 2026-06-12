---
title: "Redhat 6.2 works, no version of Ubunut does. :-("
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by nontrivial on 2008-01-25
I am a big fan of Ubuntu; we use it at work and all my machines at home run it. I have an extra laptop (Toshiba Portege 320CT, PIII 266, 96 Meg of RAM) which I love the form factor and keyboard, and I figured that is would make a nice couch web browser. I've literally spent all of my free time the last two weeks trying to get Ubuntu run on it without success. Windows 98 runs flawlessly. Redhat 6.2 installs and runs flawlessly. Ubuntu will install flawlessly and then fail to boot claiming to not be able to find the hard drive. 

I have tried about 40 different installations so far including putting the drive in another machine and various partitioning schemes (including a small boot partition as hda1). I have tried LILO and grub. I have tried Ubuntu versions back to 6.10. I assume due to a BIOS limitation (even though I have flashed the BIOS to the latest version) under windows I need to install an overlay driver to get windows to see the full 20 Gigs instead of maxing out at 8 Gigs. As I said, Redhat 6.2 works flawlessly from start to finish. When I popped the drive into another machine and got LILO installed, it did complain about the something or other not matching and I had to use the IGNORE-TABLE option to boot.

The MOST frustrating thing about this whole situation is the install always goes swimmingly, so I am baffled why it can't find the darn hard drive when booting for the first time. I have about decided to give up, install windows, putty, and firefox and call it a victory, but i figured I would give it one last shot here.

UPDATE: Just for completeness before I submitted this, I stuck in the hard drive from the perfectly fine laptop and the damn thing boots right up. So I guess now the question is, what is wrong with my HD and how can i fix it?

James

---

### Post by PmDematagoda on 2008-01-26
Both Red Hat 6.2 and Windows 98 are very old, so if you have a very old PC(I am just assuming) then it may be something to do with your PC itself. Could you post the specifications of your PC so that the real cause could be found.

---

### Post by nontrivial on 2008-01-26
As I posted originally, it is a Toshiba Portege 320CT, PIII 266 Mhz, 96 Meg of RAM and a 20 Gig HD. It is a circa 2000 laptop. What other information would you like? All versions of Ubuntu install, none recognize the HD after booting. USB, flobby, sound, video, and everything else are recognized just fine.

I have fiddled with fdisk and gpart (on a second laptop) and LILO no longer reports that the MBR is hosed and I no longer need the LILO ignore-table option. However, the Portege will still having nothing to do with it. So I have pretty much decided to swap hard drives, since each laptop seems to like the other's HD just fine. The other HD is only 10 Gig, but oh well, it looks like the office beater laptop is getting a HD upgrade courtesy of yours truly. I am a wee bit afraid that after I get the 10 Gig HD ready the Portege won't like that HD anymore either. That would be par for the course.

James

---

### Post by nontrivial on 2008-01-26
So the second hard disk had Xubuntu on it, and it was running pretty slow. So I decided in my infinite wisdom to install Fluxbuntu instead. Works great on the second laptop, won't boot on the Portege. So now neither HD will work in the Portege and both will work in the second laptop. I think it's time to install Win98 and call it a week.

James

---

### Post by nontrivial on 2008-06-22
I finally had some time to work on this again. I ended up using grub for DOS from the dos partition to boot the latest (2.6.21) Puppy Linux kernel with the standard Ubuntu (2.6.22) inird.img. It was ugly, but it was good enough to boot into Ubuntu. After that I created a custom initrd.img and it's actually pretty slick now. 

On a related note, for anybody with old, slow computers I HIGHLY recommend Ubuntu Minimal CD installer. It runs pretty damn fast on my ancient laptop.

James

---

### Post by mlmarsh on 2008-06-23
Where can I find a free download of Red Hat 6.x

---

### Post by nontrivial on 2008-06-23
I suppose if you dig around on the Redhat site you can find an ISO. I still have an install disk from way back when.

As for my problem I have decided to try different Ubuntu kernels (server and/or older) to see if that works. If not I plan on trying to recompile the standard Ubuntu kernel. Since the 7.10 intaller works, maybe I can find the configuration for that kernel. (The funny thing is starting with 8.04 the installer boots and then can't find the CD drive and fails!) I have been poking around and I think the problem may be with libata (AKA LibAtaForAtaDisks) not working on machine. The one data point I have is if the kernel understands what /dev/hda means then it works, and if it relies on /dev/sda it doesn't seem to work.

James

---

