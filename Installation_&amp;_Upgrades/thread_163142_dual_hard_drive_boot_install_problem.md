---
title: "dual hard drive boot install problem"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by greene on 2006-04-20
hi

as far as i can tell this is slightly different from the installation threads i have been reading, so prompts my own posting...

i have 2 hard drives one SATA (with Win XP) and one IDE which I want to install Ubuntu 5.10 onto. The problem is that I believe my MBR for loading Windows XP on the SATA drive is actually on the smaller IDE drive. 

My fear is that if I install Ubuntu onto the IDE drive, will I lose the MBR for Win XP and thus not be able to boot to Windows? I previously had them installed seperately on each respective drive, but had to remove either the SATA cable to boot to Ubuntu or the IDE cable to boot to XP which was a real pain, as you may appreciate. 

Ultimately, I could (if any easier solution is not forthcoming) be preapared to re-install both from scratch...but would prefer if their was a way of avoiding that scenario. 

I hope this does not irritate any potential support from the community on this, but I need to confess that I am a complete linux code novice/virgin and am hoping I don't have to "go there"...

i hope someone can help. i have previously always used mandrake/mandriva, but have been very impressed by Ubuntu in the short space of time I have used it.

To recap, at the moment XP is installed on the SATA drive), Ubuntu was installed on the IDE (but now isn't) because I reformatted and re-installed Windows (on SATA drive) but during XP installation, I think the MBR was written to the IDE drive (In fact, if I remove the IDE cable now, XP does not boot - which I think proves this theory)

apologies if I have over-egged the description of the predicament.

cheers
greene

---

### Post by Ocxic on 2006-04-20
check youir bios to make sure of your drive order, and put your ide drive first, then just install ubuntu on the ide drive, grub will fond you XP install and add a grub enetry for it, it won't overwite the windows MBR, if you're really worried then just tell grub to intall to a partiton and not the MBR it will/should ask.

---

### Post by greene on 2006-04-20
thanks for such a prompt (reassuring) reply. I will try this out and post my success/failure later.

---

### Post by greene on 2006-04-20
i checked bios as advised, and installed Ubuntu 5.10 onto the IDE hard drive, however, during the install i was not given the option to install grub either to a partition or to the mbr. i am now unable to boot to XP which is on the SATA drive, my pc just boots to Ubuntu . When Grub loads, it only lists Ubuntu options. Help! Is this a reconcilable problem? 
cheers
greene

---

### Post by Ocxic on 2006-04-21
ok I'm going to assume that your only have the ide and sata drives, and your ide drive is the first drive on your system. if this doesn't work, try reversing the map commands

add this to your /boot/grub/menu.lst
```

title              Windows XP
root               (hd1,0)
savedefault
map                (hd1,0) (hd0,0)
map                (hd0,0) (hd1,0)
chainloader        +1

```

---

### Post by greene on 2006-04-21
thanks for your response. there is just the sata and ide drive. 

before seeing your last post, i ended up doing a fresh Win XP install, having taken the IDE cable (and therefore IDE drive) out of the equation. So, having bitten the bullet with Windows and reformatted and re-installed, I'm okay about starting again with a fresh Ubuntu install too, as this is less of an inconvenience anyway. 

What do I need to do during the install so that I get the GRUB options? - as they did not appear in my previous installation. In the previous install sequence I was asked if I wanted to erase all of the IDE drive or erase all of the iDE drive with LVM (???). I chose the latter and then it automatically partitioned and installed and then loaded.... and then whenever I rebooted it went straight into loading Ubuntu...ie no option to select XP.

I appreciate the command line stuff you mention, but if I'm honest (and I will be) I don't know how to go about initiating what you have suggested. I'm THAT kind of novice.

I really want to use Ubuntu, but I may resign myself to going back to Mandriva, as the install for that distro sorted out what I wanted without too much pain...

---

### Post by mikeyman77 on 2006-04-21
I have a sata hd and an ide hd.  My sata drive is the one I want to install ubuntu on and the IDE drive is strictly for storage of backup files with no os on it.  I set my sata drive as the first boot device and I would install ubuntu and after the install goes to reboot, it will not boot.  For some reason even if I make the sata drive the first boot device, it thinks its hd1 not hd0, and during the install it it installed grub on the hd0 which is my IDE, do in order to boot my system i have to set the IDE as first boot device.  They need to make it so you can tell it where you want grub installed.  It took me a couple tries to figure out why it wasnt working.  So basically ubuntu installed on hd1 but the boot loader is installed on hd0 master boot record which makes no sense at all.  Im going to attempt to remap the drives so that sata drive is hd0 and ide drive is hd1 and reinstall grub on sata drive.

---

### Post by Ocxic on 2006-04-21
grub has a problem with booting from SATA drives, I've never been able to get it to work, I just go off my IDE drive, there's really no performance difference.
and what you going to do mikeyman will prolly work, but don't re-install grub if it still able to load.

---

### Post by greene on 2006-04-21
just to wrap up my initial posting...

for whatever reason my first installation of ubuntu (on IDE drive) did not recognise windows XP (on SATA drive) in grub via the mbr. 

I re-installed fresh Win XP on the SATA drive minus IDE cable. then reconnected and re-installed Ubuntu on IDE drive and during the install, grub recognised Win XP in the mbr and so now I am dual booting successfully.

job done. many thanks for the spirit of support, which attracted me to Ubuntu in the first place.

---

