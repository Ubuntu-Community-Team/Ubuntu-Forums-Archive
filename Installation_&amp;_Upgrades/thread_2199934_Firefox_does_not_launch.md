---
title: "Firefox does not launch"
date: 2014-01-16
forum: Installation &amp; Upgrades
---

### Post by lz1dsb on 2014-01-16
I'm running Firefox version 25 and I've noticed lately that it does not launch! The only way to solve that is to reboot the whole system. This has worked several times, but it's quite frustrating.
Now, when I click on the Firefox icon, it starts flashing and than - nothing. Checking the started processes shows that there is a firefox process running, but it's in weird states like "sleep", "unix_wait_for_peer" etc.
Has anyone encountered this?

---

### Post by papibe on 2014-01-16
Hi lz1dsb.

Do you have plugins installed? I would start by disabling all plugins, and enable them one a time to check stability.

Another approach is to get yourself a clean start by [reseting Firefox to its default state]("https://support.mozilla.org/en-US/kb/reset-firefox-easily-fix-most-problems") (clearing profile).

You may loose your bookmarks, so you may need to backup them ([export]("https://support.mozilla.org/en-US/kb/export-firefox-bookmarks-to-backup-or-transfer")) before the reset, and then [restore]("https://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them") them.

Hope it helps. Let us know how it went.
Regards.

---

### Post by ajgreeny on 2014-01-16
Just rename the hidden .**mozilla** folder in your home to .**mozillabak** and restart FF, but don't delete that folder; you will probably want a lot of the data in it and you can copy back a lot of it later bit by bit, once you've got FF running again.

---

### Post by lz1dsb on 2014-01-17
> **papibe said:**
> Hi lz1dsb.

Do you have plugins installed? I would start by disabling all plugins, and enable them one a time to check stability.

Another approach is to get yourself a clean start by [reseting Firefox to its default state]("https://support.mozilla.org/en-US/kb/reset-firefox-easily-fix-most-problems") (clearing profile).

You may loose your bookmarks, so you may need to backup them ([export]("https://support.mozilla.org/en-US/kb/export-firefox-bookmarks-to-backup-or-transfer")) before the reset, and then [restore]("https://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them") them.

Hope it helps. Let us know how it went.
Regards.

I think you're absolutely correct about this. Yes, I do have plugins installed. Not many, but I have some. By accident yesterday I noticed that my digital signature reader gets stuck when I don't use it for some time. And this only happens when it's connected to a USB hub I use (most likely the USB hub has some issues). Why this concerns Firefox? Well, because I have a plugin for my e-banking. So, the pattern matches. When I reboot everything is initialized, the USB reader for my digital signature is plugged in and works. I start Firefox - no issues. After some time, the USB hub maybe fails: I noticed that when this happens even if I plug it off, I can still see it and every USB device that was previously connected to it in the lsusb output. And at that point when I try to launch Firefox - it fails. Today I tried using my USB reader for the digital signature directly connected to a USB port - no issues with Firefox! Works as it's supposed to :guitar:

---

