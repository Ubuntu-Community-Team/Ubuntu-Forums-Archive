---
title: "Common Problems / Frequently Asked Questions About Testing"
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-12-01
Here are answers to some commonly asked questions and solutions to common problems when testing pre-release Ubuntu versions. It will be updated during the testing period as necessary. Feel free to post suggestions for things that you think should be included (I won't promise to include them all, since making the document unnecessarily long typically discourages people from reading). 


**I already have a testing installation. Do I have to reinstall the latest alpha / beta?**

If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the beta, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix.

The milestone releases (alphas, betas and the RC) are slightly stabilized snapshots of the package archive at pre-decided dates, so they reflect the latest state of Lucid on those dates. If you're up to date, you already have the latest packages. If you have to reinstall, and have an old disc image, you may want to [use rsync]("https://wiki.ubuntu.com/RsyncCdImage") to avoid having to download the whole image.

**If I install the alpha / beta / RC now, do I need to reinstall the final version when it's released? **

You don't have to (Update Manager will let you upgrade to the final version), but you may want to, if one or more of the below apply:

[list]
[*] You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 


[*] You have replaced essential components of your installation with versions from external repositories / PPAs


[*] You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community


[*] You have applied hacks / workarounds for testing purposes for good reason (prompted during structured testing, bug triage etc.), which may cause problems during daily usage of a stable installation


[*] You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes)
[/list]

**Update Manager offers a "Partial Upgrade". What should I do?**

[Read this]("http://ubuntuforums.org/showthread.php?t=1343434").

**When / at what time will the alpha / beta / RC be released?**

Take a look at [the release schedule]("https://wiki.ubuntu.com/LucidReleaseSchedule"). There's no specific time of the day for releases; just wait for the official release announcement, which will be mirrored immediately in the forum with a sticky thread as well.
 
**I'm trying to report a bug, but I'm redirected to [this page]("http://help.ubuntu.com/community/ReportingBugs"). What's going on?**

That's intentional; you'll understand what's going on once you read that page :)

**I'm trying to report a bug, but I don't know which package it belongs to. What should I do?**

