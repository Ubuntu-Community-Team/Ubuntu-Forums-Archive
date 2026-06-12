---
title: "Xubuntu install hangs at 85% &quot;Installed xubuntu-desktop&quot;"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by tylersticka on 2007-04-22
I have a secondary laptop I use for academic work, word processing and web browsing. It depends on a wireless connection, so although I'm not an "early adopter," I couldn't resist upgrading to "Feisty Fawn" after hearing of its improved out-of-the-box wifi capabilities.

The machine is 933mHz, 128mb, 20gb HDD and has been running Edgy for months. Because of it's amount of RAM, I am using the Alternate Xubuntu install CD.

Things were going fine until 65% into the "Select and install software" step. I killed the "anthy" configuration using the method from [this thread]("http://ubuntuforums.org/showthread.php?t=293514") and it started chugging along as it previously had.

Unfortunately, at 85% of "Select and install software" I see "Installed xubuntu-desktop" and it just hangs. The CD isn't spinning, the hard drive isn't working, it's like it isn't doing anything. I can press Alt+F2 and back again, and it reacts promptly and fine.

The first time this happened I just rebooted and tried again. The second time, I tried a similar process as the anthy method mentioned below, and although I could view the ID number, attempting to kill returned an error that process didn't exist, almost as if it disappeared upon my looking for it. Nonetheless, no perceptible changes occurred and I had to reboot again.

Any help you might be able to volunteer would be appreciated. Thanks in advance!

---

### Post by tylersticka on 2007-04-22
(bump)

Perhaps I should do a clean install of Edgy, then upgrade to Feisty?

Any suggestions from anyone?

---

### Post by Benitez on 2007-04-23
> **tylersticka said:**
> (bump)

Perhaps I should do a clean install of Edgy, then upgrade to Feisty?

Any suggestions from anyone?

[SIZE="3"]
Try this: [Minimal CD Installer]("https://help.ubuntu.com/community/Installation/MinimalCD").

You will need fast, constant access to the internet though in order to do it; I have a feeling it is quite heavy on the servers though, so maybe your best bet *might* be to do an install of Feisty from scratch...

Lemme know how it works...
[/SIZE]

---

### Post by tylersticka on 2007-04-23
I didn't want to use the minimal CD because there's not a pre-baked Xubuntu version, and while I know that you can change it to Xubuntu after installation, I seek the squeeky-clean freshness of a clean install.

Just to get it back to where I had it, I attempted to use my Edgy Eft install CD, when it had the same problem!

I knew then that it was my issue, not the install CDs. The only thing I had changed was the addition of a wireless card, so I figured it had something to do with that. Sure enough, when I plugged an Ethernet cable directly into my laptop and chose it as my primary means of connectivity, installation went smoothly.

So, I'm now running Feisty Fawn, and so far I am impressed! This thing just keeps getting better. Thanks for your suggestion; my guess is my wireless network was just being finicky.

---

### Post by beep1314 on 2007-07-26
I have the same problem.  My first install of xubuntu 7.04 went great except for having to kill anthy.  But I reinstalled (clean install) to correct a problem with acpi=force and now the install hangs at 85% "Installed xubuntu-desktop".  Toshiba 2595CDT laptop 64mbs ram.

Any hints?

---

### Post by prober8 on 2007-09-14
Happened to me too. On a Samsung SENS laptop with P3 750MHz and 192 MB of memory. Here's what I did.

[LIST=1]
[*]pressed "alt + F2" similar to the anthy thread. This switched me to a console.
[*]"ps"
[*]I looked for some process to kill like apt-get update. I am not expecting any internet update at that time. I am not even connected to the network. So I thought it was safe to kill it.
[*]after killing it pressed alt + F1 to go back to the installation process. It already continued with the installation.
[/LIST]

This worked for me. I hope this helps or works for others. :)

---

### Post by doanotherlinux on 2007-09-28
I'm having a similiar problem with my Xubuntu.  I installed a few days ago and when my add/remove files menu froze I restarted the computer.  When it restarted it kept telling me about an error with apt-get not being installed.

I did a reinstall and it keeps sitting forever at 85%  I let it sit for a half an hour or so and finally it continues.  But after it finishes with the install and restarts it tells me how apt-get is not installed.

Any suggestions?

---

### Post by lowracer on 2007-12-21
I had the same problem installing Feisty from the alternate CD... Hung at 85%.  Doing the Alt F2 and killing the apt-get update process resumed the install...

Now here's the thing that's going to nag me for awhile, keeping me awake nights.

What harm did this do?  Will I have a botched install in some way that will come back to bite me later?

---

