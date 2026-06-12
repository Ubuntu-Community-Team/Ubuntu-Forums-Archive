---
title: "New install of Ubuntu 18.04 freezes before log in"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2018-08-15
I downloaded the Ubuntu 18.04 ISO using torrent.  However I also checked the hash (SHA256SUM) just to be sure.  I then created a USB flash drive (using Startup Disk Creator) as well as a DVD using (Xfburn).  I tried to install 18.04 to my test desktop using the created flash drive and then the DVD.  In both cases after the installation and reboot, the system froze just before the log in image appeared.  I tried several other flash drives with the same result.  Not to be out-smarted by a machine, I downloaded Lubuntu, Xubuntu, Kubuntu, Ubuntu Mate, and Ubuntu Budgie and placed them on USB flash drives.  To my surprise, each installed and rebooted as expected.  When Ubuntu 18.04.1 became available I downloaded it and tried again with the same result, a frozen screen after installation and reboot just before the log-in image.  Is this a bug.

I am not sure if it makes any difference.  The computer is not EFI.

---

### Post by oldfred on 2018-08-15
If computer is not UEFI, then over 5 years old.
So how much RAM and what video card/chip?
What brand/model system, some need boot parameters.

But full Ubuntu is now really for newer systems as GUI needs better gpu and system.
The others you installed except maybe Kubuntu are lighter weight configurations that work better on limited systems.

---

### Post by Rex Bouwense on 2018-08-15
Yes the computer is over ten years old.  It is merely a test machine to check install media prior to our LoCo installfests.  It currently has Ubuntu 16.04.5 installed and is functioning fine.  If it installed and rebooted Kubuntu which is just as robust (if not more so) as Ubuntu and functioned fine shouldn't have done the same with the mother distro?

Dell OptiPlex GX620
Memory 2GB
Processor:  Intel Pentium (R) 4 CPU 3.20 GHz x2
Graphics: Intel 945G

While it is nice to install to newer computers, some of the machines that we install a Linux system on belong to people who for some reason do not want to buy a newer computer or cannot afford one.  Until the release of 18.04 this was possible.  Something has changed.  We can still install one of the other five "flavors".

---

### Post by Rex Bouwense on 2018-08-21
After some additional research, I discovered that Ubuntu 18.04 comes with a new (and heavier) login display manager, gdm3, replacing LightDM which was used in 16.04.  Older machines may not be able to load the new login display manager.  The solution was install LightDM and make it the default login display manager.  See [https://unix.stackexchange.com/questions/446119/the-difference-in-ubuntu-18-04-that-requires-nomodeset/447707#447707](https://unix.stackexchange.com/questions/446119/the-difference-in-ubuntu-18-04-that-requires-nomodeset/447707#447707).  That enabled the machine to boot Ubuntu 18.04 normally.

---

### Post by jmr3 on 2018-10-17
I just had a similar problem on an old Dell GX520.  Ubuntu would start but the screen froze and I could not even switch to a text VT.
I fixed it by editing /etc/gdm3/custom.conf and uncommenting the line:
```
WaylandEnable=false
```

Then,
```
systemctl restart gdm
```

Of course, to do this you have to access the system, possibly by starting in rescue mode (text-only).

I hope this helps.

João Rodrigues

---

### Post by Rex Bouwense on 2018-10-18
Thanks jmr3.  The same response was offered to my question in launchpad [https://answers.launchpad.net/ubuntu/+source/lightdm/+question/672572](https://answers.launchpad.net/ubuntu/+source/lightdm/+question/672572).  It works fine with that edit as well.

---

### Post by AnupamMitra on 2018-10-21
[QUOTE=Rex Bouwense;13809527]Thanks jmr3.  The same response was offered to my question in launchpad [https://answers.launchpad.net/ubuntu/+source/lightdm/+question/672572](https://answers.launchpad.net/ubuntu/+source/lightdm/+question/672572).  It works fine with that edit as well.[/QUOTE

I'm also suffering with the same problem with one of my Pcs. I followed your earlier suggestion given herein:  [https://unix.stackexchange.com/quest.../447707#447707]("https://unix.stackexchange.com/questions/446119/the-difference-in-ubuntu-18-04-that-requires-nomodeset/447707#447707").  

More or less now it boots normally, but not as usual. A terminal opens automatically, something going on and finally it starts. However, my earlier problem of freezing before log in is over.

Further, I also want to know what you have stated two days ago. Would you please elaborate step by step so that I can reach to uncomment the line "WaylandEnable=False" in the "/etc/gdm3/custom.conf" .

---

