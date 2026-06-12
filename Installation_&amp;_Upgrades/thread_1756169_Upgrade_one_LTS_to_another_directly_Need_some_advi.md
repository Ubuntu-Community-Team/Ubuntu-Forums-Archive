---
title: "Upgrade one LTS to another directly? Need some advice"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by blauendonau on 2011-05-11
I was surprised to discover that that users of Hardy Heron could upgrade directly to Lucid Lynx since both versions are LTS.

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

Will this feature continue to be implemented? In other words, will users of 10.04 be able to upgrade to the eventual 12.04 LTS without having to go through the interim versions? 

The reason I'm asking is because I just finished reinstalling 10.10 after finding Natty to be unusable (slow, buggy, wouldn't shut down). Since I haven't invested anything into this fresh install yet, would it be worth going back one more version, to 10.04? I'm into stability and convenience over cutting-edge, so the idea of sitting with one LTS for several years and being able to jump to the next LTS when it becomes available appeals to me. I don't like the thought of having to upgrade twice a year, with all the risks of something breaking.

So, I'm looking for a little advice on what to do. Thanks :-)

---

### Post by confused57 on 2011-05-12
I would "assume" one would be able to upgrade from LTS to the next LTS version.  I've been using Hardy 8.04 since it was released, but I wouldn't recommend doing an upgrade to 10.04.  I think most would recommend a clean install of the next version vs. an upgrade, which is prone to possible issues & problems.

You could back up your home folders:
[http://members.iinet.net.au/~herman546/p13.html](http://members.iinet.net.au/~herman546/p13.html)
then after doing a fresh install, copy over your "old home" folders/configuration files.

I have a separate /home partition, so installed 10.04 over top of the 8.04 root(/), but chose not to format /home(but specify it to be used as 10.04's /home, using manual partitioning).

I had to reinstall the programs I used, as well as, set up my printers again.  All my Thunderbird, Firefox, Kmymoney, etc settings, emails, bookmarks, etc. were there & no problems with 10.04.

---

### Post by tommcd on 2011-05-12
> **blauendonau said:**
> 
Will this feature continue to be implemented? In other words, will users of 10.04 be able to upgrade to the eventual 12.04 LTS without having to go through the interim versions? 

Yes, unless there are changes made to this policy, which seems unlikely, then you will be able to (in theory) upgrade from one LTS to the next LTS indefinitely.
Personally, I always do clean installs myself.

---

### Post by ivanovnegro on 2011-05-12
In theory its possible and that is the policy but like the other posters I would go for a clean install.

---

### Post by akand074 on 2011-05-12
Clean install + separate /home partition is where it's at. Theoretically, that should work though. I wouldn't recommend it though.

---

### Post by blauendonau on 2011-05-12
Thanks for all your replies!

I was sort of expecting that, but just checking. Clean install still means I'll have to reinstall all the programs, right? And is upgrading from one LTS to another any more risky than a standard upgrade? I mean, LTS releases are supposed to be extra-stable, no? (Comparatively speaking. I know it's not possible to be "Debian-stable" with a six-month release cycle.)

There are three computers that I'm going to transition to Linux in the next few weeks, and doing up to six total upgrades/installs per year isn't an option if they'll run Ubuntu. The less maintenance to do, the better.

So is it best to overwrite Maverick with Lucid LTS and sit with it for the next year or two, since my goal is to have something stable that won't need to be upgraded for a long time? Or is it even important that the release be "supported"? I'll install LTS on the other machines for sure, but for this one I'm pondering if it's worth the trouble for yet another reinstall.

Thanks again!

---

### Post by kostkon on 2011-05-12
My upgrade to 10.04 was 100% successful (from a heavily used 8.04, that had also been upgraded 2 times in the past, from 7.04 to 7.10 and then to 8.04). So, you should definitely try an upgrade if that's what you want to do (obviously, backing up your data first is a prerequisite).

---

### Post by snowpine on 2011-05-12
Upgrading directly from LTS to LTS is 100% easy, supported, and recommended.

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

Occasionally, a new feature is introduced that requires a fresh reinstall, *if you wish* to take advantage of that feature. An example of this is the ext4 filesystem; upgrading 8.04 to 10.04 does not convert the existing ext3 to ext4.

---

### Post by blauendonau on 2011-05-12
> **kostkon said:**
> My upgrade to 10.04 was 100% successful (from a heavily used 8.04, that had also been upgraded 2 times in the past, from 7.04 to 7.10 and then to 8.04). So, you should definitely try an upgrade if that's what you want to do (obviously, backing up your data first is a prerequisite).

Yeah, that's what I initially thought. I mean, upgrades are quicker if they're successful because programs, files, etc., remain intact, less "maintenance". If an upgrade breaks my system everything will obviously be backed up anyway, so I can do a fresh install and nothing's really lost compared to if I'd just done a fresh install right away.

So, perhaps another question to ask is: how safe are upgrades in general? I've heard a lot of complaints from people transitioning from Maverick to Natty, but this seems to be a more "buggy" release than usual. Are they always this way? (I've never done an upgrade before, always clean installs, so I have no experience with it.)

