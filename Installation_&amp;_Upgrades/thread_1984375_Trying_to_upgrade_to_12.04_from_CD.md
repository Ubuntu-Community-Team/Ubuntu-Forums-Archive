---
title: "Trying to upgrade to 12.04 from CD"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by willdogs4286 on 2012-05-21
I found out that my sources.list is corrupt when trying to upgrade from 11.04 to 11.10. I get the same error messages when trying to upgrade to 12.04.

I have created a burn disc with the latest version, but my computer will not boot from the disk. I've tried upgrading using every means available except a clean install.

My question is how do I format my hard drive and reboot using the boot disk to install 12.04?

I am currently using Ubuntu 11.04. My hard drive is not big enough to partition. I've tried several suggestions to repair my sources.list. I have tried the update manager as well as the terminal to do updates and upgrades. Because of my repositories problem I am unable to update, upgrade, or install anything.

---

### Post by wilee-nilee on 2012-05-21
> **willdogs4286 said:**
> I found out that my sources.list is corrupt when trying to upgrade from 11.04 to 11.10. I get the same error messages when trying to upgrade to 12.04.

I have created a burn disc with the latest version, but my computer will not boot from the disk. I've tried upgrading using every means available except a clean install.

My question is how do I format my hard drive and reboot using the boot disk to install 12.04?


I am currently using Ubuntu 11.04. My hard drive is not big enough to partition. I've tried several suggestions to repair my sources.list. I have tried the update manager as well as the terminal to do updates and upgrades. Because of my repositories problem I am unable to update, upgrade, or install anything.

If you do not have what you need backed up stop, get another HD and back it it before proceeding, plain and simple. ;)


Don't let what you think you want proceed good decisions, what you are running is still being supported.

---

### Post by willdogs4286 on 2012-05-21
> **wilee-nilee said:**
> If you do not have what you need backed up stop, get another HD and back it it before proceeding, plain and simple. ;)


Don't let what you think you want proceed good decisions, what you are running is still being supported.

I cannot even update software without it giving me the same error message. I already have what really matters to me backed up to my external drive.

---

### Post by wilee-nilee on 2012-05-21
> **willdogs4286 said:**
> I cannot even update software without it giving me the same error message. I already have what really matters to me backed up to my external drive.

If you have what you need backed up I would do a fresh install, that is what I always do. 

You can save all the installed programs and reload them with this in a fresh install, with the dpkg commands. 

Be sure to have all the PPA's saved form /etc/apt/sources.list.d and /etc/apt/sources.list making sure they are applicable to the new install, and you have any keys needed.

Code:
dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:
dpkg --set-selections < installed-software

followed by
Code:
dselect

If you get a missing key error run this on each one.
                                   [FONT=Verdana, sans-serif][SIZE=1]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys missing key here

Post all the errors messages as well that might get us closer if you are set on a upgrade all the text including the commands that generate them.
[/SIZE][/FONT]

---

### Post by wilee-nilee on 2012-05-21
I will add this screenshot of deselect you can just open it with sudo deselect, and if you have the first command run to save the installed Apps, hit install.

Make sure though that you have loaded all repos and keys, and run sudo apt-get update to make sure you are clear for a reload.

[ATTACH]218439[/ATTACH]

---

### Post by willdogs4286 on 2012-05-21
> **wilee-nilee said:**
> Be sure to have all the PPA's saved form /etc/apt/sources.list.d and /etc/apt/sources.list making sure they are applicable to the new install, and you have any keys needed.[/SIZE][/FONT]

This is what is corrupted on my computer. I get an error message saying that it cannot retrieve the code or its the wrong code. I have rewritten them, I have tried reinstalling them, and I have tried a fresh install. Everytime it gives me the same message. That is why I need to completely format the drive and install a stable version.

---

### Post by wilee-nilee on 2012-05-21
> **willdogs4286 said:**
> This is what is corrupted on my computer. I get an error message saying that it cannot retrieve the code or its the wrong code. I have rewritten them, I have tried reinstalling them, and I have tried a fresh install. Everytime it gives me the same message. That is why I need to completely format the drive and install a stable version.

So actually posting what you're mentioning (referring to) and all the code to generate the errors and the errors is needed, we can't guess.

Here is a source list generator if it helps.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

