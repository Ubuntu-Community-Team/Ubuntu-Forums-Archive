---
title: "Problem upgrade PC from 18.04 to 20.04; thinks it is i386"
date: 2020-05-27
forum: Installation &amp; Upgrades
---

### Post by FoxJT on 2020-05-27
Apologies if already discussed elsewhere.  

I have a PC which is 64bit. It has a two partitions with Ubuntu and W7.  The W7 (64bit version) partition tells me it is "x64 based PC". I am running 18-04 32bit and I want to upgrade to 20.04. When I try to do this, it tells me I can't because the PC has i386 architecture.  Checking lscpu it tells me it is i686, and the cpu is definitely 64bit.  I created a DVD with 20.04 on it and ran this successfully from the DVD.

When I do "do-release-upgrade" it starts and then bombs out telling me it can't do it because it is i386 architecture.  

How can I convince the upgrade procedure it is OK to continue?  If I install the 20.04 from the DVD, it will destroy what I have on the HD. I do have a backup.  

Another related question: can i restore a 32bit backup to a 64bit OS?

I have Gparted loaded in case I need to do anything to the linux side.

Thanks.

---

### Post by CelticWarrior on 2020-05-27
Ubuntu 20.04 has no 32-bit version. You can't update 18.04 32-bit, you can keep it until April 2023, it's over after that.

---

### Post by FoxJT on 2020-05-27
Thanks Celtic Warrior.

I understand that!!!  The problem is that my PC IS 64-bit (i686). 18.04 is running at 32-bit.  I want to upgrade to 20.04 which is as we know, 64-bit only.  As 18.04 is running at i386 and the upgrade doesn't like that, does that mean that I have to install 20.04 from scratch, rather than an upgrade?  If so, when I do that 20.04 install, how do I restore my current system apps, etc? Will the i386 backup support a restore to ai686 PC? Forgive my "basic" questions, but I have never needed to  do a restore up to now!

Thanks.

---

### Post by deadflowr on 2020-05-27
i686 is 32-bit.
amd64 is 64-bit.
i### are all 32-bit. (i386,i486,i586,i686 are all 32-bit)
> As 18.04 is running at i386 and the upgrade doesn't like that, does that mean that I have to install 20.04 from scratch, rather than an upgrade? 
Not that it doesn't like it, it's more that it has no idea what it is.
And yes, you'd have to do a clean install if you want to upgrade to 20.04.
Basic Backup guide: [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by FoxJT on 2020-05-27
Hi CelticWarrior again!

Apologies! Re-reading what you said made me think again about what I am expecting this to do. Of course the upgrade would work as I wanted it if it was already a 64 bit os installation. However, it is more fundamental than that!  So it must be a clean install of 20.04 and a restore of the complete backup. I now assume that the backup must be "limited" as we don't want to introduce file conflicts. A read of the user / installation guide wouldn't go amiss!

Thanks.

---

### Post by FoxJT on 2020-05-27
So I686 is still 32bit! Mea culpa! Strangely, I have W7 on the other partition and this reports the system as "x64 based PC".

Confused?

---

### Post by deadflowr on 2020-05-27
> **FoxJT said:**
> So I686 is still 32bit! Mea culpa! Strangely, I have W7 on the other partition and this reports the system as "x64 based PC".

Confused?

The actual physical machine is 64-bit capable.
But that has no bearing on whether or not you installed a 64-bit operating system.

---

### Post by CatKiller on 2020-05-27
> **FoxJT said:**
> I now assume that the backup must be "limited" as we don't want to introduce file conflicts.

Files aren't any different between a 32-bit or a 64-bit install. The difference is how the binaries and libraries behave, all of which you're installing fresh as 64-bit. For your user files and config files there's no difference at all.

---

### Post by FoxJT on 2020-05-28
I bit the bullet, backed up my 18.04 system, loaded 20.04 from DVD and restored my backups. It all went well if taking a longish time. Watching the files as they restored, I realised how much old, obsolete, duplicated stuff is there!! A tidy up and clear out for tomorrow!
Thanks to all those who helped me clarify my thinking and pointed me in the right direction.&#128077;

---

