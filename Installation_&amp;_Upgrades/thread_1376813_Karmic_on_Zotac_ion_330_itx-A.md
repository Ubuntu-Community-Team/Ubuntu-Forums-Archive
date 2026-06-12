---
title: "Karmic on Zotac ion 330 itx-A"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by martron88 on 2010-01-09
I've been trying to install karmic from a usb key onto a new zotac ion 300 itx-A board and can't get into the liveCD to test things out.

The system boots to the install menu and when I select "Try Ubuntu..." the system hangs on a blinking cursor.  This also happens if I choose the "safe graphics" mode.

Selecting "Install Ubuntu" has the same result.

I recently used the same usb key to install karmic onto my laptop so I know it works.

Searching for "karmic zotac ion" has led me to some posts about xorg not loading but that's after the initial install process and also on an alpha version of Karmic (I'll burn that bridge when i get to it).  Others seem to have had no problem getting karmic installed.

I've also tried mythbuntu and 64-bit jaunty with the same results.

Is there any way I can find out what's causing this hang?  I can't get into a console or anything...

Thanks

---

### Post by phillw on 2010-01-09
> **martron88 said:**
> I've been trying to install karmic from a usb key onto a new zotac ion 300 itx-A board and can't get into the liveCD to test things out.

The system boots to the install menu and when I select "Try Ubuntu..." the system hangs on a blinking cursor.  This also happens if I choose the "safe graphics" mode.

Selecting "Install Ubuntu" has the same result.

I recently used the same usb key to install karmic onto my laptop so I know it works.

Searching for "karmic zotac ion" has led me to some posts about xorg not loading but that's after the initial install process and also on an alpha version of Karmic (I'll burn that bridge when i get to it).  Others seem to have had no problem getting karmic installed.

I've also tried mythbuntu and 64-bit jaunty with the same results.

Is there any way I can find out what's causing this hang?  I can't get into a console or anything...

Thanks

Hi, with the caution you noted about xorg, my instinct would be to try with the alternate install (the text based one) --> [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

You'd need to post what video driver you have & check to see if it is supported 'out of the box' or you need to issue a command at boot-up time.

Regards,

Phill.

---

### Post by martron88 on 2010-01-09
I tried out the alternate installer to no avail, the same problem occured, however, I noticed that the usb key light turned off when the hang occurs. So I went snooping around in the BIOS for usb configurations and there's an "EHCI Handoff" setting which I set to disabled.  And voila, now Ubuntu boots to the installer!

---

