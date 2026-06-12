---
title: "Should Lucid be shipped with GRUB2 or revert to GRUB1?"
date: 2010-01-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kevpatts on 2010-01-13
My vote is for GRUB1 cause GRUB2 is not stable. Ubuntu is supposed to be easy to use but GRUB2 buggered up so many peoples installations that the Ubuntu guys surely, to keep to they're underlying ethos, have to ditch it until it's more mature and stable ... **especially for an LTS release.**

---

### Post by Leppie on 2010-01-13
if you read the documentation grub2 isn't that difficult to understand. furthermore it has a powerful os prober which can be run whenever you want and i haven't found in grub legacy.

---

### Post by mk1w86 on 2010-01-13
I think by the time Lucid is released any major Grub2 problems will have been fixed and I am guessing most problems with grub2, correct me if I'm wrong, were caused by upgrading from grub-legacy.  Also if they released Lucid with Grub-legacy it would probably cause problems for people upgrading from Karmic with Grub2 installed.:-s

---

### Post by Cheesemill on 2010-01-13
I think that one of the main reasons the they shipped Karmic with Grub2 still in beta was to get any bugs ironed out **before** Lucid, rather than shipping an LTS with an untested Grub2.

---

### Post by darkod on 2010-01-13
> **kevpatts said:**
> My vote is for GRUB1 cause GRUB2 is not stable. Ubuntu is supposed to be easy to use but GRUB2 buggered up so many peoples installations that the Ubuntu guys surely, to keep to they're underlying ethos, have to ditch it until it's more mature and stable ... **especially for an LTS release.**

With all the respect, most "buggered up" cases I've seen here were by the user rather than grub2. Maybe because I have single drive setup, but both on my netbook and desktop ubuntu 9.10 and grub2 played together great with win7. And I've never even seen ubuntu before, I started using it when 9.10 came out.
But I did have knowledge about partition because even for windows I want to control my own partition sizes. So without any doubt, I used manual partitioning for ubuntu during the install.

---

### Post by presence1960 on 2010-01-13
:popcorn:

Human nature is to resist change. When we get uncomfortable the first thing a lot of us do is want to revert back to the old rather than invest our energy in learning the new way.

Legacy GRUB is so outdated and hasn't been upgraded in a long time. It may seem "easier" or "better" now because a lot of us are familiar with it. But it is now time to bury GRUB 0.97 for new versions going forward with 9.10

I have 3 internal disks and an USB external. I have had up to 4 Linux OSs and XP multibooting with not so much as a skipped beat with GRUB2.

Everything in this world is either growing or dying. GRUB 0.97 is dying. Embrace GRUB2 and learn about it.

P.S. A lot of people told me not to use Sabayon Linux that it is a pain to install and configure. Well just that made me do it anyway. I have been using Sabayon for over a year now. Glad I didn't listen to those who said it was too hard. When I installed it I found out that they meant it is "different", not hard. It was a major adjustment because it is based on Gentoo. But I began to learn how to use it and still am. Actually in some respects it is faster than Ubuntu. Faster opening browsers with or without compiz, compiz effects way faster and crisper than in Ubuntu. Had to learn the whole Package Manager and command line installs but will not get rid of it because it works great! Just my two cents.

---

### Post by kevpatts on 2010-01-13
I have to disagree with a few points made here, from personal experience:

> **mk1w86 said:**
> I am guessing most problems with grub2, correct me if I'm wrong, were caused by upgrading from grub-legacy.

I have two machines that were unbootable after an upgrade from Intrepid/Jaunty, both because of GRUB2. I tried to then install a fresh copy of Karmic onto both and neither worked with GRUB2 (one had fakeraid and the other was a macbook pro, both of which worked with GRUB1).

> **mk1w86 said:**
> Also if they released Lucid with Grub-legacy it would probably cause problems for people upgrading from Karmic with Grub2 installed.

I doubt it. GRUB1 supports ext4 now. There should be no major obstacles with downgrading.

> **Cheesemill said:**
> I think that one of the main reasons the they shipped Karmic with Grub2 still in beta was to get any bugs ironed out before Lucid, rather than shipping an LTS with an untested Grub2.

This is what Alpha and Beta releases are for. If there were serious bugs still in the software at the time of major release, which there definitely were, it should not have been included in the final version. I could understand if this was a bug in an app, but in such a critical system component, I think it was careless/reckless.

As most server ubuntu installations are running the last LTS release and will be upgrading directly to Lucid (and these are the most critical installations not to bring down) I think it should be canned, from the server release at least, until it's more stable.

