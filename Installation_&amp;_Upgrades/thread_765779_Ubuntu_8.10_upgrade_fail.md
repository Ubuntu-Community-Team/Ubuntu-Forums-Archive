---
title: "Ubuntu 8.10 upgrade fail"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Pligon on 2008-04-24
I tried upgrading Ubuntu 7.10 to 8.04 through the Update Manager, but when I initiate the upgrade, the Update Manager window stalls and i have to force quit out... the upgrade won't run at all. Any and all help is appreciated, thanks.

---

### Post by a10waveracer on 2008-04-24
Yeah, I'm having the same problems upgrading from my current Gutsy install.  The weird thing is that I'm having that problem while using the alternate CD... I'll keep you updated if I can figure it out... just be aware that the same problem is possible (if not probable) if you're using the alternate CD as well.

[COLOR="Red"]EDIT:[/COLOR]  Yeah, so, just restart.  I got it working by doing that.  Do I feel stupid?  Yeah.  Happens.

---

### Post by nitrokid759 on 2008-04-24
I have the same problem, but restarting doesn't help.

---

### Post by justin whitaker on 2008-04-24
> **Pligon said:**
> I tried upgrading Ubuntu 7.10 to 8.04 through the Update Manager, but when I initiate the upgrade, the Update Manager window stalls and i have to force quit out... the upgrade won't run at all. Any and all help is appreciated, thanks.

Try changing the servers you are connecting to. Under system> adminstration> software sources you can change where the updates are coming from.

---

### Post by nitrokid759 on 2008-04-24
Nope, Still nothing

---

### Post by justin whitaker on 2008-04-24
> **nitrokid759 said:**
> Nope, Still nothing

You can physically change the source list...changing regions until you find one that works....I would just hold off until the servers are a bit less jammed.

---

### Post by nitrokid759 on 2008-04-24
Its just the Update Manager that freezes

---

### Post by Pligon on 2008-04-24
Actually, that may in fact be the issue.  The problem might be caused from the overloaded servers.  If that is the case, then it explains why the Update Manager fails when trying to go through the server to get the Upgrade... I'll keep trying every now and then, and play around with some settings... If I find anything out, I'll post it here.

---

### Post by bsharp on 2008-04-24
Just download the alternate cd (torrent is faster) and upgrade from it.

---

### Post by a10waveracer on 2008-04-24
> **bsharp said:**
> Just download the alternate cd (torrent is faster) and upgrade from it.

I tried that and it doesn't work.  Oh, and I thought restarting earlier worked--it got me farther, but not much.  It still locked up...

---

### Post by ptcbus on 2008-04-24
Use torrents; it is way faster. See [http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/]("http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/")

---

### Post by denham2010 on 2008-04-24
I had similar issues with the updater hanging at various points.

The solution that worked for me was to revert your sources.list back to the defaults, and removing all 3rd party entries and GPG keys. Don't just disable the 3rd party repositories, you need to remove them or it still causes issues.

The updater seems to have issues with 3rd party entries being present in the sources.list file.

To revert back to the default:

Backup your sources.list file first.
Run Software Sources from your menu.
Switch to your 3rd Party tab and delete all entries.
Switch to the GPG tab and delete all entries.
Click the DEFAULT button and save.

The updater will now begin the update without any problems, except for server lag due to everyone updating at the same time.

---

### Post by Ken Jannot on 2008-04-24
When I first tried upgrading, I kept getting the notice, failed to download release notes," and the upgrade never started. Changing the software source from US to Main seems to have fixed the problem--at least, now the upgrade process is underway. It may be slow from the traffic, but it is moving. (So far.)

---

### Post by a10waveracer on 2008-04-25
> **denham2010 said:**
> I had similar issues with the updater hanging at various points.

The solution that worked for me was to revert your sources.list back to the defaults, and removing all 3rd party entries and GPG keys. Don't just disable the 3rd party repositories, you need to remove them or it still causes issues.

The updater seems to have issues with 3rd party entries being present in the sources.list file.

To revert back to the default:

Backup your sources.list file first.
Run Software Sources from your menu.
Switch to your 3rd Party tab and delete all entries.
Switch to the GPG tab and delete all entries.
Click the DEFAULT button and save.

The updater will now begin the update without any problems, except for server lag due to everyone updating at the same time.
Okay, I tried to follow denham's instructions and it doesn't work--I still get stuck on the very first step which, I believe, is either "Reading Cache" or "Loading Cache".  I'm not sure which because it fizzles out before I can actually read it.

---