---

### Post by YesWeCan on 2011-05-12
I have a question.
It seems the majority of users recommend a clean install upgrade.
When I just searched the Community Documentation for this I was unable to find anything, or anything complete. The sign-posted front page did not lead me to a procedure. There are detaled instructions on doing a regular upgrade.

What is the procedure?

Eg: If /home is in a separate partition then you erase and re-install to the /root partition and remount the original /home.
OK. But what happens to all your applications?
What about listing all your existing apps before the install so you can remember what you've lost, if you do lose them? Can the inventory and re-installation be automated?
If you re-install the apps is there going to be any conflict with old apps files that are still in your original /home?
What about all your configurations in /etc?

How easy is this to do?

---

### Post by akand074 on 2011-05-12
> **YesWeCan said:**
> I have a question.
It seems the majority of users recommend a clean install upgrade.
When I just searched the Community Documentation for this I was unable to find anything, or anything complete. The sign-posted front page did not lead me to a procedure. There are detaled instructions on doing a regular upgrade.

What is the procedure?

Eg: If /home is in a separate partition then you erase and re-install to the /root partition and remount the original /home.
OK. But what happens to all your applications?
What about listing all your existing apps before the install so you can remember what you've lost, if you do lose them? Can the inventory and re-installation be automated?
If you re-install the apps is there going to be any conflict with old apps files that are still in your original /home?
What about all your configurations in /etc?

How easy is this to do?

Well I always do it through a manual install using the installation disk. Basically you just select your '/' partition select to use it as EXT4 and format it and then choose to use your '/home' partition as ext4 WITHOUT formatting. Then let it install, it'll wipe your '/' partition and give you a clean install.

All of your applications will be gone! It'll be a clean, brand new install. But your data and config files are still there undamaged. So basically you just reinstall all your applications and when you run them you don't have to switch the settings back to what you want or re-add your bookmarks/addons or put your messenger chat info back in etc etc.

---

### Post by YesWeCan on 2011-05-12
> **akand074 said:**
> But your data and config files are still there undamaged.
Thanks for explaining. It sounds like the user's configurations would be retained because they are within /home but the global configurations and any root home directory files will be wiped. For example, SSH config files, OpenVPN, Samba configs, mdadm, Grub file in /boot/grub, perhaps Java and database and webserver directories  and anything else of that nature.

So there is some work required beforehand to identify what all the current applications are and what all the current global/root configuration files are.

I suppose one could back it all up first, then do a diff between the new and old / filesystems to see what needs copying back.

Is this your understanding?

---

### Post by blauendonau on 2011-05-12
Thanks for the information. But it doesn't completely answer my question: are upgrades safe in general to do? I'd be interested to hear perspectives on that. Once again, I'm interested in convenience and stability over than cutting-edge. It'd be nice to get away without having to reinstall all the repositories/programs.

In any case, I'm going to pop in the 10.04 LTS disk and overwrite the Maverick partition with it, if for no other reason, because it'll be supported a year longer. Thanks for the feedback so far, appreciated. :-)

---

### Post by snowpine on 2011-05-12
> **blauendonau said:**
> Thanks for the information. But it doesn't completely answer my question: are upgrades safe in general to do? I'd be interested to hear perspectives on that. 

Release upgrades are the official recommendation of ubuntu.com. Theoretically they should be smooth and safe. In practice of course no software is perfect, there are always bugs, and this applies to the update manager as well. You should always check the release notes and the forums before doing an upgrade. Furthermore, since hardware compatibility can change over time, I always recommend test-driving a Live CD of the target release, even if you are planning to upgrade-in-place. If there are any incompatibilities, it's better to know about them before you commit to the upgrade.

---

### Post by blauendonau on 2011-05-12
Okay, just finished the install of Lucid + about 340mb worth of updates and the nvidia drivers, works like a charm and it's nice to know it'll be supported for another full two years.

I'm concerned about upgrade safety because I've seen a LOT of people complain that the lastest upgrade caused their system to be unusable or even unbootable. Then again, Natty seems to have been less smooth than previous releases, so I don't know if this is an exception to the norm.

Anyways, I think I'll take snowpine's advice. There's no rush for me, Lucid will suit my needs perfectly for the next ~18 months and then I'll look into 12.04. Thanks everyone once again.

---

