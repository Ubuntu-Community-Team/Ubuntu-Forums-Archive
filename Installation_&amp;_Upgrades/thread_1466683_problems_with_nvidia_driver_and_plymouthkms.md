---
title: "problems with nvidia driver and plymouth/kms"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by symon1980 on 2010-04-30
hey guys

ok... ubuntu 10.04 is installed... proprietary nvidia drivers are installed, nouveau driver is blacklisted via /etc/modbrobe/blacklist.conf

all is sweet... i can use my nvidia driver.... but
the problem is.. now the ubuntu splashscreen resolution is all messed up.. and i have no framebuffer when I log into a konsole.... (i know kms doesn't support proprietary nvidia drivers)

but... has anybody figured out how to fix the ubuntu splashscreen resolution problem... and if possible... how to fix the framebuffer so that the konsole can be at a nice resolution? I tried setting vga settings under GRUB_CMDLINE_LINUX="" in /etc/default/grub with no success... 

PLEASE HELP
:)
im disappointed with ubuntu.. its basically a noob distro and shouldn't require this much intervention to get things working correctly... with nouveau the splash screen was perfect and framebuffer/kms but i need to be able to use compiz and games...no proprietary nvidia drivers then no compiz, no games.... 

any ideas guys? c'mon... don't fail meeeee! :)

---

### Post by kamikazepsi on 2010-04-30
i'm in the same boat that you're in.

acer w/ nVidia GeForce 8200:

the splash screen is corrupted on both startup and shutdown once i enable any of the nvidia 3d accelaration drivers but it goes away when i disable it

compaq w/ nVidia Geforce 6150:

same problem but disabling the driver doesn't get rid of the corruption.  i'm a linux amateur so i was force to do a complete reinstall after trying everything i could think of.

---

### Post by Gadwil on 2010-04-30
This is an issue with the proprietary drivers.  Noveau works perfect with Plymouth.  So far I have not found a fix, just deal with it, or turn off Plymouth by telling it to show text during boot.

---

### Post by fazza on 2010-04-30
To be honest I'm pretty disappointed with this too, and I've followed a long thread on how to fix this (which reallllly shouldn't be necessary in 2010 ¬.¬), which didn't work. Great.

I have a geforce 8600gt, and plymouth worked perfectly with the noveau driver.

---

### Post by symon1980 on 2010-04-30
another stupid decision by canonical! ffs
plymouth/kms works great with nouveau... but the problem is nouveau just plain sucks! its not even at the point where it can support compiz! forget about any 3d gaming.... surely they would realise that Nobody with nvidia cards will want to use this crap driver! and when you want to use the closed source driver that works... it messes stuff up! 
I don't know whether canonical are just plain stupid, ignorant... or don't even realise these things themself... Ofcoarse this is going to cause problems for people! Ubuntu is suppose to be for the majority of people who are not very tech savy... not to mention this is an LTS and they give us this crap to deal with....

This has really Pi#$ed me off... why enable new technologies by default that are nowhere near ready for the masses... they did this with pulse audio too....

If canonical want to compete with the big boys... this is not the friggin way to do it... it is very unprofessional to make decisions like this... I think Ubuntu need a leader who is not retarded and is capable of making the right decisions

Back to Arch linux I go.... I installed ubuntu because I wanted something that worked out of the box with minimal user intervention... pfftttt. I know I can disable plymouth but thats not the point... Canonical are retarded.

ahhhh I feel better now

---

### Post by kamikazepsi on 2010-05-01
Is there a way to turn off the splash/loading graphics? 

i will gladly sacrifice the boot and shutdown eye candy in favor of having a fully functional computer w/ 3d acceleration.

---

### Post by kamikazepsi on 2010-05-01
well, turning off the splash graphics just reverts the boot process to corrupted text outputs....

after constant googling, i'm beginning to think the only thing we can do is wait for full 3d support on nouveau.....?

---

### Post by kamikazepsi on 2010-05-01
another update...

this seems to be the best fix available at the moment. easy to follow, and everything works flawlessly now.  a few people report that this fix adds a few more seconds to their boot time but i'm still clocking ~25 second boots.    

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by symon1980 on 2010-05-02
I can confirm that tutorial worked flawlessly

---

### Post by Forbidden on 2010-05-02
I *wish* all I had was this problem.  For me, installing the nvidia drivers bricks the system.  Can't even boot single user.

This is all because Shuttleworth got a hard on for faster boot times.  I boot my workstation maybe once a month.  I could care less what the boot looks like or how long it takes.  But to shackle an LTS release to a system that can't even boot because of graphics drivers is absolutely absurd.

---

### Post by Neremor on 2010-05-02
I absolutely agree on this, it's really stupid to release an LTS-version that can't even boot on many people mashine's because they are using new ati, nvidia or intel cards. For me it is not only the splash that is not working, I can't even login after a fresh installation. All I get to is the tty1... What confuses me most is the fact, that canonical tells users that updating software endangers stability and provides software upgrades only with major os-releases, and then they kill the whole system of many people just through this careless and not enough tested LTS-version upgrade or installation on the other hand. If there would be an alternative to all the nice things ubuntu usually provides, i would have changed the distribution allready a long time ago. I, for my pont, am not able to spend many hours fixing a broken, fresh installation and applying some fixes for problems I did not even produce. I will have to miss the benefits of a computer for the next days or weeks, I think, and can only hope that an official upgrade to fix this problem will be released soon...

Greetings,
Jonathan

---

### Post by symon1980 on 2010-05-02
There won't be an official update to fix this problem... Because plymouth/Kms don't support proprietary nvidia drivers... The devs for plymouth/kms will have to work something out with the Nvidia devs to add support for plymouth/kms in their driver... which will probably happen, but who knows when... could be months away or more....

---

### Post by JPorter on 2010-06-17
> **symon1980 said:**
> There won't be an official update to fix this problem... Because plymouth/Kms don't support proprietary nvidia drivers... The devs for plymouth/kms will have to work something out with the Nvidia devs to add support for plymouth/kms in their driver... which will probably happen, but who knows when... could be months away or more....

The problem is that the nvidia proprietary drivers don't have a framebuffer driver for fbdev.  They need one in order to have fully native graphical boot and terminal, as well as seamless handover to X.

This is unrelated to KMS. KMS typically has native framebuffer support as a side effect, but the real reason KMS is a "big deal" is because of the major permissions changes that it enables, i.e. running X entirely in userspace rather than as root.  That's a big deal and really has nothing to do with what the output to screen looks like.

---

