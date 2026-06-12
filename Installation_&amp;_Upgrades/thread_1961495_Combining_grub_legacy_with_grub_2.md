---
title: "Combining grub legacy with grub 2"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by PedroGomes on 2012-04-19
Hi, I have a Ubuntu installation in on partition and I'm now installing a Enterprise Linux variation on the second partition. Having coded the kickstart file to preserve the partitions, my problem is now with grub. As this kind of linux comes with grub legacy I'm now in doubt in how to deal with this two flavors of linux/grub. 

I have tried to force Ubuntu to use grub legacy on /dev/sda (mbr) and then install the second linux pointing grub also to the mbr with: 

```

bootloader --location=mbr --append="nofb quiet splash=quiet " 
[FONT=Arial][SIZE=1]
This ends up not detecting Ubuntu forcing me  to insert the entries by hand/script. 
This maybe solved by Kickstart, being this not the best place to ask about this, I assume. [/SIZE][/FONT][SIZE=1]
[/SIZE]

```My question is: is there a better strategy for this? Can I still use grub2 (what are the real advantages)? I'm doing right putting the boot loader pointing to the disk mbr in both installations? :confused:

---

### Post by darkod on 2012-04-19
If EL has an option not to install a bootloader, I would do it like that.

Yes, you are right poiting the bootloader to the MBR but only the latest installed will be there because the earlier gets overwritten of course.

I would install ubuntu and let it install its grub2 to the MBR.
Then when installing EL look for Advanced options during the installation, and choose not to install a bootloader.

On first boot only ubuntu will be there. Boot it and run:
sudo update-grub

That will detect EL and create the needed entry in the grub2 boot menu.

---

### Post by ajgreeny on 2012-04-19
When you install this new version with legacy grub, put grub on the OS partition, not on the MBR.  Ignore any warning about it not being recommended, as you will not be using that grub in any case.

Now reboot back to your ubuntu with grub 2, and run sudo update-grub, which will add the new OS to your old grub menu, allowing you to start it when you want to from the grub menu.

EDIT:
Too slow, but basically the same advice.

---

### Post by PedroGomes on 2012-04-19
Yep that works. Thanks guys! 
I would like that I wouldn't have to return to Ubuntu after the installation, but it works and that is what matters.

---

### Post by darkod on 2012-04-19
Well, you do that only the first time. Now that it is in the boot menu, you can select which OS you want when you boot and never need to go into ubuntu if you don't need to.

---

### Post by oldfred on 2012-04-19
Not really any different, but old grub legacy never complained about installing to a partition - PBR. Anw we used to chainload grub legacy all the time.

So you could install the grub legacy to the PBR. And then in Ubuntu's grub2 40_custom add a chainload entry. The disadvantage is on every boot you get a second menu from grub legacy, but the advantage then is that you get the grub legacy kernel updates without having to boot into Ubuntu and running sudo update-grub.

---