> **darkod said:**
> With all the respect, most "buggered up" cases I've seen here were by the user rather than grub2. Maybe because I have single drive setup, but both on my netbook and desktop ubuntu 9.10 and grub2 played together great with win7.

Both my systems were upgraded by simply doing a distribution upgrade through the updage GUI. I wouldn't call that user error! And in fairness, if they released it with bugs for single drive setups they should be shot! Luckily they're not that bad.

---

### Post by kevpatts on 2010-01-13
> **Leppie said:**
> if you read the documentation grub2 isn't that difficult to understand. furthermore it has a powerful os prober which can be run whenever you want and i haven't found in grub legacy.

Sorry, forgot to comment on this. This was not my point at all! I don't agree that GRUB2 **will be** a huge step forward, but it's not ready.

---

### Post by kevpatts on 2010-01-13
> **presence1960 said:**
> :popcorn:

Human nature is to resist change. When we get uncomfortable the first thing a lot of us do is want to revert back to the old rather than invest our energy in learning the new way.

Legacy GRUB is so outdated and hasn't been upgraded in a long time. It may seem "easier" or "better" now because a lot of us are familiar with it. But it is now time to bury GRUB 0.97 for new versions going forward with 9.10

I have 3 internal disks and an USB external. I have had up to 4 Linux OSs and XP multibooting with not so much as a skipped beat with GRUB2.

Everything in this world is either growing or dying. GRUB 0.97 is dying. Embrace GRUB2 and learn about it.

P.S. A lot of people told me not to use Sabayon Linux that it is a pain to install and configure. Well just that made me do it anyway. I have been using Sabayon for over a year now. Glad I didn't listen to those who said it was too hard. When I installed it I found out that they meant it is "different", not hard. It was a major adjustment because it is based on Gentoo. But I began to learn how to use it and still am. Actually in some respects it is faster than Ubuntu. Faster opening browsers with or without compiz, compiz effects way faster and crisper than in Ubuntu. Had to learn the whole Package Manager and command line installs but will not get rid of it because it works great! Just my two cents.

I take your point, but Ubuntu is not a testing platform, by it's essence it's not supposed to difficult to use/install/upgrade.

---

### Post by elliotn on 2010-01-13
> **kevpatts said:**
> My vote is for GRUB1 cause GRUB2 is not stable. Ubuntu is supposed to be easy to use but GRUB2 buggered up so many peoples installations that the Ubuntu guys surely, to keep to they're underlying ethos, have to ditch it until it's more mature and stable ... **especially for an LTS release.**

For me grub2 is working good except that its slow but it does all I want

---

### Post by presence1960 on 2010-01-13
> **kevpatts said:**
> Both my systems were upgraded by simply doing a distribution upgrade through the updage GUI. I wouldn't call that user error! And in fairness, if they released it with bugs for single drive setups they should be shot! Luckily they're not that bad.

I don't doubt your sincerity. But have you read the number of threads at every release about how dist-upgrades have a whole lot of problems, even before GRUB2.

In my opinion dist-upgrades are the lazy way out to avoid perceived work. But in reality they cause so many problems that the assertion they are easier is circumvented. There is a way to have all your packages except those compiled or from third party software restored to a clean install. I have used it successfully on my machine, my daughter's machine & many clients machines. Here is the link: [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

I have taken note of all those threads and will never do a dist-upgrade. I can have my clean install up & running in the same amount of time or less than it takes to complete a dist-upgrade. A wise person learns from not only the success of others but also from their failures.

---

### Post by mk1w86 on 2010-01-13
> I have two machines that were unbootable after an upgrade from Intrepid/Jaunty, both because of GRUB2.

How could Intrepid to Jaunty upgrade problems be caused by Grub2? :confused: If however you meant you upgraded from Jaunty to Karmic, it keeps grub-legacy unless you specifically install Grub2.  Grub2 is only installed with Karmic when you do a fresh installation.

> I tried to then install a fresh copy of Karmic onto both and neither worked with GRUB2 (one had fakeraid and the other was a macbook pro, both of which worked with GRUB1).

> As most server ubuntu installations are running the last LTS release and will be upgrading directly to Lucid (and these are the most critical installations not to bring down) I think it should be canned, from the server release at least, until it's more stable.

Although it doesn't necessary excuse the Grub2 problems you're having many 'mission critical' server installations will not be using fakeraid or be running on macbook pro's. :biggrin:

