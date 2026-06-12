---
title: "Remote Server Won't Reboot after Upgrade to 22.04"
date: 2024-08-12
forum: Installation &amp; Upgrades
---

### Post by smokey_58au on 2024-08-12
I have been regularly trying for over 2 years to upgrade my Ubuntu Server 20.04 to 22.04, but I have had no success.  It's the only time in my long history (since Dapper Drake) using Ubuntu that I've ever had a problem with upgrading, either Desktop or Server.  My server is on the Vultr platform, running Webmin/Virtualmin, and I can also access it remotely through SSH.

When I perform the upgrade via the terminal/SSH, everything goes as expected with no errors that I can see, and I choose the Default "N" for all the input screens that are displayed during the upgrade.  At the end it asks to restart, but at that point it fails to restart.  I can't ping the server, and my terminal screen hangs when it asks me for my SSH passphrase.  When I try to tty in from my Vultr console, it hangs after entering my password, and when I try to bring up the login screen in Virtualmin it can't find the URL.  Vultr shows the server status as running, which I assume is correct because the tty session identifies the server when it asks for my login credentials.

I have no way of knowing why the restart is failing without accessing the upgrade logs, and I'm unable to access the logs without being able to log in, so I can't have a look at them to try and troubleshoot.  The only way I can recover my server is to restore from the snapshot I take just prior to the upgrade, and this obviously removes any upgrade logs created.  Back when I first built the server, I was able to upgrade from 18.04 to 20.04 without issue, but anything I try with the 22.04 upgrade fails in the same way at the same point.  I have also tried upgrading using the inbuilt terminal session in Virtualmin, but had the same outcome.

Is anyone able to shed any light on what might be causing the failed restart, or how I might be able to access the logs?  Any assistance or thoughts would be very much appreciated, as this is becoming quite tiresome trying to do a simple upgrade.

---

### Post by TheFu on 2024-08-13
I treat my VPSes like cattle and my home systems like pets.  Seems like it is time to send this cow to slaughter.  Create a new VPS and manually migrate over.  This is a good time to check your DR plan.  May be worth choosing a different Vultr DC too.

When you are done, just change the DNS record.  Of course, you'll want to change the TTL on the DNS to be shorter to make all the client systems find it quickly.  Having a TTL of 1 day by default, then reduce that to 1 hour and to 5 minutes when you think it is ready for the switchover.

Perhaps the Vultr support team will help by swapping the IPs for you?  IDK, I've never asked them. Can't hurt to ask.

---

### Post by currentshaft on 2024-08-13
1356

---

### Post by smokey_58au on 2024-08-13
> **currentshaft said:**
> Use paragraphs because your wall of text is painful to read.

Done.

> Which commands did you run to "upgrade"?

 do-release-upgrade and sudo do-release-upgrade, depending on which account and which method I'm using to access the server to try the upgrade.  Not sure what relevance that has - it's the only command I'm aware of that does a release upgrade?  I update/upgrade the server and check for any helds before I commence the release upgrade.

> Why did you blindly choose "N" for each "input screen" without reading what each respective program is asking to change?

 I didn't.  I've tried this upgrade many, many times and have even downloaded each file that this choice appears for, then compared those files during the upgrade for the differences.  I have tried choosing "Y", I have tried being selective after comparing differences, I have tried editing the files pre-update to include any new changes.  Same outcome any way I try it.

> Can you access the serial console in Vultr?

I already mentioned trying a tty session from the Vultr console.  That always works when the server is up and running, never works after the upgrade - it hangs at the login screen.

> Also, stop using SSH passphrases and switch to public-key authentication.

Serious question - why?

---

### Post by smokey_58au on 2024-08-13
> **TheFu said:**
> I treat my VPSes like cattle and my home systems like pets.  Seems like it is time to send this cow to slaughter.  Create a new VPS and manually migrate over.  This is a good time to check your DR plan.  May be worth choosing a different Vultr DC too.

When you are done, just change the DNS record.  Of course, you'll want to change the TTL on the DNS to be shorter to make all the client systems find it quickly.  Having a TTL of 1 day by default, then reduce that to 1 hour and to 5 minutes when you think it is ready for the switchover.

Perhaps the Vultr support team will help by swapping the IPs for you?  IDK, I've never asked them. Can't hurt to ask.

I've been toying with doing this for a long time, and even though I know it will provide a fix, my many years consulting in IT have instilled a problem-solving mentality that I find hard to shake.  I would rather find out what's causing the problem to prevent it happening again, instead of running the risk of hitting the same hurdle in the future.  I have been using Linux (primarily Ubuntu) for almost 20 years and have never had an issue with any upgrade of any flavour that hasn't been quick and simple to fix, which is why this one is doing my head in.

It's still a good and viable (inevitable?? :( ) option to start with a clean slate, but my background is in software development, not servers, so it won't be a simple or quick task to build a new one, implement all the security I have added in bits and pieces over time, and then migrate the existing domains/apps running on it.  That's why I'm reluctant to go down that path without exhausting all avenues.  It runs my mail server and private cloud among other things, and I can't afford them to be offline for too long if I can get away with it.

---

