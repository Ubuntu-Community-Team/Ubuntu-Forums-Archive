---
title: "Dual Boot 18.04 i386 and 18.04 amd64"
date: 2022-03-23
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2022-03-23
I have one old system originally installed as 32 bit. It has been upgraded over the years and finally when I get to 18.04 I have not more upgrades. I tried to install 18.04 amd64 into a different partition and it seemed to work for a while, but now the 64 bit install won't boot. I can get to the grub menu and select it but I get kernel panics almost immediately. I've worked on it but can't get to boot. I'm going to try reinstalling over the existing install. Is there anything I should be aware of?

---

### Post by guiverc on 2022-03-23
If your machine can boot an *amd64* ISO and install from it; it should run the system fine.

You've provided no specifics though as to what 18.04 system you were using. I was involved with QA (*Quality Assurance*) testing with *flavors* of Ubuntu which meant I was using *i386* ISOs into the 19.04 or *disco* cycle (as 18.10 & 19.04 were not LTS releases; 18.04 LTS was the last with supported *i386*) and thus my last QA work with *i386* was in [August 2020]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/").

I did encounter some old IBM Thinkpads that booted older kernels perfectly, including up to 5.3 or 18.04.4, but had issues with the 20.04 kernel found i 18.04.5 with HWE enabled. The easy fix for those devices was to install with older media (ideally 18.04 or 18.04.1 that defaults to GA), but HWE media with older stacks (18.04.2-18.04.4) but disallow upgrades until you've switched to the GA stack, then perform all upgrades.  Some of those boxes experienced kernel panic, but they were *i386[I] CPUs only *[/I](early pentium M, ~2003) and were incapable of booting any *amd64* ISO so this may not be your issue; but still maybe your *workaround*.

You provided no details of your hardware either.

I'd treat it as I would any system that kernel panic'd, or suffered a power-outage.  I'd boot *live* media & file-system check, explore the file-system & look for clues. But to me the required details are what Ubuntu 18.04 system ISO did you use?  

Did you validate it prior to write to media? and validate the write to your media? (*or confirm no errors occurred during install; esp. squashfs*) as the normal pre-install checks are really just cheap insurance (*taking a max of minute or two, compared to the hours-days of fixing problems like what you're describing*). Documentation exists on performing these checks, but I don't know which applies to you as you didn't provide product/ISO specifics.

FYI:  I still use my *i386* installs of Ubuntu Desktop with my files intact.  I'm a desktop user, and it's rather easy to re-install a desktop system (including switching from *i386* to *amd64*) without loss of files, and having your additional packages (if from Ubuntu repositories) re-install automatically, but my last *i386* install was likely 11.04, 11.10 or around that era, so I can't say I've done it recently. Those systems are 20.04 & 21.10 now & *flavors* instead of main Ubuntu.

---

### Post by rsteinmetz70112 on 2022-03-24
Unfortunately I don't recall the 18.04 iso I used I use the Ubuntu generic kernel. As for hardware that shouldn't be an issue since I have other computers with virtually identical hardware happily running 20.04 LTS. Since I can boot the i386 I have used that to file check the file systems, that's the system I'm running on a day to day basis, but I need to move to amd64. The initial install of i386 worked for a while, but at some point it became unbootable and I can't figure out what happened so I'm going to reinstall.

---

