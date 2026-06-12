---
title: "[lubuntu -&gt; fedora] error: you need to load kernel first"
date: 2023-01-21
forum: Installation &amp; Upgrades
---

### Post by leoxavi3r on 2023-01-21
[IMG]https://i.ibb.co/Jm4h4wb/Whats-App-Image-2023-01-21-at-13-49-57.jpg[/IMG]
img1

Hi

Help to boot my fedora37-kde usb?
cause dont recognize (img1)

just a grub screen after Esc (img2)

[IMG]https://i.ibb.co/3FyMTTy/Whats-App-Image-2023-01-21-at-13-49-58.jpg[/IMG]
img2

i have this one 

Apple MacBook "Core 2 Duo" 2.4 (Black-08)
Identifiers: Early 2008 - MB404LL/A - MacBook4,1 - A1181 - 2242

yesterday i tried use
lubuntu®&#65039; 22.04.1 LTS (Jammy Jellyfish)

but a lot of snap errors and others
so today i want to try fedora kde

would you help me?
cause i cant load bootable usb

here's usb identified:
Bus 002 Device 002: ID 0951:1642 Kingston Technology DT101 G2

partitions:

/dev/sdb1 (img3-4)

[IMG]https://i.ibb.co/42tRLzX/particao.png[/IMG]
img3
[IMG]https://i.ibb.co/vzQr4bx/particao2.png[/IMG]
img4

i mount this bootable disk in another windows 7 desktop
like when i mount lubuntu

this is a screenshot of usb "inside" (img5)
[IMG]https://i.ibb.co/Vxbb2KG/pasta-pendrive.png[/IMG]
img5

but now i cant load
there's a grub or kernel unload that dont recognize usb
it makes sense?
srry poor english i'm brazilian ok

so i tried some tutorials and codes
but back some errors (imgs6-8)

take a look and help me, pls?

[IMG]https://i.ibb.co/d2TyrBS/Whats-App-Image-2023-01-21-at-13-31-40.jpg[/IMG]
img6
[IMG]https://i.ibb.co/4mBpBcY/Whats-App-Image-2023-01-21-at-13-49-59.jpg[/IMG]
img7
[IMG]https://i.ibb.co/KFWX7X9/Whats-App-Image-2023-01-21-at-13-49-59-1.jpg[/IMG]
img8

So,
where's wally?

---

### Post by guiverc on 2023-01-22
Fedora isn't Ubuntu (*or flavor like Lubuntu is*), so you're asking in the wrong place for Fedora support.  I'd suggest reading the Fedora documentation on downloading an ISO, validating it, then writing it to media.

The *snap error* on Lubuntu makes me wonder if you were using *optical media* such as a DVDr/rw for installation, as *optical* media is not intended for installation of any release later than Ubuntu 20.04 LTS (or Lubuntu 20.04 LTS with *flavors* like Lubuntu) as the *timeouts *that can occur during media scan are wrongly recognized as other errors. If were you using *optical *media, thus thread maybe helpful - [https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246](https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246) but do note, Yes it's possible to still install from DVD; but the install can take more than an hour, and it may take more than 3 installs before you have a working system.  Using USB *flash* media is just far easier & is expected for any release of Ubuntu 20.10 or later.

---

### Post by leoxavi3r on 2023-01-22
> **guiverc said:**
> Fedora isn't Ubuntu (*or flavor like Lubuntu is*), so you're asking in the wrong place for Fedora support.  I'd suggest reading the Fedora documentation on downloading an ISO, validating it, then writing it to media.

The *snap error* on Lubuntu makes me wonder if you were using *optical media* such as a DVDr/rw for installation, as *optical* media is not intended for installation of any release later than Ubuntu 20.04 LTS (or Lubuntu 20.04 LTS with *flavors* like Lubuntu) as the *timeouts *that can occur during media scan are wrongly recognized as other errors. If were you using *optical *media, thus thread maybe helpful - [https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246](https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246) but do note, Yes it's possible to still install from DVD; but the install can take more than an hour, and it may take more than 3 installs before you have a working system.  Using USB *flash* media is just far easier & is expected for any release of Ubuntu 20.10 or later.

Sorry.

---

### Post by guiverc on 2023-01-22
Your Fedora issue is likely related to the ISO & write of ISO to media, at least that's my guess (*why I suggested reading Fedora documentation on writing an ISO to media*).

I have a system here with Fedora 37 on it, but I'm also very aware there are many types of ISO files, and how they get written to media varies greatly, and I can't recall how Fedora was written to thumb-drive, and what software/options were required, thus my suggestion to follow the documentation appropriate to it  (Ubuntu documentation assumes Ubuntu or *flavor* of Ubuntu which are all of the same ISO type).

Opening up a Fedora ISO written to thumb-drive will look I'd bet identical if written to ISO correctly, or incorrectly, as the only difference is the correctly written ISO will boot, where as the incorrectly written will not be bootable.

---

