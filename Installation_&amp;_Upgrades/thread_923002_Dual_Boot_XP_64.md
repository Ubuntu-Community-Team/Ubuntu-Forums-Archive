---
title: "Dual Boot XP 64?"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by bhart007 on 2008-09-17
Ok I know this is a noob question.. it's just that I've never bothered with Dual booting.  Ok Does Windows have to be installed first or can you throw it on an already running Ubuntu machine?

Also would 64-bit make any difference to the linux side?

Thanks!

---

### Post by overdrank on 2008-09-17
> **bhart007 said:**
> Ok I know this is a noob question.. it's just that I've never bothered with Dual booting.  Ok Does Windows have to be installed first or can you throw it on an already running Ubuntu machine?

Also would 64-bit make any difference to the linux side?

Thanks!

Hi and you can install windows after Ubuntu and this link can help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
As for installing 64 bit it should make no difference to the already installed OS.

---

### Post by iaculallad on 2008-09-17
It's a good idea to install your windoze OS first before installing Ubuntu, doing this will automatically include windoze in your GRUB menu list startup boot option. 
There will be no difference when dual booting both windoze 64-bit and an Ubuntu 32-bit version as they're two different entity.

---

### Post by ronbie_68 on 2008-09-17
I too am a newbie to Ubuntu. In fact i am a newbie to Linux period. I have vista Ultimate 32 bit on a 64 bit dual core and with the Live Cd install for the (hardy) flavor it installed like a dream. 

Ive read many, many forums before installing Ubuntu and if you just google a lot and read what you're looking for from multiple people that know what their talking about, I don't see you having any issue installing next to 64 bit xp. Make sure not to pre-partion your HD. Its much easier to let gparted do it during the install. It will even automatically account for swap partion during install and allow you to shrink your windows partition. Also make sure to backup important files on you HD first. You never know what can happen. 

Kudos to the people working on this (Ubuntu) project as you have made easy enough even for the most novice of users to install and use. Now we have a choice.

---

### Post by bhart007 on 2008-09-17
Ahh ok I think I see it now.  By installing windows after ubuntu.. it will overwrite the MBR.  Following the link from Overdrank, I should use those instructions to "rebuild" the MBR and Grub to include both ubuntu and winblows?

---

### Post by overdrank on 2008-09-17
> **bhart007 said:**
> Ahh ok I think I see it now.  By installing windows after ubuntu.. it will overwrite the MBR.  Following the link from Overdrank, I should use those instructions to "rebuild" the MBR and Grub to include both ubuntu and winblows?

Hi and yes, have you consider just using windows in virtual machine within Ubuntu?

---

### Post by iaculallad on 2008-09-17
> **overdrank said:**
> Hi and yes, have you consider just using windows in virtual machine within Ubuntu?

That would be a good choice, doing just a VM within Ubuntu :)

---

### Post by ronbie_68 on 2008-09-18
> **iaculallad said:**
> It's a good idea to install your windoze OS first before installing Ubuntu, doing this will automatically include windoze in your GRUB menu list startup boot option. 
There will be no difference when dual booting both windoze 64-bit and an Ubuntu 32-bit version as they're two different entity.
I agree. Based on the other forums i've read you are better off installing with windows already installed. Unless you're familly with editing Bios settings. I'm not but could afford to play with mine. Using 64 bit should not make a difference.

---