Take a look at the [Bugs/FindRightPackage page on the wiki]("wiki.ubuntu.com/Bugs/FindRightPackage"), and try invoking Apport's (currently rather primitive) symptom-based reporting mode by issuing ```
ubuntu-bug
``` with no arguments. If those don't help, feel free to start a thread, or join the #ubuntu-bugs channel on [the Freenode IRC network]("help.ubuntu.com/community/InternetRelayChat") to ask for assistance.

**My testing installation is badly broken. Is there a way to roll back to the stable release, or a relatively stable point in the development branch?**

No. You'll have to fix your installation or do a fresh install.

**I haven't been getting updates for a while. Is it that there's nothing new in Lucid, or is there a problem with the servers?**

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors). Also note that there will be relatively few updates during the freeze periods leading to alpha, beta and RC releases.

**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**

The daily images get built automatically, and due to the rapid and asynchronous nature of uploads to Lucid, no effort can be made to make them fit on a CD on a daily basis; such an effort is only made for the milestones. Note that you can still use oversized CD images for testing in a virtual machine.

**Is testing Lucid in a virtual machine useful?**

For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing bug reports from virtual machine installs, don't forget that they will be reports about Ubuntu failing to work on that particular virtual machine, and don't forget to indicate that you're testing on a virtual machine in your bug report. While virtual machines are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level functionality such as userspace applications, user interfaces, documentation, translations and so on, virtual machines are mostly fine.

---

### Post by VMC on 2009-12-01
Very thorough. Another answer to this FAQ, "**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**", might be to suggest using a DVD. In fact I only use DVD-RW's until the final release.

Now if we had all the answers to Booting issues, all would be well :)

---

### Post by Gina on 2009-12-02
DVD+RWs are slightly quicker because the don't need erasing.  And DVDs have a higher data transfer rate than CDs so they are quicker generally.  

Incidentally, I use K3b to burn them, I've found it the most reliable and has an option to check the data written if you want.

+1 On the booting issues.

---

### Post by Arlanthir on 2009-12-03
> **VMC said:**
> Very thorough. Another answer to this FAQ, "**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**", might be to suggest using a DVD. In fact I only use DVD-RW's until the final release.

Now if we had all the answers to Booting issues, all would be well :)

Or using a USB stick? I don't usually have problems that way :)

---

### Post by XubuRoxMySox on 2010-01-06
I so very much wish I could help test Lubuntu and Xubuntu Lucid! My bandwidth allowance is so limited I would be "FAPped" (_F_air _A_ccess _P_olicy violation) from Day One. I've already gotten in trouble with my ISP for "distro hopping" last year...

I can only be a cheerleader for the projects, I'm afraid, but I want you devs and testers and artists and translators and packagers and maintainers to know that we appreciate you!! Thank you sooooo very much for the amazing work you unsung heroes put into making the Ubuntu family such an awesome distro!

One of your biggest fans,
Robin

---

### Post by MikeDK on 2010-02-18
What is this thing with the removal of gnome-volume-control from system tray?

this is really annoying.
running lucid from alpha1 x64 and a few days ago its no longer available in repos.

kind regards mikedk

---

### Post by uncleV on 2010-02-20
Decided to try the Lucid.

It's stupid and may be I'm stupid, but didn't find any clue here in the forums **where to download Lucid from?**
Thank you in advance!

May be you should put this question as FAQ?

---

### Post by darkstaar on 2010-02-20
> **uncleV said:**
> ...**where to download Lucid from?**...

Here's a link to the Alpha 2 page:
[http://www.ubuntu.com/testing/lucid/alpha2]("http://www.ubuntu.com/testing/lucid/alpha2")

---

### Post by uncleV on 2010-02-20
Thank you darkstaar!

Downloaded LiveDVD.

---

### Post by IanW on 2010-02-20
Perhaps the current Plymouth vs Xorg "Press enter to freeze your system" bug should be mentioned as a common problem here?

---

### Post by Silvestro Fantacci on 2010-02-21
Would it be better to install the latest milestone release (currently [Alpha 2]("http://cdimage.ubuntu.com/releases/lucid/alpha-2") of 13-14 Jan) or the latest [Daily Build]("http://cdimage.ubuntu.com/daily-live/current") (currently 21 Feb)?

---

### Post by darkstaar on 2010-02-21
Generally speaking, milestone releases are deemed to be more stable than daily builds.

That said, what's "better" for one user may not be better for another with different hardware.

There's really no 'correct' answer to your question.

---

### Post by SoftwareExplorer on 2010-02-28
> **dixiedancer said:**
> I so very much wish I could help test Lubuntu and Xubuntu Lucid! My bandwidth allowance is so limited I would be "FAPped" (_F_air _A_ccess _P_olicy violation) from Day One. I've already gotten in trouble with my ISP for "distro hopping" last year...

I can only be a cheerleader for the projects, I'm afraid, but I want you devs and testers and artists and translators and packagers and maintainers to know that we appreciate you!! Thank you sooooo very much for the amazing work you unsung heroes put into making the Ubuntu family such an awesome distro!

One of your biggest fans,
Robin
Maybe zsync would help? It lets you download only the changes from the previous version of the image that you have.

---

### Post by Cr0n_J0b on 2010-04-19
Couple of notes that I didn't find very clear anywhere.

1) when Installing Lucid. To access the special boot options, hit [esc] key when you see the intial logo.  This should be make clear with text.
2) There are some issues with screen refresh while using VNC and nVidia drives.  You need to turn off Compbiz and and all visual effects.  This has been a reported bug since Karmic.
3) dmraid is the new management interface for raid type devices.  This changes a lot of things including device names and can break raid sets.  I suggest that if you have existing raid sets, use the nodmraid option during installation.
4) I suggest that you always burn the ISO to a DVD and install from there.  I have found nothing but frustration with installing ubuntu from CD.

thanks.

---

### Post by rzstarpaw on 2010-04-24
Was wondering if anyone else had problems post install. Well I installed 10.04 RC and then my Laptop freezes during the first reboot. Has anyone else have this issue?

Specs: Gateway 7320GZ
Intel 4 2.8
Ram 1GB
HD: 80GB

---