> This is what Alpha and Beta releases are for. If there were serious bugs still in the software at the time of major release, which there definitely were, it should not have been included in the final version.

Going back to the thread title, remember Lucid still *is* alpha software and Karmic is not an LTS release so is less likely to be running in mission critical enviroments. :-s

:popcorn:

---

### Post by SuperSonic4 on 2010-01-13
> **presence1960 said:**
> :popcorn:

Human nature is to resist change. When we get uncomfortable the first thing a lot of us do is want to revert back to the old rather than invest our energy in learning the new way.


Amarok 2.X and KDE 4.X come to mind immediately.


I think grub2 should be embraced, keep marching on with technology. Too many people see Linux as being stuck in the 80s

---

### Post by wkulecz on 2010-01-13
> Amarok 2.X and KDE 4.X come to mind immediately.

Amarok 2 is so different from Amarok 1.4 it shouldn't share the name.  Different is not better, better is better.  Amarok 2 on 9.10 I find simply obnoxious forcing crap in my face that I don't want! I uninstalled it within seconds of opening it the first time after one look at all the crap I didn't want.

If KDE 4.x is the future, Windows 7 is looking a lot better all of a sudden.

Nobody gives a rat's *** about the boot loader until it breaks,  Use the search, Grub2 breaks alot and the information on how to fix it is just not readily available at present.

I resisted the move from lilo to Grub for the very reason I'll resist the move to Grub2  Better the devil you know than the devil you don't!

I mean just when I'm confident I can solve any Grub issues that may come up, bang everything I know is wrong because Grub2 is somehow better, WTF?

For every system the OS prober is a win for I'm sure there are ones its a loss for, like mine where partitons that hold old OSes I was testing should be ignored instead of adding to the boot menu.  If I want to boot them easy enough to do with Grub, but Grub2 seems so complex you need a prober program to add a new boot entry.  This is progress??

--wally.

---

### Post by presence1960 on 2010-01-13
> **wkulecz said:**
>  Better the devil you know than the devil you don't!

I mean just when I'm confident I can solve any Grub issues that may come up, bang everything I know is wrong because Grub2 is somehow better, WTF?


Therein lies the crux of the problem. people are lazy & don't want to learn new things. They stubbornly cling to old things that may serve them ok because they understand them, but at the same time refuse to keep an open mind & a willingness to advance their own knowledge.

The "devil you don't know" is unknown because you refuse to get to know it. If you don't strike up a conversation with that devil soon you may soon find yourself with no one to converse for the "devil you do know" will be leaving us soon and will not be returning.

Here is a quote from I don't remember whom: There is a principle that is a bar to all information & will forever keep a man in everlasting ignorance. That principle is contempt prior to investigation.

---

### Post by Leppie on 2010-01-13
> **kevpatts said:**
> Sorry, forgot to comment on this. This was not my point at all! I don't agree that GRUB2 **will be** a huge step forward, but it's not ready.
i've seen quite a lot of grub issues in the last couple of weeks. i can't say that grub2 doesn't mess up (because it seems that sometimes a clean install results in a mix of grub legacy and grub2), however most of the issues are caused by wrong usage (directly or indirectly).
for example, one of the most common issues seems to be that people install ubuntu first and then install some version of windows. while grub2 is installed, they will try to restore the mbr using grub legacy instructions. i don't think that such issues can be attributed to grub2 being too immature for production.

---

### Post by Leppie on 2010-01-13
> **wkulecz said:**
> For every system the OS prober is a win for I'm sure there are ones its a loss for, like mine where partitons that hold old OSes I was testing should be ignored instead of adding to the boot menu.  If I want to boot them easy enough to do with Grub, but Grub2 seems so complex you need a prober program to add a new boot entry.  This is progress??
grub2 is not so complex that you need a prober program to add a new boot entry. the exact same message about not editing the grub.cfg is also displayed in the menu.lst. however, whereas grub2 offers an easy way to add the menu entry to the grub menu for a newly installed os on your system, grub legacy doesn't. just run update-grub and you're done, without messing around with the config file. and **that is** progress

---

### Post by warfacegod on 2010-01-13
> How could Intrepid to Jaunty upgrade problems be caused by Grub2? If however you meant you upgraded from Jaunty to Karmic, it keeps grub-legacy unless you specifically install Grub2. Grub2 is only installed with Karmic when you do a fresh installation.

