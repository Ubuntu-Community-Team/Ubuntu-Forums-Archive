---
title: "Xubuntu 7.10 installs but won't boot, 6.06LTS does boot"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by mpstarix on 2008-03-01
Hi !

This is my first post on this forum.
Here is what it's all about :

I own an old Celeron, with 3*128 Megs of RAM, that works with XP.

I wanted to update it to Xubuntu, so I downloaded last alternative ISO and installed

It took me one day to figure out why it crashed after a few seconds : I have faulty RAM (thanks to memtest I have seen it) so I ran the installer with "mem=256M" and it installed right.

After reboot, though, even if I had to add "mem=256M" by myself, I won't work.

I get a couple of ata1 bus reset, then ldm_validate_partition_table() failed. Then I am redirected to a (initramfs) shell, where I don't know what to do.

I have tried the "nodma" option. It did nothing. Then "ide=nodma" that did not work any better.

So I downloaded 6.06 desktop ISO. I can boot it using "mem=256M" but there will be no other sda* than /dev/sda in /dev. fdisk /dev/sda works, though. Looks like it only fails at boot time, and I just don't know how to repopulate /dev

When I boot 6.06 using "mem=256M ide=nodma" then it works ok : i get /dev/hda, /dev/hda1, /dev/hda5 (swap)
Of course, /dev/hda1 is mountable and error free.

Now I would like to know how I can get 7.10 to work :
* kernel switches at boot time ? (to disable libata and get back to good old ide driver if there is no other way)
* recompiling a kernel ?

Basically, I can post whatever you want (lspci, dmesg, ...) but I just can't figure out how I can get the kernel boot log when it crashes...

Thanks to anyone who can help !

---

### Post by tomiscool on 2008-03-02
" **[SIZE="5"][COLOR="Navy"]Legal responsibilities[/COLOR][/SIZE]**"
"**[SIZE="5"][COLOR="Navy"]i do not take any responsibility for ur computer if it doesn't turn that will be under ur responsibilty u follow this at ur own risk[/COLOR][/SIZE]**"


ok make sure the drive ur using is set to master on its jumpers and if anther hard drive its jumper settings are slave as well this is only available if the hard drive is using ide connectors. If it is sata hard drive then its master settings are automatic usually both are master of what my bios does. Any way if ur using sata make sure where the sata drive is conneted is connected to the sata one slot on the mobo (motherboard)"just in case if u didn't know" lol (no harms ment) ok well if u have another sata hard drive of course just put it in number 2 slot. Now make sure to have all connectors tight especially the power connectors for the hard drive all u need to do now is start to configure everything. First u need to make sure things that are not connected to the mobo like floppy, usb front panel 2.0, etc anything else ur mobo may support but u do not have connected disable them as long as u know what ur doing. Now When it comes to the cd drive make sure the mobo "to be safe" has it shown as "cd drive" and ur hard drive as "hard drive" if it has that feature. You can do this in the first bios menu by selecting the drive now what u need to do if ur hard drive doesn't have a "hard drive" feature is to just leave on auto or w/e it was before. Okay now save the settings and lets reboot, Before it reboots u might want to take the cd out to make sure there is not scratches on the cd if no huge deep scratches are present then put the cd back in. What were going to do is install a fresh copy of ubuntu 7.10 (also make sure the type of architecure your computer is if it is traditional x86 then use the x86 one but if it is 64 bit u dont need to but its faster also there is alot of things not so great with 64 bit version that usaully other hardware just doesn't support it) on ur computer since it seems u want it so bad lol now what u do is check cd for errors which u'll see in the cd menu and then let it check becuase its important that the cd is not damaged or unable to load important files now if it says theres nothing wrong then we should not have any problems it will reboot then once it reboots into the cd then press start/ install once u did that u should see it loading and just cross ur fingers if it dont work then its a hardware prob.  Your computer probably doesn't support it." i do not take any responsibility for ur computer if it doesn't turn on becuase of certain mobo settings that will be under ur responsibilty u follow this at ur own risk" just to say if ur computer doesn't turn on and make the beep noise or just doesn't turn on then if u know just reset cmos im sure u do lol but if u dont look at the motherboard manual or computer manual ok hope this helped srry the reply is so big and long lol

:popcorn:

---

### Post by tomiscool on 2008-03-02
when i said sata one i meant sata one slot and the same goes for the second sata lol

---

### Post by mpstarix on 2008-03-03
I just don't get it : I don't have a problem with the BIOS ! It's just that using libata just prevents me from booting, especially because "ide=nodma" seems to be ignored.

And i can't find a way to use the good lod ide driver...

---

### Post by zxscooby on 2008-03-03
Faulty RAM you say?  id try replacing that first.
will it boot to the command line in recovery mode?

---

### Post by mpstarix on 2008-03-03
Well the faulty RAM is handled with "mem=256M" whereas I have 380 useful Mb of OK ram and the last 4 Megabytes that are faulty

I haven't tried recovery mode. Yet.

But in the busybox shell I'm arriving in, I have been able to type
ls /sys/modules/libata/
and there, I realized that the libata.dma=0 was just UNSUPPORTED by that version of the kernel.

I'm downloading a Hardy Heron Iso to get a more recent (ubuntu flavoured) kernel.

---

