---
title: "Synaptic update has trashed my system!"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Land Rover Series 3 on 2009-11-23
Just powered up 10 minutes ago and went into Synaptic package manager to look around. It automatically brought up a load of suggested upgrades, including Linux kernel and various Linux headers etc. As a novice, and without any real explanations as to what they all were, I followed the advice and upgraded.

ON REBOOT ALL I GOT WAS A FLASHING LOGIN PROMPT THAT WOULDN'T LET ME TYPE PROPERLY.

What's happened? Does anyone have an explanation for this. Better still, does anyone know have to undo the upgrade (system was working perfectly before, and still does if I boot up into the "old" system)?

Makes one wonder whether to trust ANY future updates suggested by Synaptic!!!!

---

### Post by audiomick on 2009-11-23
Don't panic. Most likely, all the is broken is the GUI. I can't tell you how to fix it without researching for a couple of hours, but I know you can.

---

### Post by bloke-brian on 2009-11-23
> **Land Rover Series 3 said:**
> Just powered up 10 minutes ago and went into Synaptic package manager to look around. It automatically brought up a load of suggested upgrades, including Linux kernel and various Linux headers etc. As a novice, and without any real explanations as to what they all were, I followed the advice and upgraded.

ON REBOOT ALL I GOT WAS A FLASHING LOGIN PROMPT THAT WOULDN'T LET ME TYPE PROPERLY.

What's happened? Does anyone have an explanation for this. Better still, does anyone know have to undo the upgrade (system was working perfectly before, and still does if I boot up into the "old" system)?

Makes one wonder whether to trust ANY future updates suggested by Synaptic!!!!

Same problem here with todays update that required a restart because there was kernel update.
I too only have flashing text after the Ubuntu logo splash would normally change to the animated progress bar. The flashing text  is trying to stop Firestarter.

I'm now stuck using just  a Karmic livecd and hope I can fix the  installed OS.
Can any of the boot scripts be edited to rescue it or workaround Firestarter?

(This reminded me of an earlier borked upgrade from Jaunty to Karmic so I even plugged in that old drive and it too eventually was stuck in the same boot stage though trying to  stop Firestarter was a subsequent message)

---

### Post by Land Rover Series 3 on 2009-11-23
From looking around the forum, it seems this is a fairly widespread problem. I've only been using Linux a few days so far, gradually trying to learn it, so you've lost me with whatever Firestarter is, and what consequences it has for the kernel. However, I thought that one of the great benefits of open software was SUPPOSED to be that things were thoroughly tested BEFORE they got issued as stable. Doesn't seem to be the case here. I hope someone who knows about these things can get this problem sorted out pronto, or I'll have to seriously consider whether to carry on with Ubuntu if this kind of mess is going to keep on happening in the future.
Not a happy bunny.

---

### Post by bloke-brian on 2009-11-23
Been using various Linux distros for 5yrs and I very rarely have problems doing either distro upgrade or kernel updates like today. Its hard to test things 100% with so many combinations of sw & hw so these things sometimes slip thru as much as it sucks.

