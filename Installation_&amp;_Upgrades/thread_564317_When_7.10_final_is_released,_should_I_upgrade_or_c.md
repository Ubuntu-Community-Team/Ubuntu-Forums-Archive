---
title: "When 7.10 final is released, should I upgrade or clean reinstall"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by Codename46 on 2007-10-01
Hey guys,

When the final version of Gusty Gibbon is released, should I just download and burn another CD and re-install from scratch or should I upgrade? Would there be any significant disadvantages of just upgrading? Will I experience any problems as far as settings, and would programs like Compiz and Gnome screw up?

Thanks.

---

### Post by RebounD11 on 2007-10-01
Safer to clean install. At least that's what I think and what I'm gonna do :D

---

### Post by Codename46 on 2007-10-01
> **RebounD11 said:**
> Safer to clean install. At least that's what I think and what I'm gonna do :D

Ugh. I don't want to sound like a lazy bum but I am not inclined to spend 4 hours re-installing all my programs, copying over files I backed up, and reconfiguring Compiz/Gnome/Themes/etc.

ETA: Have any of you guys just upgraded from previous releases? Did you guys have any problems?

---

### Post by rsambuca on 2007-10-01
Either way you should  back up your data, so there is no harm in upgrading first.  If you have just stuck to the standard ubuntu repositories, then it is likely your upgrade will work.  If you have added external repositories, installed programs from outside the repositories, and/or used things like Automatix, your chances of a smooth upgrade decrease.

---

### Post by Codename46 on 2007-10-01
> **rsambuca said:**
> Either way you should  back up your data, so there is no harm in upgrading first.  If you have just stuck to the standard ubuntu repositories, then it is likely your upgrade will work.  If you have added external repositories, installed programs from outside the repositories, and/or used things like Automatix, your chances of a smooth upgrade decrease.

Noob question: Does the universe/multiverse repositories count as "standard ubuntu repositories"?

I think the only thing I installed manually was Pidgin because it was not in the repository along with some third-party Gnome themes. I'll probably uninstall it because AFAIK it'll come with 7.10.

Which brings up another question: Should I uninstall Pidgin before upgrading?

Also, another question: The new Gnome release will be in 7.10 along with another version of Compiz, correct? Does that mean my Gnome settings will get screwy?

Thanks for the help so far guys

---

### Post by dimbulb1024 on 2007-10-01
I'm going to upgrade. I have my Home folder on a separate partition, which is always backed up. I did a clean install with 7.04 and even though I used the same user name and password I had to change permissions on my home folder, a pain.

Any repositories you loaded from inside Synaptic Package Manager, which includes universe and multi, I would think would not affect an upgrade.

I would think your Gnome settings should stay just the way you have them if you upgrade. I am not sure why they wouldn't.

I not sure about the Pidgin question.

---

### Post by megamania on 2007-10-06
> **Codename46 said:**
> When the final version of Gusty Gibbon is released, should I just download and burn another CD and re-install from scratch or should I upgrade?
When 7.04 came out, I upgraded from 6.10 to 7.04 with no problems. Now I upgraded the same system from 7.04 to 7.10beta successfully. 

My setup is pretty straightforward though (gnome + synaptic applications + virtualbox)

---

### Post by cuby on 2007-10-07
I've upgraded in the last 2 releases. But my current installation is new... I had a hardware problem a couple of months ago. 
I never experienced problems in upgrades, so, I'm going to do it.

Of course, I'm going to backup important data, as usual...

---

### Post by leopards on 2007-10-12
I listened to some bad avice when I first started using Ubuntu and installed a lot of stuff with Automatix!! Is there anyway to uninstall all the stuff in a way that would let me do an upgrade? If not, after the clean install of 7.10 how do I move all my saved e-mail and stuff back off the external USB drive were it is backed up into my home folder again without messing up the new install?? As you can see I am a noob at linux! when it comes to CLI I have to just about cut and paste!!

---

### Post by imaca on 2007-10-12
Hi - just upgraded my kids PC to gutsy RC.
Make sure you back up your old xorg config. Gutsy tries to auto configure it and in my
case made a total mess.
Failed to detect my radeon 9800 and also the ADI PD965  monitor - ended up with vesa driver and 640x480.
This is the worst result of any version of Ubuntu I have installed.
Previous versions have at least installed the ATI driver and given me 1024x768, the restricted driver manager in Fiesty installed fglrx without a hitch.
I think I'll be waiting quite a while before installing Gutsy on my PC.

---

### Post by nowhere@cox.net on 2007-10-12
Ummmm,

I made the switch to Ubuntu because I heard debian distro upgrades were sooo much more smooth than Red hat based distro upgrades. 

I have in the past upgraded from FC1 to FC3, FC3 to FC4, FC4 to FC5 and tried FC5 to FC7. Every one of them broke so many packages and I spent more time debugging it all that it would have to clean install and try to remember all the things I had to fix that didn't work when I installed clean.  With the FC5 to 7 debacle I decided to install clean with Ubuntu with the hopes of a smoother ride. The clean install of 7.04 did not go well so I expect to have problems with the upgrade as well...


Eric

---

### Post by Axed on 2007-10-12
I upgraded from Dapper to Edgy to Feisty with few issues, but decided to reinstall Feisty when I changed hard drives from a 120 to a 250 as it was getting pretty messy from all my tinkering.

Just upgraded from Feisty to Gutsy RC with little drama, so I'd recommend at least trying the upgrade. Just have the CD handy so you can reinstall if the upgrade is a disaster. ;)

I think I'll be reinstalling again when 8.04 comes out as it should be time to move to 64-bit by then (it's already quite viable but x86 is still a safer bet).

---

### Post by mhenry676 on 2007-10-15
Well, as for 32 vs 64, check this out: [http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)

I've tried opensuse 10.2, 10.3, kubuntu 64 and fedora 7 64. All get tricky with plugins for firefox, but I do have to say that this has only been over the last two months when I entered 64bit capability. 

Even in the windows world (for me=gaming/work) 64 bit gives no noticeable increase. Actually sometimes more headache as some games use copy-protection that is not 64bit compatible. You'll have to use a CD crack; whether or not it's legal cause you own the game, I don't know. But hey, I had to when I got Quake3, cause after opening my brand new, SEALED store bought copy, I was greeted with a message saying my key was in use! (Store policy was for the customer to deal with the manufacturer, I had it pre-ordered/waited for months-NO WAY!)

As for the upgrade, give it a go: But first, as any upgrade tells you BACKUP! But this is Linux, not Windows. You should be able to get a list of you installed packages, and use that to create a script to replace the repositories with the new ones for gutsy, and install all those packages in one swoop! I always keep track of packages I have to download separately or compile. And always keep backups of /etc/X11/xorg.conf! Use a flash drive for this! They are so cheap, I waiting for them in cereal boxes! 

:guitar:

---

### Post by Cochise on 2007-10-15
im fresh installing anyway........

---