### Post by ZinkAlkon on 2008-05-25
Quick Question. Ubuntu 7.04 installed now, also I have the Ubuntu 8.10 release 64 bits v CD, (the one I need, I've got an Acer Aspire 5043 w/a Turion 64, plus the Atheros WIFI card) after failing horribly on trying to get my wifi card to work, seems the right choice to update.

Issue #1, got the CD into the CD drive, doesn't start automatically, althought it does recognice it as Ubuntu 8.10, but I can't get anything to actually start it. 
I've tried several things like

gksu "sh /cdrom/cdromupgrade"

also some others I've found on the FAQ's and diff updates issues threads.
None of them seem to work.

Issue #2 It won't boot neither (issue is not the CD, I've got it into diff PC's and boots right away.
maybe I need a special command for the CD to boot from start? I don't have a problem in formatting everything, everything's is backed up.

Issue #3, I can, (actually on the process) upgrade from 7.04 to 7.10, and then take it to the next, so on, up to 8.10) but the issue here is that the servers are really slow, and I'm ONLY downloading the 7.10 now. Seems pretty crazy having the CD, not getting it to work from ground zero, althought I can download the updates and also changed the download sources under System > Administration > Software Sources . It's taking FOREVER (at about 10 kb/s)... u can see the pic.

Would love some advice to get the nice CD to do the job, again, I don't mind getting everything from ground zero.

    Thanks in advance, to all the Ubuntu community!

---

### Post by molotov00 on 2008-05-25
Maybe the GUI appears to lock up but is still working? Tried leaving it?

For upgrades I prefer apt-get. I did this to upgrade my server:

```
sudo apt-get dist-upgrade
```

If it is a GUI problem you are experiencing then a command line approach will work. It's what I would try in your shoes.

M

---

### Post by ZinkAlkon on 2008-05-25
thxs! great advice, althought I did leave the GUI, reboot, etc etc...

I´ve checked the other laptop that I´m updating, and at this point is around 50 kb/s, so I guess an hour or so in the update #980/1054 is not a bad sign. I´ll definitly try the sudo command if the 7.10 to a higher version is giving me trouble.

Just curious, due to the fact that I´m in the noob noob noob stage at linux and ubuntu, would you care on explaining whatactually that command would do and the diff between them?

Thx again!

---

### Post by CTBuckweed on 2008-05-28
I'm having the same problem. I've just installed 8.04 (hardy) on a partition (new install). I get notified of upgrades available; I click to install them and it just stalls. I left it running overnight and it's just sitting there.

---

### Post by agas on 2008-06-03
> **molotov00 said:**
> Maybe the GUI appears to lock up but is still working? Tried leaving it?

For upgrades I prefer apt-get. I did this to upgrade my server:

```
sudo apt-get dist-upgrade
```

If it is a GUI problem you are experiencing then a command line approach will work. It's what I would try in your shoes.

M
I get this...

agas@agas-home:~$ sudo apt-get dist-upgrade
[sudo] password for agas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dpkg-dev fakeroot
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
agas@agas-home:~$

---

### Post by abn91c on 2008-06-03
try dpkg --configure -a
also you may try sudo apt-get check and see if it tells you what to do

---

### Post by migalhasm on 2008-10-30
Hi, i'm running ubuntu 8.10 beta, how do I update to the final release?

Thanks

---

### Post by robertyou on 2008-10-30
> **migalhasm said:**
> Hi, i'm running ubuntu 8.10 beta, how do I update to the final release?

Thanks

You don't need to do a major upgrade. Just make sure everything is updated thru update manager.

---

### Post by Meteo13 on 2008-11-05
My Upgrade from Ubuntu 8.04 (kernel 2.6.24-21-generic)failed aswell. All the files were downloaded by the Updatemanager and right before completing the installation my Inspiron 9300 shuts down. I tried to start the recoverymode (dpgk) for the 2.6.24-21-gen kernel and it seemed to work, but the nvidiagraphic is broken. I tried to use Lowgraphics mode, but it could not pass the screen right after login. It failed to install the Gnome-powermanagement module aswell. I will try to reinstall ubuntu 8.04 later...

Meteo

---

### Post by ElvisGump on 2008-11-06
I used the Update Manager to go from 8.04 to 8.10 which took several hours to download overnight and then went through all it's steps this morning. 

A few times it asked me about the menu.lst file and I don't know if I screwed up in the answers it wanted. I thought letting it keep the current file was the way to go, but now I think that was a mistake because I'm stuck at the grub menu. It still lists the Ubuntu system installed as 8.04 and won't boot, but goes into a shell I guess is what it is -white type on a black screen asking for my login and password after which it expects a command I don't know to give it.

Have I hosed my install or can I edit the grub menu.lst from there? I assume it needs to be told the system installed is 8.10 instead of 8.04 before the grub can access the new OS right? I had to boot back into WinXP. 

I still have a 7.10 Ubuntu partition if that helps me edit the grub menu.lst file from there.

Help!

---

### Post by robertyou on 2008-11-07
My upgrade didn't go well at all, it stuck at a point for hours so I terminated the process and did a clean install.

I wonder if it's better to burn a cd and go through the upgrade option..

---

### Post by nishant_g_shah on 2008-11-15
I you try to upgrade Ubuntu 8.10, and if it fails. It locks everything and it will not allow to update anything.

I tried apt-get clean and it cleans up the buffer and i can update antthing.
Try it
it works

---