This problem may be  too new to have much traffic on forums or IRC if its limited to only a few of us.
I mention Firestarter as its the only flashing text (beside the flashing login which can't be used). Its just a gui frontend to configure the internal firewall iptables.

 Can you read any relevant flashing message ?

---

### Post by kestrel1 on 2009-11-23
I would suggest posting a bug report if you think this is a bug & carry on using the older kernel for the time being. If you do not get a grub menu up at start up press the ESC key just after post has finnished & you should get the grub menu up & you should see the older kernel in the menu. Use that for now & post the report.

---

### Post by bloke-brian on 2009-11-23
Thanks Kestrel After several re boot attempts was able to press Esc in time to pick  2.6.31.14 so I'm back.  I will look around for other traffic if 2.6.31.15 has not yet been reported for this issue.  In StartUp-Manager my grub timeout had been 10 secs so now its a mystery that pressing Esc is so tricky.

---

### Post by mkvnmtr on 2009-11-23
I know it does not help you but after reading your post I booted back into my 9.10 install. I had done the updates this morning and then gone to another distro. I seem to find no problems so it is a problem just some are having and a bug report is the way to proceed. 
Probably a simple fix and someone that remembers how will come on shortly with some advice. Until then just booting into the old kernel will keep you going.

---

### Post by Land Rover Series 3 on 2009-11-23
The only flashing message I can read is the login prompt, but that's flashing pretty well.
Something seems to be jamming up the cpu's though, because with all the flashing 'un all it won't recognise my keystrokes unless I happen to synchronise a key press with the system reading it. But tha't nfu for the password of course, because that doesn't show up anyway.

I thought fundamental changes to the kernel etc. were only supposed to happen every 6 months or so, so I presumed the upgrade suggested was just some minor tweaks to odd files. Seems I was wrong.

---

### Post by Land Rover Series 3 on 2009-11-23
> **kestrel1 said:**
> I would suggest posting a bug report if you think this is a bug & carry on using the older kernel for the time being. If you do not get a grub menu up at start up press the ESC key just after post has finnished & you should get the grub menu up & you should see the older kernel in the menu. Use that for now & post the report.
Fortunately, when I boot up Grub gives me the following 2 main options...

Ubuntu, Linux 2.6.31-15-generic
     (this is the default, and the one that doesn't work)
Ubuntu, Linux 2.6.31-14-generic
     (this still works like a treat, like it always has)

Would really like to be able to (a) preferably, restore the system back to how it was before the upgrade made such a mess of it all, or (b) delete the first option from Grub and tell it to automatically boot up into the old system. Any way of doing either of these, preferably the first?

---

### Post by wilee-nilee on 2009-11-23
> **Land Rover Series 3 said:**
> From looking around the forum, it seems this is a fairly widespread problem. I've only been using Linux a few days so far, gradually trying to learn it, so you've lost me with whatever Firestarter is, and what consequences it has for the kernel. However, I thought that one of the great benefits of open software was SUPPOSED to be that things were thoroughly tested BEFORE they got issued as stable. Doesn't seem to be the case here. I hope someone who knows about these things can get this problem sorted out pronto, or I'll have to seriously consider whether to carry on with Ubuntu if this kind of mess is going to keep on happening in the future.
Not a happy bunny.

If you think open software is supposed to be a final product your are partially correct. This depends on hardware though and if the open software is written and distributed on the web, and whether it has been modified for a distribution. Now all Ubuntu releases are sent out with inherent bugs this is where if you have not been a part of testing, then the general public is part of the bug tracking. It is common knowledge that a percentage of the programs in Ubuntu are modified open source code, so a reasonable conclusion is that there may be inherent problems. No program or OS is perfect, and threatening to leave Ubuntu is a supported idea in general in that go where you are happy and feel safe and supported, it will get little sympathy though from people who recognize and know the nature of OS of any type.

---

### Post by pjalegria on 2009-11-23
I have update error on today update linux kernel 2.6.31-15, is it a bug?

---

### Post by Land Rover Series 3 on 2009-11-23
> **wilee-nilee said:**
> If you think open software is supposed to be a final product your are partially correct. This depends on hardware though and if the open software is written and distributed on the web, and whether it has been modified for a distribution. Now all Ubuntu releases are sent out with inherent bugs this is where if you have not been a part of testing, then the general public is part of the bug tracking. It is common knowledge that a percentage of the programs in Ubuntu are modified open source code, so a reasonable conclusion is that there may be inherent problems. No program or OS is perfect, and threatening to leave Ubuntu is a supported idea in general in that go where you are happy and feel safe and supported, it will get little sympathy though from people who recognize and know the nature of OS of any type.
Understood, and I can agree with your sentiments, to a point. I cannot honestly complain too much about an operating system that is free to install and use, and works so very well (at least the previous version on my machine), has such a lot of top-quality, free software available, and is so well supported by forums and users such as here.

However, there is another side to the coin, and that is to do with confidence in the operating system to keep performing stably in the future. If I am forever going to be anxious about ever upgrading my system again in the future, that's not good for confidence. But do I have a choice in whether to upgrade or not? If I were to re-install everything from the DVD (to revert the system completely back to how it was before today), that's a lot of work (again!), and brings another problem ... when I installed originally, Synaptic Package Manager quickly flagged up a whole series of upgrades, which worked flawlessly. If I re-install now, it will surely upgrade to the current level, i.e. re-introduce all of the same problems. Hence I will be forever discouraged from any future upgrades.

I've only ever used Windows before, but the M$ upgrades don't tend to re-install the kernel, just tweak things about a bit. And you can always revert back to how things were is something goes awry. I don't know of any way of doing that under Ubuntu (which isn't to say there isn't, just that I'm not versed enough to know).

Regards

---

### Post by bloke-brian on 2009-11-23
Land Rover You can set grub to pick 2.6.31-14-generic as default in System -> Administration -> StartUp-Manager.  At some point later when 2.6.31-15 is OK again you will be able to change to it.

---

### Post by Land Rover Series 3 on 2009-11-23
> **bloke-brian said:**
> Land Rover You can set grub to pick 2.6.31-14-generic as default in System -> Administration -> StartUp-Manager.  At some point later when 2.6.31-15 is OK again you will be able to change to it.
Thanks, that's what I'm doing (enabling me to reply to you). Pity that Grub doesn't (afaik) allow me to set a user-defined default boot up though - the one that doesn't work is the default. Will wait to see if Ubuntu fixes this problem.

Regards

---

### Post by bloke-brian on 2009-11-23
My previous references to Firestarter can be disregarded as I disabled and uninstalled it, then tried booting with 2.6.31-15 and it failed at the same point.

---

### Post by wilee-nilee on 2009-11-23
> **Land Rover Series 3 said:**
> Understood, and I can agree with your sentiments, to a point. I cannot honestly complain too much about an operating system that is free to install and use, and works so very well (at least the previous version on my machine), has such a lot of top-quality, free software available, and is so well supported by forums and users such as here.

However, there is another side to the coin, and that is to do with confidence in the operating system to keep performing stably in the future. If I am forever going to be anxious about ever upgrading my system again in the future, that's not good for confidence. But do I have a choice in whether to upgrade or not? If I were to re-install everything from the DVD (to revert the system completely back to how it was before today), that's a lot of work (again!), and brings another problem ... when I installed originally, Synaptic Package Manager quickly flagged up a whole series of upgrades, which worked flawlessly. If I re-install now, it will surely upgrade to the current level, i.e. re-introduce all of the same problems. Hence I will be forever discouraged from any future upgrades.

I've only ever used Windows before, but the M$ upgrades don't tend to re-install the kernel, just tweak things about a bit. And you can always revert back to how things were is something goes awry. I don't know of any way of doing that under Ubuntu (which isn't to say there isn't, just that I'm not versed enough to know).

