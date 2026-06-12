---
title: "Upgrade from 10.04 to 10.10"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Vepar on 2010-12-21
I'm running Ubuntu 10.04,

lsb_release -a

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid
```uname -a

```
Linux vepar-desktop 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
```and i want to upgrade.

So i did a google search and found [this]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") and [this]("https://help.ubuntu.com/community/MaverickUpgrades"), but after i updated the system, it says to press "Check" again, and i should be prompted that there's a new release, but nothing happens, just says my system is up to date... 

So, is it? Btw, lsb_release -a, and uname -a were done after the update, so idk, it says 10.04 still... 

Also, is it a smart thing to want to upgrade now? I've seen some posts here in the forum that the 10.10 messed up their dual boot, and since i dual boot too, i'd rather it didn't mess it up, although from reading the threads, i think they did a fresh install. Since i allready have grub set up, upgrading shouldn't hurt my dual boot right? Should i upgrade to 10.10 or just leave it like this?

---

### Post by theasprint on 2010-12-21
Hi,

Er, if you're dual-booting, I recommend you should not upgrade (especially if you're using Wubi install)

But I believe that if you want to upgrade, then you can, but you would need to reinstall your grub again, and also to update your grub using ```
sudo update-grub
```

For now, I believe sooner or later there will be one expert to come tell you.

Good Luck :D

---

### Post by Vepar on 2010-12-21
Well i'm not using WUBI, i downloaded the Live CD and installed from that...

---

### Post by Jonners59 on 2010-12-21
> **theasprint said:**
> Hi,

Er, if you're dual-booting, I recommend you should not upgrade (especially if you're using Wubi install)

But I believe that if you want to upgrade, then you can, but you would need to reinstall your grub again, and also to update your grub using ```
sudo update-grub
```For now, I believe sooner or later there will be one expert to come tell you.

Good Luck :D

I do not agree with this.  I run a number of machines including mobiles (yes, Ubuntu on a mobile phone, it's just like the desktop) , all now on Ubuntu, all dual boot, and whilst I have some issues, they tend always to be the same machines and tend to be those running with nVidea cards.  Others never have a problem with upgrades of which I have been through 4 major on 9 machines so far.

To upgrade, I suggest ordering the CD from the Ubuntu home page.  Others prefer to download and burn their own.  I am not a techie and get stuck easily, so for me this is the best option.

Wibi is not a long term install and should, ideally be removed when moving to a proper, full install, after copying the HOME directory to somewhere safe should you want to keep files and docs.

I tend to create 3 partitions, plus a SWAP space of c5Gb.  1 is the Windows OS, which I use the Windows Manage Storage to size if required, then from within Ubuntu I use Gparted to create the others, 1 for the current Ubuntu install and another for the next upgrade.

I like to have the spare partition because I use it to install the new install too, and it then allows me to set it up safely over as much time as I like.  Once done, I can then install the next version of Ubuntu over the old partition and so on.

Then insert the CD in the machine.  Re boot, and follow the instructions.  I always over-ride the dual boot setup offer, and choose my own partition to create the new install.  The rest should be plain sailing.

Yes, it is a good idea to run sudo update-grub, but not essential.  Grub is not Ubuntu either an dthe update is included in the install.

Also suggest installing Ubuntu Tweaks - great for "tweaking" your install.  You can also use it to move directories and even you boot up image.

Hope this helps.

---

### Post by Vepar on 2010-12-21
Thank you for the reply, but you're saying i should update from a CD, and i've been trying to avoid that since it means i have to download it, burn it, and reinstall the system again (more or less, even updating from CD tends to be problematic), so i wanted to upgrade within the OS if it's possible, and according to ubuntu help, it should be, but somehow i'm not getting the upgrade option.

---

### Post by oldos2er on 2010-12-21
Check System, Administration, Software Sources, Updates tab, under Release upgrade check it's marked as 'Normal releases' and not 'Long term support releases only'. Run ```
update-manager -d
```

---

### Post by Jonners59 on 2010-12-21
> **Vepar said:**
> Thank you for the reply, but you're saying i should update from a CD, and i've been trying to avoid that since it means i have to download it, burn it, and reinstall the system again (more or less, even updating from CD tends to be problematic), so i wanted to upgrade within the OS if it's possible, and according to ubuntu help, it should be, but somehow i'm not getting the upgrade option.

Sorry, I must have not been clear...

No, what I suggested is ordering the CD on-line.  I do this for the same reasons you mentioned.  I'm not techie and I am more likely to make some mistake if I do it.

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

So, yes, you can upgrade from the Update Manager, but, only, from my limited experience, if it has the [COLOR=Red]*update option[/COLOR], and even then it does not always work - I won't go in to my experiences.  The update does not always appear.  Of all my 10 machines it has only appeared on one.

So, you can download the iso and burn on to a CD - yuk

Or order it.  It takes a few weeks, but the point is that once you have it is easy to use, is as good as it gets - and - if anything goes wrong at any time, it is so very useful....


[COLOR=Red]*When an update to a new version such as 9.04 to 9.10 to 10.04 to 10.10 is released, then sometimes on some machines the option appears at the top of the Update Manager as an option.[/COLOR]

I have just upgraded three machines, one has a problem which I am raising on a thread, the others were easy.  I also have oe in the Update Manager that the install fails every time.  I shall do from CD later.

---

### Post by ottosykora on 2010-12-21
>Of all my 10 machines it has only appeared on one.<

well you have to enable it in the packet sources, if you do not enable it will not be shown. If you enable it, it will be shown definitey as soon as the release is definitiv.

---

### Post by Jonners59 on 2010-12-21
> **ottosykora said:**
> >Of all my 10 machines it has only appeared on one.<

well you have to enable it in the packet sources, if you do not enable it will not be shown. If you enable it, it will be shown definitey as soon as the release is definitiv.

Ah, many thanks....

Where is it exactly, please?

My experience of upgrading this way has only been one of horrors, but it is always good to have the option.

---

### Post by Vepar on 2010-12-22
> **oldos2er said:**
> Check System, Administration, Software Sources, Updates tab, under Release upgrade check it's marked as 'Normal releases' and not 'Long term support releases only'. Run ```
update-manager -d
```


Yes, that worked, thank you very much!
After i typed this in the terminal i could see the Upgrade button.

@Jonners59:

You were clear, i just thought this net upgrade was a bit easier than ordering a CD then waiting a week etc... Anyway, i did the net upgrade, and as far as i can tell, everything is allright...


lsb_release -a
```

Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
```uname -a

```
Linux vepar-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```So i guess the problem i was having is solved! Thank you!

---

