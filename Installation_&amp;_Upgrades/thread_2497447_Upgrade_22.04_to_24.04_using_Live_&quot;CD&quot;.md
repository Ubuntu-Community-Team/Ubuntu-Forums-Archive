---
title: "Upgrade 22.04 to 24.04 using Live &quot;CD&quot;"
date: 2024-05-05
forum: Installation &amp; Upgrades
---

### Post by jbygden on 2024-05-05
I have 22.04 LTS on a machine and I have 24.04 LTS on a USB-drive.
Can I somehow upgrade 22.04 to 24.04 using the USB-drive so I can do some initial tests before the scheduled August 24.04.1 release?

---

### Post by MAFoElffen on 2024-05-05
Are these "initial tests" on a VM or Physical (on your daily driver)? Please answer that question. That does matter in how I answer this.

Not recommended for the general public, but there "are" several ways, that are unofficial and have 'risks'. 

But if for just "tests", which I would suggest doing those tests on a VM... I could share those with you.

---

### Post by yancek on 2024-05-05
Doesn't make much sense to upgrade 22.04 to 24.04 to do tests.  What do you do if the tests you do are not positive and you decide to not upgrade to 24.04.  Not a simple task to go back to 22.04.  Use virtual software as suggested or test with the 'live' install version of24.04 on the usb or boot the 24.04 iso from the hard drive, the 22.04 filesystem from Grub and test that way.  Just put an entry in the 22.04 grub.cfg file to boot the iso, save the change and reboot.  When you have finished your tests, just delete the entry for 24.04 in grub.cfg.

---

### Post by MAFoElffen on 2024-05-05
> **yancek said:**
> Doesn't make much sense to upgrade 22.04 to 24.04 to do tests.
For production servers, you do test migrations in a test environment, to see what the challenges will be in your migrations.

So, in that respect, it does make sense... It would take time to make plans for that. But that purpose is not confirmed.

Though: If this is found to be for personal on physical, then there will be no explanation given that will put that at risk.

---

### Post by jbygden on 2024-05-06
We have some 50+ 22.04 laptops in production at the moment.
There are some applications, both proprietary and publicly available that I need to test before the August release. If you don't understand the need for this, then I can't help you. You clearly don't work in an enterprise environment then...
I could just wipe and re-install the machine I want to test in, but if there is a working upgrade I'd rather do that.

---

### Post by jbygden on 2024-05-06
> **MAFoElffen said:**
> Are these "initial tests" on a VM or Physical (on your daily driver)? Please answer that question. That does matter in how I answer this.

Not recommended for the general public, but there "are" several ways, that are unofficial and have 'risks'. 

But if for just "tests", which I would suggest doing those tests on a VM... I could share those with you.

It's a physical machine, but not my daily driver.

---