Regards

There is a force in synaptic to revert to whatever worked, and a history of installs. To assume a reinstall will cause the same problems is problematic in that there are way to many varibles when you have over 1200 individual programs, not to mention any add ons from out side or backport repositories. 

The best way to not be scared for me is to use my computer as a OS and store the important stuff on a external HD, then if something goes wrong I have my trusty install CD  to just reinstall nothing is lost, and I know what I need to get it running like I need it to.

The only times I have had problems was when I went wild with the customizations, and or a hardware failure.

---

### Post by wilee-nilee on 2009-11-23
> **Land Rover Series 3 said:**
> Thanks, that's what I'm doing (enabling me to reply to you). Pity that Grub doesn't (afaik) allow me to set a user-defined default boot up though - the one that doesn't work is the default. Will wait to see if Ubuntu fixes this problem.

Regards

startup manager in synaptic allows the chosen startup point.

---

### Post by 73ckn797 on 2009-11-23
I have not performed the update for today but checked what was being offered. I noticed the kernel updates specify (New Install). Did you perform a fresh or upgrade installation? I am assuming the kernels are specific to a new install due to the bracketed comment. See attached screenshot.

---

### Post by seeker5528 on 2009-11-23
> **Land Rover Series 3 said:**
> Fortunately, when I boot up Grub gives me the following 2 main options...

