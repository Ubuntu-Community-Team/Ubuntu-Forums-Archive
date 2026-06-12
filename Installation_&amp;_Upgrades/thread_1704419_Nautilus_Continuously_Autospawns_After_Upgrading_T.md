---
title: "Nautilus Continuously Autospawns After Upgrading To 2.31.1 From PPA"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by hayhursm on 2011-03-10
I upgraded Nautilus from 2.30.0 to 2.31.1 in Ubuntu 10.04 using **ppa:am-monkeyd/nautilus-elementary-ppa.  **After I rebooted my PC the processor shot up about 80% and a bunch of Nautilus windows began to open on my taskbar; I also noticed that all of my Desktop icons (Trash, Computer, Network Servers) had disappeared.  Of course, using the command "sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa" fixed the problem but I would really like to use the new version of Nautilus.  Does anyone know of a fix for this problem?

---

### Post by Frogs Hair on 2011-03-10
I have been using that PPA on 10.04 and 10.10 without the slightest problem . Do you have a lot of PPAS ? the only thing can think is a possible conflict with another PPA or it did not install correctly . It may be worth another try .

---

### Post by hayhursm on 2011-03-10
> **Frogs Hair said:**
> I have been using that PPA on 10.04 and 10.10 without the slightest problem . Do you have a lot of PPAS ? the only thing can think is a possible conflict with another PPA or it did not install correctly . It may be worth another try .


What do you consider to be too many PPA's?  I currently have 13 PPA's (including the Nautilus PPA).  I just tested this PPA on a second PC running Ubuntu 10.04 (with same PPA's) and it works just fine so far.  Hmmmmm... now I'm stumped, do you think it's a dependency of some sort?

---

### Post by hayhursm on 2011-03-11
> **Frogs Hair said:**
> I have been using that PPA on 10.04 and 10.10 without the slightest problem . Do you have a lot of PPAS ? the only thing can think is a possible conflict with another PPA or it did not install correctly . It may be worth another try .


I GOT IT!!  First, I decided to give this another try so I re-activated the PPA and then installed again but still no luck.  I decided to purge the PPA once again but noticed this:
[B]Suggested packages:
  gnome-app-install[/B]
The following packages will be DOWNGRADED:
  libnautilus-extension1 nautilus nautilus-data

After purging the PPA I decided to install **gnome-app-install**.  After that I re-activated the PPA yet again and issued a **"sudo apt-get update && sudo apt-get dist-upgrade"** and PRESTO, Nautilus 2.31.1 worked!!  It's strange the **gnome-app-install **package is listed under **Suggested Packages **when it is actually **REQUIRED** for the upgraded Nautilus to function???  These little set backs are frustrating but at the same time one always learns something new.

---

### Post by Frogs Hair on 2011-03-11
Glad it's working , I have only NE installed twice , once 10.04 and once on 10.10 and I did not see anything like you described . I just installed the PPA and ran nautilus -q and never looked back.

---

### Post by hayhursm on 2011-03-22
> **Frogs Hair said:**
> Glad it's working , I have only NE installed twice , once 10.04 and once on 10.10 and I did not see anything like you described . I just installed the PPA and ran nautilus -q and never looked back.

I apologize but I must reopen this thread.  I'm 100% sure I've narrowed this problem down to having multiple monitors.  I thought the **gnome-app-install **fixed my problem but it turns out I just had my second monitor disabled.  I can recreate the autospawn problem by enabling and disabling my secondary monitor so I'm 100% sure this is causing it.  When the secondary monitor is enabled then Nautilus will continuously autospawn and not work.  It seems odd that a second monitor would cause this but I'm sure there's some explanation for it.

---

### Post by hayhursm on 2011-03-24
Can anyone help me out?

---

### Post by hayhursm on 2011-04-17
Can anyone help me out...surely I can't be the only one with dual monitors experiencing this?

---

### Post by hayhursm on 2011-06-09
Bump

---

