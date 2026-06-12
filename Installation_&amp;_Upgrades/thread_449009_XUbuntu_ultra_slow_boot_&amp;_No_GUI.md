---
title: "X/Ubuntu ultra slow boot &amp; No GUI"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by JonMidhir on 2007-05-19
Hi Guys,

I'm fairly struggling with getting Xubuntu to work on my old laptop. The specs:

Pentium II 
128MB RAM
4Gig HD

The BIOS is locked so I can't boot from CD. In turn I've extracted the hard drive and used my main PC to boot into the Xubuntu live CD and install the OS on the laptop hard drive using an external box. By editing the GRUB loader in the laptop I can start the boot process no problem, but it's extremely slow both for Xubuntu and Ubuntu.

It takes about 40 minutes to boot up to a shell, not even the GUI! It hangs mainly on 'Preparing Restricted Drivers' and then takes ages to go through the rest of the process.

I can't figure out what is going wrong! I really think there shouldn't be a problem running Xubuntu despite the limited resources.

Anyone have any clues to what might be causing the problem? I'm very new to Linux but really itching to get started in that environment.

Thanks,

Jon

---

### Post by southernman on 2007-05-20
> Anyone have any clues to what might be causing the problem?You can't install any OS on one machine and move the hdd to another machine, expecting it to work. Well, you could if the two machines are an identical match... hardware for hardware.

What brand of laptop do you have, that you say the BIOS is locked?

---

### Post by Matty2006 on 2007-05-20
> **southernman said:**
> You can't install any OS on one machine and move the hdd to another machine, expecting it to work. Well, you could if the two machines are an identical match... hardware for hardware.

What brand of laptop do you have, that you say the BIOS is locked?

ya, what he said!!
There is a way to reset the BIOS. On Desktop mainboards there is a jumper that can be located near where the BIOS is mounted. The process usually involves moving the jumper to the opposite position on the three pins and waiting up to 2 minutes. then moving it back to where it was. After this the bios settings are reverted to factory default. 

I can not say that I have done this on a laptop, but I am pretty sure its the same.
Now on laptops this can be a lot more tricky mainly because laptops are not all that friendly at coming apart. Puting them back together can be equally tricky. If any of the inside ribbons are damaged, it may not be possible to get a new one. I would be very very careful at attempting this or have a pro do it. 

There is also a way to boot off USB using Knoopix but this does not accomplish what you want.

Good luck

---

### Post by JonMidhir on 2007-05-20
> What brand of laptop do you have, that you say the BIOS is locked?

It's a Dell laptop, an older latitude model. It was used by an old employer and was locked for understandable reasons, so I replaced the HD but there is no option to edit the boot order at startup, just F2 to enter setup which isn't editable.

The replacement HD came with WinXP which didn't boot anyways so I wiped and repartitioned it.

Would there be any way to boot up the Xubuntu live CD from GRUB? If I could get that far I could reinstall the OS on the laptop itself?

Good to know I can't do it using the external box, at least I'm not barking up the wrong tree now.

Thanks for the help so far!

---

### Post by einsteinisgaurav on 2007-05-20
u cant run tht wid 128mb's of ram

---

### Post by einsteinisgaurav on 2007-05-20
my 256 mb ram and PIV couldnt do tht

---

### Post by JonMidhir on 2007-05-20
Yes you can, I have friends doing so.

---

### Post by southernman on 2007-05-20
> **einsteinisgaurav said:**
> u cant run tht wid 128mb's of ram
Just last night, installed xubuntu drapper on a compaq presario with 64mb ram and 4.3gb hdd...

On to the problem at hand. Have a look at [Installing without a CD]("https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd").

IF after reading all that, it's still clear as mud... search the forums for install from hard drive.

Will check back later on, after have several cups of coffee.

---

### Post by JonMidhir on 2007-05-20
I can boot into recovery mode (although it takes a long time), so I'm currently partitioning the drive and copying the install cd over to the hard drive to try and install it from there as it descibes on that page you listed!

So I'll also be back in a few cups of coffee!

---

### Post by JonMidhir on 2007-05-21
I was just thinking...


I can boot into a bash prompt from which I can mount the cdrom drive...


Is there some way I could install Xubuntu from this prompt?? I have both the Desktop CD and the Alternative Install CD.

Thanks,

Jon

---