This not necessarily true. I did an upgrade install on my laptop from 9.04 - 9.10 just before i did a clean install. I also did an upgrade install on my wife's desktop from 8.10 - 9.10. In both cases, GRUB was replaced with GRUB2 and it did it with *no* notification. I was totally unaware of the change until after rebooting. In the desktop upgrade, GRUB2 was so hopelessly fragged that I didn't even bother fixing it. I simply swapped out the drive with a back up I'd made the day before and then did a fresh install on the fragged drive.

Personally I don't give a damn about GRUB and neither should the Ubuntu staff. There are still far and away too many people having huge problems with wireless cards, video cards (especially ATi, Intel), sound not working, Java, Flash, printers, cameras, etc., etc., etc., etc., etc. It took me almost two years from 7.04 - 8.10 before I was comfortable enough with Linux to get my wireless card working and working well. Then in 9.04 my wireless is perfect, I don't have to do a thing. Yeah! In 9.10 however my signal strength in down 20%, what the hell?!

And I don't want to hear the same old story about manufacturers not supporting Open Source because it's bulls#!t. Report me for abuse if you like but it's true! I can understand newly released hardware but say, video cards that are three years old, it's an excuse and a cop out. The average user doesn't want to, nor should they have to, spend hours or days doing obscure things to his/her computer while reading through some mystical set of instructions to do it, just to be able to watch youtube.

The bottom line is this. Cannonical is biting off more than they can chew with each release. Trying to change this, improve that, replace, switch and upgrade. Ubuntu S.C. is a prime example; it doesn't work! Cannonical is promising or at least implying things with their O.S.es to average users that they are not delivering on. They need to throttle back on quantity and start working on quality.

---

### Post by Mark Phelps on 2010-01-13
Adding my 2-cents ...

Linux in general, and Ubuntu specifically, are targeted at a community of folks that WANT to learn HOW to use computers. I didn't join this community because they offered a free version of MS Windows (which they don't); I joined this community because they offered a free ALTERNATIVE to MS Windows.

While I agree that the early versions of GRUB2 were problematic, as I experienced this myself when I upgraded my Jaunty install to use GRUB2, since I've installed GRUB2 afresh with Karmic, I've had absolutely no problems with it.

And, mostly through reading posts in THIS forum, I've learned how to customize my GRUB2 booting far beyond what I was able to do with GRUB1. So, for me, the upgrade has been an overwhelming success.

But then .. I'm not an supporter of the point-and-click crowd and don't shy away from learning scripting or other forms of programming when that brings with it new features and capabilities.

So, my vote is to press on with GRUB2 (and other such advancements).  If the result is that folks have to learn something technical, then they need to decide whether they want to stay in THIS community, or go back to the point-and-click crowd.

---

### Post by phillw on 2010-01-14
> **Mark Phelps said:**
> Adding my 2-cents ...

Linux in general, and Ubuntu specifically, are targeted at a community of folks that WANT to learn HOW to use computers. I didn't join this community because they offered a free version of MS Windows (which they don't); I joined this community because they offered a free ALTERNATIVE to MS Windows.

While I agree that the early versions of GRUB2 were problematic, as I experienced this myself when I upgraded my Jaunty install to use GRUB2, since I've installed GRUB2 afresh with Karmic, I've had absolutely no problems with it.

And, mostly through reading posts in THIS forum, I've learned how to customize my GRUB2 booting far beyond what I was able to do with GRUB1. So, for me, the upgrade has been an overwhelming success.

But then .. I'm not an supporter of the point-and-click crowd and don't shy away from learning scripting or other forms of programming when that brings with it new features and capabilities.

So, my vote is to press on with GRUB2 (and other such advancements).  If the result is that folks have to learn something technical, then they need to decide whether they want to stay in THIS community, or go back to the point-and-click crowd.

+1

Being one of those who missed a 'little' step in updating from grub 0.97 --> grub 1.97beta - I learned a lot (Like read the instructions, although they have been amended since my goof-up, to stop others)
grub 1.98 has now got a lot of the RAID stuff in it, and that is one we're 'playing' with over on 10.04. 1.97beta isn't being 'played' with - as it is production release and the devs cannot risk breaking it whilst trying to improve it.
That is what is happening regards to the LTS. People wanting raid and talking about LTS, should be on 8.04.3 (soon to be 8.04.4) in readiness for the option to upgrade to 10.04.

I went 9.04 --> 9.10, then grub 0.97 --> grub 1.97beta, then ext3 --> ext4 Painlessly and with no data-loss (Which only happens when you have a backup), except for my goof up on the grub one.

