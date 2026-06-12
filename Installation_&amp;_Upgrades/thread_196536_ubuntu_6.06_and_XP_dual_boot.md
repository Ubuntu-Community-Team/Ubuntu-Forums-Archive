---
title: "ubuntu 6.06 and XP dual boot"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by GuyIncognito on 2006-06-14
I am new to linux and I am trying to create a dual boot of XP and and ubuntu on my 80 gig sata drive. I first made a 30 gig NTFS partition and installed XP. I then created an Ext 3 partition and a 2 gig linux swap partition and installed ubuntu. however when my systems boots it boots straight into windows. Anyone able to give me a step by step guide how I can get this to work? I don't mind reinstalling or repartitioning my hardrive if it makes it easier. thanks.

GuyIncognito

---

### Post by Rui Pais on 2006-06-14
Hi,
either you forget install grub or grub didn't install correctly on MBR of your HD.
See:
[https://wiki.ubuntu.com/GrubHowto]("https://wiki.ubuntu.com/GrubHowto")

or if you really install grub check:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub")

good luck

---

### Post by murph2481 on 2006-06-14
How much memory do you have if its over 256MB I wouldn't worry about the SWAP partition.

Have you installed ubuntu yet?  When you install it, it asks if you want to install GRUB and you do and make sure you install it to the MBR (master boot record)

---

### Post by GuyIncognito on 2006-06-14
[QUOTE=murph2481]How much memory do you have if its over 256MB I wouldn't worry about the SWAP partition.

Have you installed ubuntu yet?  When you install it, it asks if you want to install GRUB and you do and make sure you install it to the MBR (master boot record)[/QUOTE]

I have 1 gig of memory. you think i can get rid of my swap? when i installed ubuntu off the desktop cd it never asked me to install grub. am i doing something wrong? I clicked on the icon on the desktop to install ubuntu. I followed the questions about keyboard layout and time. then it asks which partition to load on. i say the ext 3 partition. and then it loads. nothing about grub. Is there a better way to install?

---

### Post by murph2481 on 2006-06-14
Yea personally I would drop the SWAP in your case.  When I installed ubuntu I used the alternate (text based) installer and had no problems and it asks all the GRUB install questions.

Try installing grub from synaptic in ubuntu and see what happens

---

### Post by GuyIncognito on 2006-06-14
[QUOTE=murph2481]Yea personally I would drop the SWAP in your case.  When I installed ubuntu I used the alternate (text based) installer and had no problems and it asks all the GRUB install questions.

Try installing grub from synaptic in ubuntu and see what happens[/QUOTE]

I prefer the text based installer but couldn't figure out how to get to it on the desktop cd. how do you? and what is synaptic?

---

### Post by Rui Pais on 2006-06-14
Hi,
synaptic is a GUI for apt, the program that generally is used by debian based distro to install and maintain application packages. 
You can use it if you are at Ubuntu, but since you problem seems to be not be able to access your ubuntu installation don't seem much relevant at this point ;)

If i was you i would keep the swap. It will not be used if not need it but may became handy at very high load peeks of computar usage and its necessary if you want to use confortable features like suspend-to-disk. 
Just make it smaller if you dont want to waste disc space.

About install grub, do you read the link to the HowTo on my previous post?

---

### Post by Herman on 2006-06-14
Hello everyone,
If you want to see a good website for showing how to use the 'desktop' installation cd, go to this one by Aysiu, [I][Click Here]("http://www.psychocats.net/ubuntu/windowstoubuntu.html").
[/I]If you want to see a website with illustrations of the 'alternate' CD installer in use, [*Click Here.*]("http://users.bigpond.net.au/hermanzone/")
Those two websites also contian a lot of other information about dual booting and other basic stuff that can help people who are new to Ubuntu.

If GRUB will not install to your MBR, check your BIOS settings for some kind of lock on your MBR or boot sector anti-virus and turn that off temporarily. Something like that could be stopping your MBR from being able to be written to by GRUB.

Welcome to Ubuntu and I hope you like it as much as everyone else!
Regards, Herman :D

Edit: A few people with sata drives seem to be unable to install GRUB to MBR, I don't know why. If you have too much trouble, try booting with [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") instead. Try with GRUB on your Ubuntu partition maybe. GAG should be able to boot GRUB, and GRUB will boot Ubuntu that way. I use Lilo on my Ubuntu partition and GRUB in my MBR, so I can use either GRUB or GAG+Lilo to boot with.

---

### Post by GuyIncognito on 2006-06-15
XP broke my grub! I had it working briefly. I installed from the alternate install cd and it worked great. Grub menu loaded. I started up ubuntu and updated, and rebooted again. Finally shut that down and loaded XP. Now my grub menu is gone! now it boots straight into XP again. I tried reinstalling grub with alternate cd rescue with no luck. Should my XP partition and Linux partition be flagged as bootable or not? When Xp was flagged as bootable but Linux wasn't grub didn't work. but then when I flagged them both as not bootable it worked. Should I flag them both as bootable? I'm at a lose here. thanks.

---

### Post by Rui Pais on 2006-06-15
hi, 
you should make bootable only the linux partition that contains grub.
There must be some lines in your /boot/grub/menu.lst like this one:
> title Windows
        rootnoverify (hd0,0)
        chainloader +1
The last line will "pass" the boot to the loader of Windows, so it won't be mad with you from not being bootable flaged ;)

Note that (hd0,0) is if you have Windows at 1st partition of 1st HD. 
(hd0,1) is 2nd partition of 1st hd, (hd1,0) is 1st partition of 2nd hd, and so on... you got the idea.

---

### Post by Herman on 2006-06-15
> Should my XP partition and Linux partition be flagged as bootable or not? When Xp was flagged as bootable but Linux wasn't grub didn't work. but then when I flagged them both as not bootable it worked. Should I flag them both as bootable?Personally, I don't think the boot flag is important. I agree with 'lcg' in the following thread. [http://www.ubuntuforums.org/showthread.php?t=186783&highlight=boot+flags]("http://www.ubuntuforums.org/showthread.php?t=186783&highlight=boot+flags")
You can try toggling the boot flag around if you want though, it won't hurt anything, I just don't think it will make any difference. Let me know if it does and I'll have to apologise.
> I am trying to create a dual boot of XP and and ubuntu on my 80 gig sata drive.Has your computer got any more hard drives in it, or is this the only one? 

Can you re-install Grub to MBR again as per one of the methods in the links Rui Pais gave you in the second post of this thread?

It is encouraging that you were able to install GRUB and have it working until you booted Windows XP. I am still thinking along the lines of some program that might be trying to 'protect' your MBR.  I  wonder if there might be some program you have in Windows XP that could be doing that now?
For example, after reading this: [http://www.f-secure.com/v-descs/boovirus.shtml]("http://www.f-secure.com/v-descs/boovirus.shtml")
it wouldn't be difficult to imagine that if a boot sector vuirs can write code to your MBR from your memory each time your computer is restarted, why can't an antivirus software act like a virus and do the same thing, but restore your MBR instead? 
 Maybe try looking for some program like that and turning it off temporarily. Most people with Windows need to load it to the gunwales with all kinds of defence softwares. Perhaps one of those can be working with your computer's BIOS to cause your MBR to behave like this.

I remember when I used to use Windows and had to constantly be updating all those types of programs and running scans with them all the time. They always used to come up with loads of trash to be deleted from Windows. Then as soon as I began using Ubuntu for all my internet and e-mail work, (and kept Windows off the internet), those programs no longer found any bad programs in Windows anymore at all, every scan came up clean.
Now I use Ubuntu for everything and have no need to waste my time with all those silly rituals that Windows people have to go through. You should still keep those programs in Windows, but try disabling them all for now and try re-installing GRUB, just keep WIndows off the internet while those things are turned off, and remember to turn them back on again before going on-line with Windows. Also, check your BIOS setting again to make sure nothing in your BIOS has been reset to block your MBR from being written to, like . I hope that will help

---