Ubuntu, Linux 2.6.31-15-generic
     (this is the default, and the one that doesn't work)
Ubuntu, Linux 2.6.31-14-generic
     (this still works like a treat, like it always has)

Would really like to be able to (a) preferably, restore the system back to how it was before the upgrade made such a mess of it all, or (b) delete the first option from Grub and tell it to automatically boot up into the old system. Any way of doing either of these, preferably the first?

If this is a wide spread problem, I would expect another update soonish that fixes it, so you might want to wait a couple of days, before you decide to take other measures.

As long as you have linux-image-2.6.31-14-generic to fall back to, linux-image-2.6.31-15-generic can be removed.

Looking at my system there seems to be 3 different metapackages linux-image-generic, linux-generic, and linux-image, which have the same primary function, pull in the preferred default kernel, so you only really need one of these, but on an installed system the only thing you really lose by removing them is automatic update to an updated default kernel that is either a newer series or same series with a different ABI.

Of the above listed metapackages two of them only depend on the current default kernel, but linux-image-generic also depends on the linux-firmware package, so would be the preferred metapackage for most people.

So if you decide to remove linux-image-2.6.31-15-generic, in turn causing the metapackages to be removed, you only need to select linux-image-generic if you see in the forums the problem has been fixed or you want to install whatever happens to be the current default kernel at the time to see if the problem has been fixed.

Later, Seeker

---

### Post by Land Rover Series 3 on 2009-11-23
> **wilee-nilee said:**
> startup manager in synaptic allows the chosen startup point.
I can't see a Startup Manager anywhere in Synaptic.
Where exactly?

---

### Post by Land Rover Series 3 on 2009-11-23
> **73ckn797 said:**
> I have not performed the update for today but checked what was being offered. I noticed the kernel updates specify (New Install). Did you perform a fresh or upgrade installation? I am assuming the kernels are specific to a new install due to the bracketed comment. See attached screenshot.
I was upgrading from a system that was freshly (re-) installed just a couple of days ago, and had already undergone one round of Synaptic upgrades without any issues. I was assuming that if Synaptic were recommending further upgrades that I should go along with it.

---

### Post by Land Rover Series 3 on 2009-11-23
> **seeker5528 said:**
> If this is a wide spread problem, I would expect another update soonish that fixes it, so you might want to wait a couple of days, before you decide to take other measures.

As long as you have linux-image-2.6.31-14-generic to fall back to, linux-image-2.6.31-15-generic can be removed.

Looking at my system there seems to be 3 different metapackages linux-image-generic, linux-generic, and linux-image, which have the same primary function, pull in the preferred default kernel, so you only really need one of these, but on an installed system the only thing you really lose by removing them is automatic update to an updated default kernel that is either a newer series or same series with a different ABI.

Of the above listed metapackages two of them only depend on the current default kernel, but linux-image-generic also depends on the linux-firmware package, so would be the preferred metapackage for most people.

So if you decide to remove linux-image-2.6.31-15-generic, in turn causing the metapackages to be removed, you only need to select linux-image-generic if you see in the forums the problem has been fixed or you want to install whatever happens to be the current default kernel at the time to see if the problem has been fixed.

Later, Seeker
Many thanks for the reply, but you lost me there - hey, I'm a building services engineer, part-time Land Rover mechanic (or at least it always seems that way), and enjoy fishing, so I didn't follow most of what you were saying. I've no idea what a "metapackage" or "ABI" is, but if I've got the general jist of what you're saying...

Will try removing linux-image-2.6.31-15-generic and all its dependencies using the Synaptic Package Manager, and see if that does the trick. If it doesn't, will re-install. Whether or not it works, will wait for some fix.

---

### Post by Land Rover Series 3 on 2009-11-23
> **Land Rover Series 3 said:**
> Many thanks for the reply, but you lost me there - hey, I'm a building services engineer, part-time Land Rover mechanic (or at least it always seems that way), and enjoy fishing, so I didn't follow most of what you were saying. I've no idea what a "metapackage" or "ABI" is, but if I've got the general jist of what you're saying...

Will try removing linux-image-2.6.31-15-generic and all its dependencies using the Synaptic Package Manager, and see if that does the trick. If it doesn't, will re-install. Whether or not it works, will wait for some fix.
P.S. If no one hears from me for a while, my apologies in advance (I'll be offline while busy re-installing again).

Best wishes

---

### Post by bloke-brian on 2009-11-23
Land Rover
I had forgotten that I installed StartUp-Manager.
You can use Synaptic's search box for  startupmanager (no hyphen in its file name).
If it doesn't show, goto Settings -> Repositories and check all except source code. Hit Reload button and search again.

---

### Post by Land Rover Series 3 on 2009-11-23
SORTED!!
I'm still here.

seeker5528 - you're a saviour!

Did what you suggested and it sorted out ALL the problems out in one fell swoop. Used the Synaptic Package Manager to get rid of "linux-image-2.6.31-15-generic" and everything connected with it (full get rid of, not just a partial get rid of), and it worked a treat.

Now when I reboot, it only has one option - the proper working version as the default - and I'm back with a fully-functioning system again! Just love my old Ubuntu!

Many, many thanks

Best wishes

---

### Post by seeker5528 on 2009-11-23
> **Land Rover Series 3 said:**
> I've no idea what a "metapackage" or "ABI" is

It's not critical to know that, the important parts to know were that in this specific situation you could remove the newer kernel package with all it's dependencies as long as you still have the older kernel installed to fall back to and that later when you are ready to try things again you need to install linux-image-generic if you want to get newer default versions of the kernel as intended.

Later, Seeker

---

### Post by Land Rover Series 3 on 2009-11-23
> **seeker5528 said:**
> It's not critical to know that, the important parts to know were that in this specific situation you could remove the newer kernel package with all it's dependencies as long as you still have the older kernel installed to fall back to and that later when you are ready to try things again you need to install linux-image-generic if you want to get newer default versions of the kernel as intended.

Later, Seeker
Thanks again,

Will now continue on my quest to learn the intricacies of Linux and Ubuntu, with new-found confidence (although I have taken the trouble to update my signature in recognition of my recent problems).

---

### Post by Land Rover Series 3 on 2009-11-23
Thanks to everyone who took the trouble to help.

---

### Post by ciiccii on 2009-11-23
I don't think it's the right solution deleting the new kernel package. I get the same blinking screen on every kernel version from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . On the kernles from mainline i can login, but can't mount /home which is encrypted -.-

---

### Post by Land Rover Series 3 on 2009-11-23
> **ciiccii said:**
> I don't think it's the right solution deleting the new kernel package. I get the same blinking screen on every kernel version from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . On the kernles from mainline i can login, but can't mount /home which is encrypted -.-
Well I honestly don't know. All I can say is that by uninstalling the upgraded kernel image it sorted out all of the flashing, non-responding login problems and gave me back a fully operational system without any problems, and made Grub start working again with the operational default.

For more you should seek the advice of someone who knows a lot more about it than me, which seems to be just about everyone.

---

### Post by dcollins on 2009-11-23
I would also like to report that once booting 2.6.31-15, reverting to 2.6.31-14 doesn't work for me.

I've since reinstalled, put the 2.6.31-14 package on hold, and keeping my fingers crossed.

Also, I'd like to follow this issue but could not find the right bug report on Launchpad. If I'm missing something would someone please post a link? Thanks.

---

### Post by Land Rover Series 3 on 2009-11-23
I can't vouch for this because I've never actually used it, but you could check out...

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Hope that might be of some assistance

---

### Post by 73ckn797 on 2009-11-23
> **Land Rover Series 3 said:**
> I was upgrading from a system that was freshly (re-) installed just a couple of days ago, and had already undergone one round of Synaptic upgrades without any issues. I was assuming that if Synaptic were recommending further upgrades that I should go along with it.


I was not sure if what I mentioned was really applicable or not. It was what the Update Manager showed and I was curious whether that could have had something to do with your problem. I update to the new kernel and had no problem on the desktop.

---

### Post by seeker5528 on 2009-11-23
> **ciiccii said:**
> I don't think it's the right solution deleting the new kernel package.

It's not the preferred solution, but in a situation where you booted the older kernel and know it is working, it is the easy solution if you don't want to get bogged down in a bunch of trouble shooting to figure out what is going on.

>  I get the same blinking screen on every kernel version from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . On the kernles from mainline i can login, but can't mount /home which is encrypted -.-

You should probably start a new thread for that, with a title that is more specific to the problem.

Later, Seeker

---

### Post by kestrel1 on 2009-11-24
I have updated my desktop to the latest kernel, but not had any problems with it. I suspect that this could be hardware specific, so what hardware are you running on etc.
If you place a bug report it may be a good idea to include your hardware specs.

---

### Post by yester64 on 2009-11-24
> **Land Rover Series 3 said:**
> Fortunately, when I boot up Grub gives me the following 2 main options...

Ubuntu, Linux 2.6.31-15-generic
     (this is the default, and the one that doesn't work)
Ubuntu, Linux 2.6.31-14-generic
     (this still works like a treat, like it always has)

Would really like to be able to (a) preferably, restore the system back to how it was before the upgrade made such a mess of it all, or (b) delete the first option from Grub and tell it to automatically boot up into the old system. Any way of doing either of these, preferably the first?

Same here. I suspected that it is the gfx driver, but i can't type anything in and so i can only work with the previous version. :(

---

### Post by Land Rover Series 3 on 2009-11-24
> **yester64 said:**
> Same here. I suspected that it is the gfx driver, but i can't type anything in and so i can only work with the previous version. :(
Well, I did a reinstall and it worked flawlessly without the nVidia driver installed first. See my later post...
[http://ubuntuforums.org/showthread.php?t=1336653](http://ubuntuforums.org/showthread.php?t=1336653)

---

