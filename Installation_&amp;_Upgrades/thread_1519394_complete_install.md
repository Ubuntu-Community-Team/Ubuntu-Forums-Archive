---
title: "complete install?"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by EvoFX on 2010-06-28
i am looking at doing a complete install of Ubuntu. my current computer is a windows xp and has a few viruses and is running slow from that. i was wondering if doing a wipe clean with ubuntu would kill the viruses? i am not interested in keeping xp, so ubuntu would be the new OS.

after some reading, i came across some stuff saying do not install the desktop right away but install the server then the desktop?


and i would be installing this from a jump drive

---

### Post by howefield on 2010-06-28
> **EvoFX said:**
> i was wondering if doing a wipe clean with ubuntu would kill the viruses?

Installing Ubuntu over your partitions would get rid of the virus. I know you said you aren't interested in keeping XP, but you can install anti virus onto your jump drive install of Ubuntu and clean the windows.

> after some reading, i came across some stuff saying do not install the desktop right away but install the server then the desktop?

If you are going to be running a desktop you'd be better with the desktop edition. If you want some server applications, they can be installed as required. There used to be a case for installing the server edition  to get the PAE kernel if it was needed to address a lot of RAM, but I think the 32 bit edition of 10.04 will automatically install the PAE kernel if it detects more than 4 gig of RAM, so if you are not looking for a server, I can't think of a reason to install it, and then the GUI,.


> and i would be installing this from a jump drive

No problems with that, good luck.

---

### Post by EvoFX on 2010-06-28
ok sweet, 

what i was refering to was the site for unbuntu help and it had this
[B]
Warning: Ubuntu Desktop edition installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which allows very little customization). DO NOT USE the Lucid Lynx Desktop edition if you use a boot partition, use multiple OS (more than 2), or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it manually. This is a serious flaw in both Karmic Koala and Lucid Lynx. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).
GRUB2 has caused major problems in installation -- be sure to research the issue before upgrading to Lucid Lynx
[/B]

so thats what i was wondering about.

also i posted this on another forum i have used before i found this. 

and they were saying to get a virus scanner, what are some for ubuntu? becuase when i use windows the virus wont let me open any of the scanners, or spybot or adware. so i pretty limited on what i could do. so thats why i would want to do a full system wipe and just use a linux based program

---

### Post by howefield on 2010-06-28
> **EvoFX said:**
> so thats what i was wondering about.

It is only a problem if you have other Operating Systems on your computer, that won't be the case for you., so you can ignore.

> and they were saying to get a virus scanner, what are some for ubuntu?

Most of the anti virus companies have Linux versions. There are some free ones, like Avast, AVG, Bitdefender for Unices, ect, there is also clam anti virus which you can install with the software manager, Synaptic Package Manager.

There are also commercial products if you want to part with some pennies.

> becuase when i use windows the virus wont let me open any of the scanners, or spybot or adware. so i pretty limited on what i could do. so thats why i would want to do a full system wipe and just use a linux based program

If you create a bootable USB disk with Ubuntu (could be pretty much any Linux distribution) with persistence, you can boot and use the USB as if it were a hard disk.

In other words, you can install Anti Virus to your Ubuntu flash stick and boot the computer with it. Then use the anti virus application to scan your hard disk, the virus can't stop it because you aren't using the hard disk/operating system on which it resides. Hope that makes sense.

There is a free download from AVG that will create a bootable CD (don't know if you can use a flash stick) that you can boot from into an environment where you can run AVG and clean your hard disk. Again, your hard disk isn't being "used" so the virus is powerless to prevent it working in the way it does whilst booted into Windows.

---

### Post by EvoFX on 2010-06-28
hmmm, ok i understand the bootable usb stick. thing, sounds like something i could do. 

so do you think its just worth having a dual operating system (windows and ubuntu together) 

or 

do you think i should choose the option of wiping the entire disk (i am assuming it would get ride of most of the viruses, if not all of them doing that?)

---

### Post by howefield on 2010-06-29
> **EvoFX said:**
> so do you think its just worth having a dual operating system (windows and ubuntu together)

Only you can answer that one, you either need windows or you don't. The fact you are asking suggests you might not know yet whether Ubuntu is  for you, or at least have a learning curve to climb, and in that case it might be worth having a windows install if you need to use it.

<Shrug>  

> do you think i should choose the option of wiping the entire disk (i am assuming it would get ride of most of the viruses, if not all of them doing that?)

That's what I would do, but then I don't need windows for anything. (Wiping the disk will rid you of any malware issues)

---

### Post by EvoFX on 2010-07-10
ok so i am looking to do a complete reinstall. deleting windows and all that. i just remembered that i have a old wireless adapter on the back. and i remember i had to install it through a cd for it to work. when deleting the windows side i guess that it will delet that program for the wireless to work. or does ubuntu have a way for me to connect to my wireless with my adapter. (i am not sure if i have the cd still, but ill have to check when i return home)

---

### Post by C.S.Cameron on 2010-07-10
Now days Ubuntu is pretty good at installing hardware out of the box.
I have not needed any other drivers for wireless adapters in years.

---