### Post by guiverc on 2024-05-06
The Upgrades doc for Ubuntu 24.04 LTS is available at [https://help.ubuntu.com/community/NobleUpgrades](https://help.ubuntu.com/community/NobleUpgrades)

The ISO is intended for new installs, and whilst *non-destructive* re-installs have been available for prior releases, some problems appeared with it with the `ubuntu-desktop-installer` for 24.04 during the QA, thus a FORMAT is *forced* in that circumstance preventing a *non-destructive* (or *unclean*) re-install and forcing a *clean* install.  The *forced* format is visible during install, in that you cannot uncheck the format box (*thus non-destructive install isn't possible*).

The plan is the *fix* this install issue, though new install media won't be provided (*outside of normal .1, .2 etc ISOs*), but as the *installer* is a *snap* package, the installer can upgrade itself & thus have that feature appear when its available. No date on when that will appear has been provided.

Upgrades are not intended to be provided for via USB/FLASH media; but using the internet.

---

### Post by jbygden on 2024-05-06
> **guiverc said:**
> The Upgrades doc for Ubuntu 24.04 LTS is available at [https://help.ubuntu.com/community/NobleUpgrades](https://help.ubuntu.com/community/NobleUpgrades)

The ISO is intended for new installs, and whilst *non-destructive* re-installs have been available for prior releases, some problems appeared with it with the `ubuntu-desktop-installer` for 24.04 during the QA, thus a FORMAT is *forced* in that circumstance preventing a *non-destructive* (or *unclean*) re-install and forcing a *clean* install.  The *forced* format is visible during install, in that you cannot uncheck the format box (*thus non-destructive install isn't possible*).

The plan is the *fix* this install issue, though new install media won't be provided (*outside of normal .1, .2 etc ISOs*), but as the *installer* is a *snap* package, the installer can upgrade itself & thus have that feature appear when its available. No date on when that will appear has been provided.

Upgrades are not intended to be provided for via USB/FLASH media; but using the internet.

Yeah, well, the recommended (and apparently only supported?) way won't be available for 3 months, and I'd like to be able to do some tests before GA of the upgrade procedure.

It would seem I'd have to do "nuke-and-pave"-style re-install to be able to test then...

---

### Post by MAFoElffen on 2024-05-06
Any method I suggested until that is worked out, would not be the 'do-release-upgrade' path that you would need to test the results of... So yes, for your tests, you would need to wait until that release upgrade (path) procedure is released.

Otherwise, you would be comparing apples to oranges. You would be doing tests on something that doesn't exist yet.

You can get there, to 24.04 from 22.04 a few ways, through a 'debian release upgrade method' suggested as an alternative in the Ubuntu Server Guide... But there are risks and problems with making the jump from those, as that technique uses modifications of the sources.list, which between those two releases, the format of those files and where they are located, changes. Not to say it doesn't still work, but there are further things you would need to do.

Also, you are talking about Desktop Edition, and not Server Edition, where there are more changes, than just to the Core system.

Again, even with those understandings, the results of your tests would be on evaluating 24.04 as a system, not on the release upgrade path, so your results would be off. 

Sorry. We are just volunteers here who share our experience with other Users. We do not work for, nor represent Canonical, so we have no control over when then are released, nor written.

With Production Servers, "we" (IT Professionals) do things differently. We do NOT do release upgrades. We do Release Migrations- Where you install fresh, install the services it had, migrate the configurations and data (and adapt them to any changes) to the machine. Then test the results to verify the installation. Everything is in place to do that, and to test that process. That way, you do not carry over anything that is cruff and not needed. It is more like being on a new/fresh install, without any of the risks and problems of a release upgrade process.

When I was in a position similar to yours years ago, we standardized our configurations, and tweaked our configuration management. We did our release upgrades of our laptops and desktops by using our network to deploy new images to our machines. Personal and local data, was isolated from the OS, which made maintenance, disaster recovery, and upgrades easier.

---

### Post by jbygden on 2024-05-06
"Nuke-and-pave" it is then...
Hopefully I'll get to test the upgrade before my users...

---

### Post by yancek on 2024-05-06
My comment above was in response to your initial post which contained very limited information and you had to be asked before you posted information indicating you are referring to a production environment with multiple computers.   Obviously in that situation one should test and even in a pure home computer environment at least, testing a live system.  The point  isn't testing but the method and your initial post seems to indicate you want to upgrade a single computer with 22.04 to 24.04 then test it.

>  I have 22.04 LTS on a machine 

The suggestion in post 9 would seem the best.  Testing with a 'live' system or in a virtual environment might be useful to a limited degree but testing on the actual hardware would be best.

---

### Post by jbygden on 2024-05-06
> **yancek said:**
> My comment above was in response to your initial post which contained very limited information and you had to be asked before you posted information indicating you are referring to a production environment with multiple computers.   Obviously in that situation one should test and even in a pure home computer environment at least, testing a live system.  The point  isn't testing but the method and your initial post seems to indicate you want to upgrade a single computer with 22.04 to 24.04 then test it.
Yeah, well - I have a production environment with some 50+ laptops running 22.04 - hence I want to upgrade a single computer from 22.04 to 24.04 to do tests of both our preferred HW and the corporate apps that's required to be able to use them in our environment.
I don't understand why I need to tell all of you all this to be "permitted" to ask the initial question without being challenged about the necessity in what I'd like to do...

---

### Post by guiverc on 2024-05-06
> **jbygden said:**
> Yeah, well, the recommended (and apparently only supported?) way won't be available for 3 months, and I'd like to be able to do some tests before GA of the upgrade procedure.

It would seem I'd have to do "nuke-and-pave"-style re-install to be able to test then...

The `do-release-upgrade -d` option was available, and will be available again for QA testing.

I'm in a team that performed FOUR **successful** *release-upgrades* on 24-April-2024 just prior to release of Ubuntu 24.04 LTS; that QA upgrade path was pulled down due to users encountering *breakage* and it will be restored once its back to reliable again.

Whilst BLOCKER bugs can be seen on the tracker page ([https://discourse.ubuntu.com/t/noble-numbat-24-04-release-status-tracking/44043](https://discourse.ubuntu.com/t/noble-numbat-24-04-release-status-tracking/44043)) there are more if you search on launchpad  (ie. BLOCKER bugs being the serious bugs). These will be fixed.

When the `-d` will be available again I don't know, but you could always *spoof* the meta development ([https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development)) file so it is *Supported: 1, *but I'm only aware of *non-destructive re-installs  *from installation media (*still available on ISOs using calamares as the installer for 24.04 currently*).

---

### Post by MAFoElffen on 2024-05-06
+1 --

Trust what guiverc says. He didn't blow his cover. He is "way too modest". (Respect) He "IS" the "QA" lead, besides a few other things. When I do ISO testing on what I need to see, the results go to him. 

I might know diagnostics and work around's, because of my testing and me trying to make things work... But he does a lot of work that I don't have the patience for. I deal with Users, and my consultancy customers. I deal with machines and fixing them. He has to deal with DEV's and bureaucracy. I do not envy that at all. Though... He is in the loop for "what is current". Trust what he says implicitly.

---

### Post by grahammechanical on 2024-05-06
The -d switch will upgrade Ubuntu to the development version. Ubuntu 24.04 is no longer a development version. So, it is not possible to use the -d switch to upgrade 22.04 LTS to 24.04 development version. Does the original poster want to upgrade 22.04 LTS to 24.10 development version? I do not think so.

In the past it was possible to re-install packages from the original install medium (CD-ROM or DVD) In fact Software and Updates>Ubuntu software still has an option to do that but on my machine it does not detect the USB stick. Perhaps it is because this install of 24.04 has been converted to 24.10 development version. Perhaps I should be trying this from 22.04 LTS which I do have installed.

I think the the original poster needs to set up off line repositories on the USB stick. 

Regards

Edit: I tried my idea on 22.04 LTS I could not get Software & Updates to see the 24.04 LTS ISO USB stick as an installation medium. Off line repositories might be the way to go.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

See Other Software tab

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by grahammechanical on 2024-05-06
I should of thought of it hours ago. I use a command to change the internet addresses of the Ubuntu repositories to go from the latest version of Ubuntu to the next version of Ubuntu under development. You could use it to change the addresses of the 22.04 repositories (jammy) to the addresses of the 24.04 repositories (noble).

```
sudo sed -i 's/jammy/noble/g' /etc/apt/sources.list
```

Update/Upgrade will bring in the changes. What state your test machine will end in I cannot say. It is your decision.

Regards

---

### Post by MAFoElffen on 2024-05-07
> **grahammechanical said:**
> I should of thought of it hours ago. I use a command to change the internet addresses of the Ubuntu repositories to go from the latest version of Ubuntu to the next version of Ubuntu under development. You could use it to change the addresses of the 22.04 repositories (jammy) to the addresses of the 24.04 repositories (noble).

```
sudo sed -i 's/jammy/noble/g' /etc/apt/sources.list
```

Update/Upgrade will bring in the changes. What state your test machine will end in I cannot say. It is your decision.

Regards
That "IS" know as the 'debian release upgrade method' I mentioned, and gave a warning on... As the format and location of where and how that is done has now changed with 24.04... As I also noted here:
[https://ubuntuforums.org/showthread.php?t=2497343&p=14188379#post14188379](https://ubuntuforums.org/showthread.php?t=2497343&p=14188379#post14188379)

That, at the bottom of that post, is what you would have to change it to once it finishes the updates... Not doing that is one of the things that is broken at the moment in the upgrade path.

---

### Post by jbygden on 2024-05-07
You can stop giving me advice on this now. I have wiped my 22.04 and done a fresh install of 24.04 instead.
Interesting discussion though.
And I keep coming back to the fact that I have to sufficiently *motivate* the reasons for my questions to get your "permission" to ask questions in this forum...
Do you all experienced users in here expect all who asks questions are total newbies and complete morons?

---

### Post by MAFoElffen on 2024-05-07
LOL. You do not need our "permission" to do something. You are really free to do as you please. That is on your own.

I care about Users, and that they are well supported. (You appear to care about your Users. Hats off to that.) I just want you to be aware of the risks, especially since there are problems, which currently there are with that process at the moment, more than on previous releases. On previous releases, you could do 'sudo do-release-upgrade -d' on the day of release, and there were no problems. That is the why of the hesitation.

I would personally feel terrible if I recommended--> Yes, go ahead with this (this way), and then without warning your upgrade is broken... and it was a known problem. You might agree that, you wouldn't be too happy with the results of that. Then you would lose faith in what we say, and in the quality of the release. I do have a sense of responsibility in what I say, and recommend.

You understand that right?

I am not special. I have no ego. I am just another User of Ubuntu here to share experience. I can say, I helped test Noble during it's DEV-Cycle. I think you will be pleased with how it turned out. 

I hope you stick around to share your experiences with it, good or bad. If bad, I hope you take the time to file Bug Reports. Working through those is how we make Ubuntu better for everyone.

Good luck and enjoy.

EDIT -- Idea... Since you do have a professional and personal investment in how this turns out... I personally invite you to be involved with the testing of the upgrade process when that time comes. They are working on it. You do care about how that turns out for your 72 Users... Watch the ["Ubuntu Development Version" Section]("https://ubuntuforums.org/forumdisplay.php?f=427") for that. That might give you a pro-active leg up on your testing.

---

### Post by yancek on 2024-05-07
> Do you all experienced users in here expect all who asks questions are total newbies and complete morons? 

Unless the person posts that information, there is no way to know and many people are.  Your initial post had the sound of a new user as you asked "Can I somehow upgrade 22.04 to 24.04 using the USB-drive so I can do some initial tests".  Of course anyone could do that but you don't ask about the potential consequences or give any information on your situation.  Most of us are not telepathic.

---

### Post by jbygden on 2024-05-08
> **MAFoElffen said:**
> LOL. You do not need our "permission" to do something. You are really free to do as you please. That is on your own.

I care about Users, and that they are well supported. (You appear to care about your Users. Hats off to that.) I just want you to be aware of the risks, especially since there are problems, which currently there are with that process at the moment, more than on previous releases. On previous releases, you could do 'sudo do-release-upgrade -d' on the day of release, and there were no problems. That is the why of the hesitation.

I would personally feel terrible if I recommended--> Yes, go ahead with this (this way), and then without warning your upgrade is broken... and it was a known problem. You might agree that, you wouldn't be too happy with the results of that. Then you would lose faith in what we say, and in the quality of the release. I do have a sense of responsibility in what I say, and recommend.

I'm sorry if I got carried away! But unfortunately that's my experience with asking questions here over the years.
However, I'm quite experienced in dealing with misc problems and if you had answered "Well, I could tell you to do this (with explanation) - but that could, at this moment in the cycle of the upgrading, render your machine unusable due to this and that" Then I could have decided on my own if it was worth it or not.

I don't know if you remember, but you and me had quite the [discussion]("https://ubuntuforums.org/showthread.php?t=2467953") in two different threads a couple of years ago (when I had SSO problems and had to create a different user) about *automating* **Desktop deployment** - My "resolution" in that thread was to go with Debian, but that wasn't acceptable for my company, so we're now installing all our user Ubuntu laptops by hand for now, doing the automation with ansible after install. It's not great, but it works, since we don't deploy that many systems on a daily basis. 

My motives was initially quite heavily questioned then as well...

I've tried asking questions in the discourse and been rather rudely dismissed for trying to accomplish something that seemingly hadn't been thought of...

> **MAFoElffen said:**
> EDIT -- Idea... Since you do have a professional and personal investment in how this turns out... I personally invite you to be involved with the testing of the upgrade process when that time comes. They are working on it. You do care about how that turns out for your 72 Users... Watch the ["Ubuntu Development Version" Section]("https://ubuntuforums.org/forumdisplay.php?f=427") for that. That might give you a pro-active leg up on your testing.

I'll have a look at the Dev Section. Thanks for the tip!

---

### Post by gezzer2 on 2024-05-08
@jbygden
i'm not involved with the discussion but its good to see deployment of Ubuntu to work laptops.

i found that 24.04 had issues on my oldish Dell 13" latitude 3380 (i5 7200u .. 16GB ddr4 .. 275GB SSD)
screen tearing and it looked like under use of the CPU causing everything to just slow down which i believe also impacted the GPU.

i reinstalled 22.04.4 and everything just went back to how it should work. just passing on my personal experience ..

---

### Post by jbygden on 2024-05-08
> **gezzer2 said:**
> @jbygden
i'm not involved with the discussion but its good to see deployment of Ubuntu to work laptops.

You mean you've seen it, or did you misinterpret what I wrote? I haven't seen it yet...

---

### Post by jbygden on 2024-09-05
> **guiverc said:**
> The `do-release-upgrade -d` option was available, and will be available again for QA testing.

I'm in a team that performed FOUR **successful** *release-upgrades* on 24-April-2024 just prior to release of Ubuntu 24.04 LTS; that QA upgrade path was pulled down due to users encountering *breakage* and it will be restored once its back to reliable again.

Whilst BLOCKER bugs can be seen on the tracker page ([https://discourse.ubuntu.com/t/noble-numbat-24-04-release-status-tracking/44043](https://discourse.ubuntu.com/t/noble-numbat-24-04-release-status-tracking/44043)) there are more if you search on launchpad  (ie. BLOCKER bugs being the serious bugs). These will be fixed.

When the `-d` will be available again I don't know, but you could always *spoof* the meta development ([https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development)) file so it is *Supported: 1, *but I'm only aware of *non-destructive re-installs  *from installation media (*still available on ISOs using calamares as the installer for 24.04 currently*).

MAFoElffen says you're the QA-lead. I've now tried the upgrade with 24.04.1.
This problem is back: [https://www.reddit.com/r/linux4noobs/comments/151elkx/dell_latitude_7430_has_severe_ui_lag/](https://www.reddit.com/r/linux4noobs/comments/151elkx/dell_latitude_7430_has_severe_ui_lag/) - with a vengance...
It's even in the boot-image of 24.04.1 (which means even the Live Image is unusable), so installation on a Dell 7430 is more or less impossible without an external monitor to run on instead of the built-in screen of the Laptop.
(Before anyone asks: Yes I tried the upgrade first, but I lost my network during it so I had to re-install from a USB-stick)
How did that get past QA?

And to those of you who wondered WHY I wanted to do testing before release - this is why...
Now I *know* this when my users start upgrading, and I can warn them and have them apply the "fix" *before* they run the upgrade.
Fortunately I found the ```
/etc/update-manager/release-upgrades
``` and could "push" a ```
never
``` to that file using ansible to avoid users doing the upgrade until I'd sorted this out.

---