### Post by TheFu on 2024-08-14
> **smokey_58au said:**
> I've been toying with doing this for a long time, and even though I know it will provide a fix, my many years consulting in IT have instilled a problem-solving mentality that I find hard to shake.  I would rather find out what's causing the problem to prevent it happening again, instead of running the risk of hitting the same hurdle in the future.  I have been using Linux (primarily Ubuntu) for almost 20 years and have never had an issue with any upgrade of any flavour that hasn't been quick and simple to fix, which is why this one is doing my head in.

It's still a good and viable (inevitable?? :( ) option to start with a clean slate, but my background is in software development, not servers, so it won't be a simple or quick task to build a new one, implement all the security I have added in bits and pieces over time, and then migrate the existing domains/apps running on it.  That's why I'm reluctant to go down that path without exhausting all avenues.  It runs my mail server and private cloud among other things, and I can't afford them to be offline for too long if I can get away with it.

I understand completely.  I also started out as a software developer.  Did cross-platform development on about 15 different platforms. That role got me sucked into being the admin + dev lead at a small company where I learned that pure knowledge is only good when it can be leveraged in the future.

Then I moved into a "Planning/Architecture" role and that opened my eyes to the admin way of thinking.  It is different from the developer way, because admins don't often really know how to tweak programs/settings, so they blow away systems and rebuild from scratch as their normal solution.

I've learned a hybrid approach.  I use my best judgement to see if I can fix any issue, but there's a running clock, because spending time on something you'll never see again is just wasted time.  The next upgrade will have a different issue.  It is never the same.  For me, it was the 16.04 --> 18.04 upgrade that taught me a valuable lesson. **All upgraded servers eventually have too much cruft to be fixed.**  Somewhere around the 3rd upgrade (that's LTS-LTS-LTS), the upgrades start having issues from cruft.  Sometimes the 3rd one works and I've had some simple systems where that happened.  

But if it doesn't work and it isn't a 30 minute fix, I blow away the upgrade, restore from backups/snapshots and work a different plan.  That plan is to migrate to a new VM.  In general, that tests all sorts of things, especially my disaster recovery plan and restore methods.  

If your backup/restore methods don't support restoring to completely new hardware, I think you need to rethink them.  Any of my systems can be restored in 30-60 minutes.  It isn't 1 command, but it is extremely flexible.  Swapping out the hardware/VM storage and networking underneath aren't an issue with the restore process.  As developers, we know that settings and data just need to "appear" to be in the same place as before. They don't actually need to be there.  Changing file systems or adding encryption don't matter either. At least not in my restore processes.

I've used my restore process to move from LTS-to-LTS a few times too.  Obviously, some of the packages are removed/gone going between releases and things that were PPAs or had to be manually compiled to be installed often are core packages in the newer OS, but from time to time there are sufficient changes that reworking things for the new OS is required.  For example, when systemd was forced onto us.  I slowly migrated all my init scripts over. There was some backwards compatibility provided, but that is gone now.  As more and more upgrades happen, that happens.  Old stuff that was supported from 2010 becomes obsolete. Sure, it works for a few years after that, but eventually, the new maintainers drop old support.  Some high profile things have been dropped in the last 5 yrs.  If you don't deploy new servers, it is easy to miss some of those things.

I only plan to do 1 LTS upgrade, then I do a fresh install.  That gets me 6-9 yrs of stability (I don't touch non-LTS releases) with 1 fresh install then 1 upgrade on servers and usually my main desktops.  10 yr old systems usually are so slow compared to new systems that a fork lift upgrade makes sense.

There's a time to wipe everything. From reading what you looking at, I think you are well passed that time.  Heck, there's s different grub boot loaded now.  This time around, as you build the system. Consider creating a script (or use something like Ansible) to make the base things you need and another script for customized settings just for this system.  Test the script a few times to be certain it creates reproducible results.  If all you end up with is a list of commands that you select/paste into the freshly installed VM, that's still reproducible.  I have a few snowflake systems like that too.   At the same time, you might want to comment every config file with a tag so they are easily found later.  _# :KEEP:_  or something like that let's you do a quick search for config files on your systems that need to be included in your new backup methods.  Some of those will be for reference only and others can be blindly copies back pre-restore, but post-OS install and pre-packages install (if that makes sense).

---

### Post by smokey_58au on 2024-08-14
Thanks heaps for your reply, the information and perspective you gave me has helped considerably.  I'm going to look at a fresh install now, after I've got things backed up and scripted to a point where I'm comfortable I won't lose functionality, security or (most importantly) too much downtime.

---

### Post by TheFu on 2024-08-14
> **smokey_58au said:**
> Thanks heaps for your reply, the information and perspective you gave me has helped considerably.  I'm going to look at a fresh install now, after I've got things backed up and scripted to a point where I'm comfortable I won't lose functionality, security or (most importantly) too much downtime.

You shouldn't have **any** downtime ... well, less than 5 minutes as the DNS records point to the new server rather than the old one.  If you get the DBMS mirroring happening active/standby, then you just need to break that link and make the standby the active and either stop replicating or replicate the opposite direction.  If your DBMS doesn't do that, use a non-toy DBMS.  I suppose you could dump/restore the full DBMS (all tables, views, accounts) between the old system and the new system, then rsync the text file over and restore it quickly.  That shouldn't be too long for non-enterprise setups.  

Or you could break the upgrade process into the web-frontend part and the DBMS part.  Just depends on whether you might need better performance and need a separate DBMS server going forward. That's a judgement call.  If 95% of your web pages are displayed in under 0.5s, I wouldn't bother.

---

