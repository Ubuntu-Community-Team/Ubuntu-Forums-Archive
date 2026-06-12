---
title: "Lubuntu on a N150 old Netbook"
date: 2020-06-24
forum: Installation &amp; Upgrades
---

### Post by bernd67 on 2020-06-24
Hello Forum,

i have an old N150 .. and wanted to install a Linux on it, i did choose Lubuntu,
downloaded 32 bit Version 18.04 i assume and tried to install via usb stick..
i did choose install and let run...
errors:
capb namespace lookup failure, ae already existing
error methos parse/executetion failed \_sb.pcio._oscc nodef4485300 ae already exists 2016930/psparse-543
and some more device descriptor read/64, error-110
usb usbi-port 7 unable to enumerate usb device..
(initramfs)

there is  windows (starter i think) on machine installed... but can be eleminated.
bernd

---

### Post by GhX6GZMB on 2020-06-24
From where did you get the install image? [www.lubuntu.me](www.lubuntu.me) is the correct site.

---

### Post by bernd67 on 2020-06-24
maybe a problem with the stick.. i just installed linuxmint, using another stick.. similar error messages but now installed and working..
maybe will give lubuntu another chance if time...:>) thx

---

### Post by GhX6GZMB on 2020-06-24
The N150 has an Intel Atom N450 which supports the amd64 instruction set.
No reason to choose 18.04, go directly to Lubuntu 20.04 LTS.

---

### Post by bernd67 on 2020-06-24
Thx for Info, will check!!!

---

### Post by guiverc on 2020-06-24
I'll provide the following manual links for Lubuntu

[https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)

I would ensure as @ml9104 suggested, you get it from the correct web site (there a number of sites offering Lubuntu for download found using search engines, search engines are out of Canonical/Ubuntu's & Lubuntu team's control, so if unsure which is correct, use ubuntu.com instead of a search engine (ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) will send you to the official web site for each Ubuntu flavor).

Probably of more significant is did you verify the ISO you downloaded? You'll find that referred to in the manual (some download methods do it automatically, ie. I trust `zsync` inbuilt check usually). 

Secondly and more importantly is verifying the write to your install media (ensure a good write, valid image on the thumb-drive). This is the step I have most problem with. It's the "***Check disc for defects***" option in the first screen-image found on the [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html) manual page. I consider it a must as it ensures the ISO was written correctly.  On releases before 20.04 (ie. 18.04) it's a manual step, but on 20.04 media which uses it by default the line no longer appears on that menu.

(if it fails on one box, I'll maybe boot it on another to try and verify it there; if it fails on both, I assume it's a bad write to installation media[*thumb-drive*] & return to prior checksum validation & re-write to media..)

That "***Check disk for defects***" option takes at most a minute, but saves hours-days of trouble-shooting problems which is where you were. Successfully installing something else (Mint) is likely proof it was a faulty write (*assuming similar software stack, though  not conclusive though*)

---

### Post by ActionParsnip on 2020-06-25
If you try a different USB stick is it better?

---

### Post by bernd67 on 2020-06-25
Hey, cool! its running as you did tell me.. exactly, Lubuntu 20.04 LTS - 64 Bit.
starting nees some time but if started its faster as expected.

how can i get a program symbol in task bar and on desktop, is there a beginners guide for lumbuntu as i expect?
there have been still some error messages while installing, but its running..
error like:
errir ae not found while resolving... ..sdpkginit...
error aborting methos sb.pcio...
update request io error dev..
squashfs error unable to red fragment cache..failure creating named object...
failed to start show plymouth reboot screen
..
--

---

### Post by CelticWarrior on 2020-06-25
[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

---

### Post by GhX6GZMB on 2020-06-25
On a fresh Lubuntu install, all programs are in the application menu (lower left corner). If you want program icons on the desktop, just drag them there from the menu.
To enable them you'll need to right click on the desktop icons and tick "Trust this executable". For icons in the task bar same thing, but you need to find a place on the taskbar where you get a green mouse symbol (usually on top of another icon). You can reorder the icons afterwards.
Tip: don't mess with the default icons in the task bar, you'll need them at some point.

---

### Post by bernd67 on 2020-06-25
oki, found that ..is there a way that application is starting via desktop without beeing prompted a second time..

---

### Post by GhX6GZMB on 2020-06-25
> **bernd67 said:**
> oki, found that ..is there a way that application is starting via desktop without beeing prompted a second time..


You forgot the step: right click on desktop icon and tick "Trust this executable". This will also remove the exclamation point on the icon.

---

