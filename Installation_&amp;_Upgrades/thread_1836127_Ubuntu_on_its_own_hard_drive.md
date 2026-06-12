---
title: "Ubuntu on its own hard drive"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by pasisti on 2011-08-30
Hi

I'm currently waiting for the ubuntu 11.10 to start using Ubuntu again in dual boot. I have Windows 7 x64 on the HDD now and I'm thinking about buying another HDD for Ubuntu, just in case.


Would it work like this:

I plug in the second HDD and set it to be the booting device from BIOS. Then I start to install Ubuntu on that drive and have the GRUB install on that drive also (it should go there automatically as it's the main HDD?). Then if something goes wrong at any time, I can just make the windows HDD the primary boot device again and wipe the Ubuntu HDD clean? This way I wouldn't have to worry about the windows MBR at any time.

I already have my windows drive in two partitions, one for files and one for programs and the OS. It's 1TB so there would be no problem with space but I would like to be careful as I intend to play around a bit with Ubuntu :) And a good & fast 320GB HDD is only 40 euros so it's not a big deal..

---

### Post by YesWeCan on 2011-08-30
> **pasisti said:**
> 
Would it work like this:

I plug in the second HDD and set it to be the booting device from BIOS. Then I start to install Ubuntu on that drive and have the GRUB install on that drive also [COLOR=Red](it should go there automatically as it's the main HDD?[/COLOR]). Then if something goes wrong at any time, I can just make the windows HDD the primary boot device again and wipe the Ubuntu HDD clean? This way I wouldn't have to worry about the windows MBR at any time.

I already have my windows drive in two partitions, one for files and one for programs and the OS. It's 1TB so there would be no problem with space but I would like to be careful as I intend to play around a bit with Ubuntu :) And a good & fast 320GB HDD is only 40 euros so it's not a big deal..
Hi there. Your approach is very good and boot loader conflicts are avoided if Ubuntu is on a separate disk (or at least the Ubuntu boot loader is on a separate disk). The Ubuntu installer is rather dumb tho because it defaults to putting Grub on sda regardless of which disk it is being installed to. So there is a possibility that your Windows disk will be called sda.

To avoid accidentally putting Grub on your Windows drive you can either disconnect it during the Ubuntu install or you can select the "special" or "something else" or whatever option in the installer and explicitly select the boot-loader disk.

For an easy life, disconnect the Windows disk. After installing Ubuntu, shutdown and reconnect the Windows disk. Boot the Ubuntu disk and run [COLOR=Navy]sudo update-grub[/COLOR] to give you a menu offering either Ubuntu or Windows the next time you boot.

Have fun. :)

---

### Post by elliotn on 2011-08-31
> **YesWeCan said:**
> Hi there. Your approach is very good and boot loader conflicts are avoided if Ubuntu is on a separate disk (or at least the Ubuntu boot loader is on a separate disk). The Ubuntu installer is rather dumb tho because it defaults to putting Grub on sda regardless of which disk it is being installed to. So there is a possibility that your Windows disk will be called sda.

To avoid accidentally putting Grub on your Windows drive you can either disconnect it during the Ubuntu install or you can select the "special" or "something else" or whatever option in the installer and explicitly select the boot-loader disk.

For an easy life, disconnect the Windows disk. After installing Ubuntu, shutdown and reconnect the Windows disk. Boot the Ubuntu disk and run [COLOR=Navy]sudo update-grub[/COLOR] to give you a menu offering either Ubuntu or Windows the next time you boot.

Have fun. :)

yep great advise

let grub list both OS in both HDD rarther than always disconnecting the HDD

---

### Post by pasisti on 2011-08-31
Thank you for the advice!

I'm looking forward to installing Ubuntu with this information :)

---

