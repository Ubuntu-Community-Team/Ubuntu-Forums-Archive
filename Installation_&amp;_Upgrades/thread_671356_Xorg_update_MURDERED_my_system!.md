---
title: "Xorg update MURDERED my system!"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Cleric. on 2008-01-18
After installing the new Xorg update and restarting, I noticed problems almost immediately after Compiz started; glitches after a short while led me to restart almost immediately. 
Thinking that it was just a temporary problem, I restarted a few more times to get the exact same results.
After some research on the issue, I discovered my problem and attempted to boot again, when I was met with a filesystem error. I ran "fsck" and pressed "y" a bunch of times, fixing some things, and restarted.
As soon as I was able to, I switched my drivers to "vesa" from "nvidia" in my xorg.conf file and reinstalled my drivers through a failsafe startup of KDE (I'm using Envy and figured this would be the easiest way). I then changed xorg.conf to look at my nVidia drivers on the next boot.

Well after ALL of that, I expected things to be back to normal...but they're far from it.
Whenever I try to boot now, the loading bar gets about 1/10th the way and just freezes. I can't ctrl+alt+F1 or do anything at all.

What should I do?!

---

### Post by atoponce on 2008-01-18
Sounds like you need to boot into a rescue environment, and gather some more information.  Before you do that, however, find out exactly where in the boot process it is freezing.  If needed, grab an Ubuntu alternate CD, and type 'linux rescue' at the prompt.  Verify that you can mount your partitions, and that everything is in place.  It sounds like you actually may have either faulty harddrives, or bad blocks in place, that fsck can't fix.

---

### Post by Cleric. on 2008-01-18
I did manage to ctrl+alt+F1 before the freeze (it took a few tries) and the place it is stopping at is right after "kinit: No resume image, doing normal boot..."
I'll grab an Ubuntu CD and make sure my drives are mountable.
Is there any other sort of information I could provide or anything else I could do to help the situation?

EDIT: I started up from an Ubuntu livecd and successfully mounted both of my drives.
I am going to try linux rescue now.

---

### Post by Discombobulated on 2008-01-18
I'm getting:>  Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  403 ForbiddenWhen synaptic attempts to update the xorg core... so it looks like something's 'up'. ;)

(Can't get the i386 .deb either, same 403).

---

### Post by GICodeWarrior on 2008-01-18
> **Cleric. said:**
> 
Well after ALL of that, I expected things to be back to normal...but they're far from it.
Whenever I try to boot now, the loading bar gets about 1/10th the way and just freezes. I can't ctrl+alt+F1 or do anything at all.

What should I do?!

That is pretty unfortunate.  I got this update from a mirror I use (it is blocked on the main site for obvious reasons), and it broke eclipse for me.

I fixed it by downgrading.  To downgrade, start by creating a file called /etc/apt/preferences with the following content.
```
Package: xserver-xorg-core
Pin: version 2:1.3.0.0.dfsg-12ubuntu8
Pin-Priority: 1001
```

Once you have that, run "apt-get install xserver-xorg-core" and the package will be downgraded.

Since your machine has degraded so far, if you have any important information on it, I would start by booting a livecd, mounting the filesystem read-only, and pulling as much of your data as possible.

---

### Post by Cleric. on 2008-01-18
Well I think it's a little too late to downgrade now; I can't boot at all and I doubt that Xorg is causing that problem :P .
I can mount both of my drives perfectly fine and navigating them hasn't caused any problems yet.

@atoponce:I tried running linux rescue on a livecd terminal but it said I needed to install some things; I then saw that you said alternate CD.  I don't have one of those handy (yet), so is there anything I can do in the meantime?

---

### Post by siouzi on 2008-01-18
What is the issue? This morning I noticed some Xorg update too and ran it. Luckily it didn't murder my entire system, only compiz. When trying to start compiz the x-server seems to restart and I end up with the login screen. I'm using the NVidia's drivers from their site. What should I do, wait? Without compiz I feel desperate :(

Edit: Downgrading to xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8 didn't fix compiz :/

Edit2: Woohoo! Thanks to oscarsfriend I got compiz back!

---

### Post by oscarsfriend on 2008-01-18
> **siouzi said:**
> I'm using the NVidia's drivers from their site. What should I do, wait?

Quite possibly you had the same problem as me, which I solved here: [http://ubuntuforums.org/showthread.php?t=671091](http://ubuntuforums.org/showthread.php?t=671091)

Waiting or downgrading most likely won't help, as chances are the update overwrote a symlink to a file needed by the nvidia drivers.  Either reinstall the driver, or follow my instructions in the post above to reinstate the symlink.  Chances are you will have to do this again when you install the fixed version of the xorg packages.

---

### Post by Cleric. on 2008-01-18
Well, I tried to start up in recovery mode, but it stopped and gave me an error saying something relating to nVidia was corrupt or something. I am going to re-boot in a minute to check exactly what the error was.

EDIT: This is the exact error I am receiving:
[    12.860000]  nvidia: module license NVIDIA taints kernel.

What does this mean? :/

---

### Post by oscarsfriend on 2008-01-18
> **Cleric. said:**
> [    12.860000]  nvidia: module license NVIDIA taints kernel.

What does this mean? :/

I don't think it is anything important.  I'm pretty sure that it means that you are using non-open source drivers, or something like that.  Anyone who installs nvidia's own drivers (or any other manufacturers) will get the same sort of message.  I get it too:
```

Jan 18 20:34:07 192 kernel: [   27.856166] nvidia: module license 'NVIDIA' taints kernel.

```
(Cut and pasted from my /var/log/kern.log.)

EDIT: Did you see my post up above, by any chance?

---

### Post by chek2fire on 2008-01-18
I have the same problem.The solution is to reinstall the driver.

---

### Post by eks on 2008-01-18
Confirmed, had the same problem. Installed the xorg upgrade and it blew up my system. Booting in recovery mode and reinstalling nvidia driver worked. 

Nevertheless, it's quite frustrating when an OFFICIAL upgrade breaks your system... :|


eks

---

### Post by PinkFloyd102489 on 2008-01-18
Same thing happened to me earlier. I downloaded the Nvidia drivers from the site onto a flash drive and then booted into Recovery mode. Reinstalled the drivers, started up normally. Dont know what happened but I fixed it.


Mine happened without the xserver upgrade. It was 403'd for me but my system broke anyway.

---

### Post by Cleric. on 2008-01-18
Well, I CAN'T boot into recovery mode; the last thing I see before I try to boot into recovery mode is that nVidia error, then it freezes. 
I can let it hang, I guess, but I don't think it is going to end up going.

EDIT: It's been hanging for a while now, and nothing has happened. 
I rebooted into the livecd and checked every log I could think would be relevant, but the logs just show the last SUCCESSFUL boots, none of these past failed, incomplete boots.
Is there anything at all I can do?

---

### Post by slayer^_^ on 2008-01-19
confirmed.. ubuntu starts up, however it freezes and my keyboard lights go crazy. compiz? firefox? who knows....
however a minute ago there were updates available, now i try reinstalling my nvidia drivers and i'll tell ya (geforce 6800)

bestregards

---

### Post by sveterv on 2008-01-19
YES! YES! YES! Reinstalling nvidia drivers solved problems with latest xserver-xorg-core update. Before that, I was able to log, but when i started some software that uses Wine, X server restarted :) and I was back to the login screen.

Thanks for help guys.

---

### Post by olavjunior on 2008-01-21
Tip! Check this out, helped me :)
[http://ubuntuforums.org/showthread.php?p=4178542#post4178542](http://ubuntuforums.org/showthread.php?p=4178542#post4178542)

---

