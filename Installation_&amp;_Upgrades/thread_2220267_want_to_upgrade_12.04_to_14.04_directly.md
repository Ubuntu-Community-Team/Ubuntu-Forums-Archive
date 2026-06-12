---
title: "want to upgrade 12.04 to 14.04 directly"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by tusharkoshti on 2014-04-27
I am using Ubuntu 12.04. I want upgrade it.  Can I upgrade it to 14.04 directly ?
I read , we cant upgrade directly. We have to upgrade it , version by version. 
But somewhere I found link saying " How to upgrade 12.04 to 14.04" 
Is it possible ? 
if yes , please give reliable soultion.

---

### Post by Iowan on 2014-04-27
From what I've read, the direct upgrade from 12.04 to 14.04 will come when 14.04.1 is released (July?)

---

### Post by Hodevah on 2014-04-27
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

have you tried this? It's quiet elementary but it might work. If not, then you might just have to upgrade via iso file

someone might have to correct me if my method does not work.

---

### Post by ibjsb4 on 2014-04-27
Dist-upgrade has nothing to do with a release upgrade.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by deadflowr on 2014-04-27
> **Iowan said:**
> From what I've read, the direct upgrade from 12.04 to 14.04 will come when 14.04.1 is released (July?)

Yes, that's right.

It's because, the thinking is that most system's running 12.04, are probably production environments and the need for the upgrade process to be solid is increased.
So the next few months will be used to fix any lingering problems that weren't addressed, or where found during that time, so that the upgrade for those on 12.04 will be as hassle-free as possible.

As a sidenote, you can upgrade from 12.04 to 14.04 now if you run the -d(d= development) flag.
```
update-manager -d
```
That should list the 14.04 upgrade option.

**BE WARNED**> As with any development cycle/process/whatever-you-want-to-call-it your chances of breakage while doing this are increased, versus waiting for the official ability.

---

### Post by squakie on 2014-04-27
Just a novice asking a dumb question:  if the -d option on update-manager is for "development", is 14.04 considered development, or will it try for what ever is the newest under development?

---

### Post by deadflowr on 2014-04-27
the -d flag will upgrade you to the next available release for your version that has not reached official release yet.
Since 14.04 has not reached official release for upgrades from 12.04, it's still in development.

After the official release I'm not sure where it points, but I suspect it would still point to the 14.04 release, and not 14.10 or newer.

Don't know if that makes any sense.

---

### Post by squakie on 2014-04-27
Yep - sounds like it picks up what ever is the next development release.  What my concern is is that 14.04 is in release now (at least that's what shows when you go to "Get Ubuntu").  I just want to make sure the OP doesn't pick up something like a development release of say 14.10 or something like that ;)

---

### Post by tusharkoshti on 2014-04-29
Thank you friends for your help. 
I upgraded from 12.04 to 14.04 through command     
update-manager -d 
For that I required almost 2-3 hrs. 
I checked it's version also. Hope it is up to date.

tushar@tushar-VPCEH3AEN:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
tushar@tushar-VPCEH3AEN:~$

---

### Post by monkeybrain20122 on 2014-04-29
Yeah why do you want to do it though?

 It may seem easy for the lazy to just push a button but it is misleading. First for 'upgrade' to work at all you need to have a fairly pristine system, basically no ppas, no third party applications such as proprietary driver and no change in system configuration files, all of these I find unlikely if you have been using 12.04 for two years. so you need to do some work to undo all these before upgrade. 

Now "upgrade" takes several hours and you will be prompted several times as it goes along, and during those several hours many things can go wrong and if say you suddenly lose internet connection (e.g wifi) then you are left with a broken system. You take a look at the forum threads, many issues are the results of bad or failed upgrades. The time to trouble shoot a bad upgrade may take even longer.

So to save yourself the troubles, backup your data and do a fresh install, which takes about 15 minutes (14.04 installation is very fast). Also make a separate /home so you will be able to keep your settings next time when you do a clean install. 

"Upgrade" is a long, fragile and unreliable process and it should come with a big warning, and I can't believe that they would prompt you to just push a button on impulse with a update-manager pop up. Even experienced users have hosed theirs system because they got distracted and press the button by accident.

---

### Post by Warren Hill on 2014-04-29
I'd recommend you wait for [14.04.1 due 24 July]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule") then backup before you update.

The point release is when we feel it's been tested by enough users that any initial bugs have been fixed and it will just work. So that's when the update manager will start asking you if you want to upgrade.

As pointed out by monkeybrain20122 Upgrades can go wrong so I usually prefer to do a clean install as well but you should be OK just pressing the button.

If you want to upgrade now however I'd recommend using the iso file.

I think

```
update-manager -d
```

Will still give you 14.04 but as pointed out by deadflowr strictly speaking this is place for the development release.  I don't think the developers have changed anything yet but I could be wrong.

---

### Post by squakie on 2014-04-29
They said the update did run and they are now at 14.04, so instead of things that could go wrong in the update process itself, maybe we should have the OP check things now that may have been affected by the update.  Things like check the wireless - it may be running fine now on a newer release.  Check the video - is it okay, does it do what you need it to?  Do you remember ever installing something other than via the package manager or software center?  If so, those things will need to be addressed again.  Etc., etc., etc.   The update is done - now how to check that everything is still ok.

---

### Post by Bucky Ball on 2014-04-29
*Thread moved to **Installation & Upgrades**.*

---