Regards,

Phill.

---

### Post by slakkie on 2010-01-14
> **kevpatts said:**
> My vote is for GRUB1 cause GRUB2 is not stable. Ubuntu is supposed to be easy to use but GRUB2 buggered up so many peoples installations that the Ubuntu guys surely, to keep to they're underlying ethos, have to ditch it until it's more mature and stable ... **especially for an LTS release.**

Only because of the last sentence: Grub-legacy is UNsupported and there is NO active development. So for an LTS release they should ship with grub2 because of this fact. 

Plus, Debian Testing uses grub2 so a sync with Debian is going ahead with grub2. There is no going back, grub2 is coming and start to get used to it :)

---

### Post by audiomick on 2010-01-14
Grub2, but do everything possible to make it as stable as possible first.

---

### Post by TheWanderingMaverick on 2010-01-16
Right now, gurb2 is (obviously) in BETA stage, so there are still bugs in it. The decision to include it in the next distro should be based upon the readiness and stability of the program.

---

### Post by warfacegod on 2010-01-16
> **TheWanderingMaverick said:**
> Right now, gurb2 is (obviously) in BETA stage, so there are still bugs in it. The decision to include it in the next distro should be based upon the readiness and stability of the program.

I think Cannonical dodged a cannon shell when they shipped an OS with a beta stage boot loader. There could easily been far more issues than there were. Not that there weren't allot. Just look at all the fragged Wubi installs that came up over the last week.

---

### Post by raymondh on 2010-01-16
Legacy or GRUB2, it does **not** matter to me.   I will be using Lucid and I'm looking forward to it.  If it comes with GRUB2 and I encounter issues, I'll just have to deal with it.  

If I paid canonical for an OS, then I'd expect canonical to give me a hassle-free OS.   

Just my opinion.

Raymond

---

### Post by kansasnoob on 2010-01-16
> My vote is for GRUB1 cause GRUB2 is not stable.

In what way is it unstable?

OK, there's been a recent Wubi bug, but it really is a Wubi bug more so than a grub2 bug.

Multiple drives can be troublesome but that was also true of legacy grub. If someone has multiple drives you'd think they'd do some research ahead of time and make sure things are cabled right (ie: master/slave/sata1/sata2, etc), bios is set right, and they'd use all advanced options in the installation to be sure both the OS and grub2 are installed in the proper location.

Outside of that there are some corner issues where grub2 just doesn't seem to work well. I don't know why (I suspect BIOS issues) but those who encounter an issue where grub2 won't work with their hardware need to file bug reports and then the devs can investigate.

Finally for those who need or just prefer legacy grub I wrote this to make it easy to revert (or vice versa):

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I might also mention that grub2 in Lucid is currently:GNU GRUB 1.98~20100101-1ubuntu2. No more Beta :P

One final observation. Having mixed legacy grub and grub2 files in the /boot/grub directory messes things up. It keeps Startup Manager from performing properly in either version, it can effect boot times, and it prevents os-prober from properly updating grub2.

It's easy to check, just run the command "ls /boot/grub" and look to see if it has both a "grub.cfg" and a "menu.lst". If so you need to start a fresh directory and totally reinstall whichever grub you're going to use.

I multi-boot six operating systems and I love grub2 now. The only actual modification I make anymore is to omit the memtest option. Otherwise Startup Manager does everything I need other than occasionally removing an old kernel using Synaptic.

If one of my other OS's has a kernel update I need only run "sudo update-grub" in the controlling OS and there's the new kernel, no editing a menu.lst :)

---

### Post by warfacegod on 2010-01-16
> **raymondh said:**
> Legacy or GRUB2, it does **not** matter to me.   I will be using Lucid and I'm looking forward to it.  If it comes with GRUB2 and I encounter issues, I'll just have to deal with it.  

If I paid canonical for an OS, then I'd expect canonical to give me a hassle-free OS.   

Just my opinion.

Raymond

People pay Microsoft everyday and look at what they get. We don't pay Cannonical and yet, as a whole, we get far fewer problems.

---

### Post by Genius314 on 2010-01-16
The version of Grub2 that shipped with Karmic didn't detect my copy of Windows 7.
But after an update, it detected it right away. I think most of the bugs are getting fixed, and will probably be gone by the time Lucid is released.

---

### Post by Zoot7 on 2010-01-16
GRUB2 is actually much more easy to use than GRUB 1 IMO. Two commands and I'd Debian booting 5 other OS's along with itself.

---

