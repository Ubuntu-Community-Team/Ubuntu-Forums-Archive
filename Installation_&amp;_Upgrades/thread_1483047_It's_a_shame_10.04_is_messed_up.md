---
title: "It's a shame 10.04 is messed up"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-05-14
They know there's an issue with the BSOD. I had a perfectly running 9.1 system. I loved it. Al I used it for was Internet & mail. The only changes I made were
1. Gnome PPP
2. wvdial
3. network administrator
4. remove modemmanager
5. Thunderbird & Firefox from Ubuntuzilla.

I did an upgrade with the Alternate CD. All went well and after 6 hours all I had to show was a BSOD.
It did the fixmbr in the windows repair console and deleted ubuntu. I'm now back to windows. I left the partition were Ubuntu was installed so that I can try again if it's ever fixed. I have a Dell lappy.

---

### Post by kansasnoob on 2010-05-14
> I did an upgrade with the live CD. 

How do you do that :confused:

---

### Post by darkod on 2010-05-14
Not all upgrades go smooth and you don't have to even upgrade if used only for internet and mail. 9.10 is supported for another 12 months.

Also, if you literary use it only for internet and mail, why not clean install of 10.04 instead of upgrade? It's always a better option. And because it's LTS it will be supported for 3yr so once you set it up how you like it, you don't have to think about upgrading or installing a new version for years.

---

### Post by El Zoido on 2010-05-14
Hm, I'm running Ubuntu 10.04 on two different machines right now and it works great.
Only thing I do have problems with so far is Ubuntu One which seemingly was reverted back to alpha. ;)

One thing I would try is simply reinstall Ubuntu and see if it works.
First time I installed Karmic the installation got for some reason completely messed up and nothing would work. Reinstalling fixed it.

Oh, and I moved the windows buttons to the right. Doesn't make sense to me to put them on the left in an LTS version without the accompanying indicators (or whatever they plan to do) for the right parts of the window.

---

### Post by darkod on 2010-05-14
> **kansasnoob said:**
> How do you do that :confused:

+1

You can't upgrade with the live cd.

---

### Post by yota on 2010-05-14
Upgrading from optical media is **not** recommended and should be considered only when no internet connection is available.
Moreover upgrading from the live cd is totally unsupported, probably you have just installed 10.04 on top of 9.10 mixing the two.

Here are documented the endorsed upgrade paths: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
You should have read the fine documentation before jumping to the conclusion that 10.0.4 is a mess... (even better would have been to read them before peforming the upgrade).

Anyway sorry for the unpleasant experience.

---

### Post by darkod on 2010-05-14
> **yota said:**
> Upgrading from optical media is **not** recommended and should be considered only when no internet connection is available.

On a separate note, why is this? I always thought it's better to download the image first separately because even if your internet connection stalls, no harm done.

If you run into connection problem during online upgrade, who knows what will come up.

Not to mention that for more computers you download the image only once (and it's smaller, 700MB while people have reported 999MB upgrade download size), which might make a difference if your internet is not unlimited.

---

### Post by yota on 2010-05-14
> **darkod said:**
> On a separate note, why is this? I always thought it's better to download the image first separately because even if your internet connection stalls, no harm done.


The network upgrade downloads everything that is needed to perform the whole upgrade before starting the process. So if there is a connection problem simply the upgrade stops without any harm (but leaving all the downloaded material in a temporary cache so one can start exactly were it left).
We can say that, actually, the package installation is done off-line.

Other than this there are a bunch of advantages which are difficult to summarize, I'll put the first that are caming to mind:
[LIST]
[*]via network you get the latest packages, with all bugfixes (potentially avoiding already resolved showstoppers)
[*]you upgrade all packages you installed (also those that are out of the base distribution and cannot fit the dvd, let alone the cd) with specific regard of the universe repository
[*]the network upgrade is an actual system upgrade, the cd upgrade is more like an install of a set of newer packages on top of the older ones
[*]if the machine is a server the network upgrade produces much less downtime (hopefully! ;-) ) since most services can stay up for at least a part of the process
[*]if you consider cd download+offline upgrade+package update (once the system is restarted) versus network upgrade usually you save band with the latter 
[/LIST]

Surely many other considerations can be done and as always "your milleage may vary", but network upgrade has its strengths.

---

### Post by Silvertones on 2010-05-14
Typo.
I used the Alternate CD.
I only have dialup and didn't want to sit at the library for 6+ hours.
I wanted to UPDATE because doing the dialup connection & Samba was a PIA. Now I'm at square one so I'll suffer with Windows until the CD I ordered from Canonical comes in the mail then I'll do a fresh install.
BTW this issue with the BSOD is a known bug with some cards. Unfortunately I discovered the work around too late. Oh well!!!

---

### Post by wkulecz on 2010-05-14
> I had a perfectly running 9.1 system. I loved it

If it ain't broke, don't fix it!

If you can't backup (rsync and an external usb drive are your new best friends) you must ask yourself before upgrading:

What does the new do that I can't do with what I have?

What is removed from the new that I need and use in the old?


Playing with every upgrade can be fun, but if you need to actually use your system, unless there is something new you need and can't get with the old the best you can hope for is some time wasted doing an upgrade and being where you are now with some different for the sake of being different issues to deal with.  Worst case, you've already experienced -- you get hosed.

---

### Post by Silvertones on 2010-05-14
You are right. I'm reinstalling 9.1 now and will leave it there for another year.

---

