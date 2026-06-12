---
title: "Bad Upgrade on a 12.04 to 12.04.4"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by sirwizkid on 2014-04-09
Hi All,
I did a HES (Hardware Enablement stack) upgrade, that hung on the flash upgrade.  It was hung bad (Almost a day) so I finally had to kill it.  So it didn't complete all it's magic and cleanup, configure etc.  I got the system back up, had to reinstall grub, pull hair out, futz with package repair's, Kick the computer, cursed at Shuttleworth, etc.  I found that my network manager no longer works, and I've had crash reports from several apps.

Are there any tools that can go and figure out what's not complete, and give me a hint on what I can work on to straighten out anything that's broken.  I don't mind loosing network manager, but what else is broken?  I don't know yet.

I am up and running, but I question how stable it is.
  Thanks

---

### Post by Kirboosy on 2014-04-10
Welcome to the forums! :D

What kind of hardware is this running on? What did you do to get the box back to a semi usable state? The more details you can provide for us the better.

Hope that helps!
~Caboose

---

### Post by sirwizkid on 2014-04-11
I'm on a intel box.
System Information
        Manufacturer: Gigabyte Technology Co., Ltd.
        Product Name: Z68X-UD3H-B3

The box is semi-usable.  Seems like everytime I do something I get pop ups to report bugs.  It's very annoying.  I tried reloading policykit this morning, and a few other things.  My vpn didn't work (found out that was a new option on encryptfs).  Parts of the upgrade have worked.  

I did find the right distupgrade logs.  I just grabbed the list of everything it said it was going to upgrade, and started off a apt-get with the big list of files.  We'll see what happens.

---

### Post by Kirboosy on 2014-04-14
Any update on this issue?

---

### Post by sirwizkid on 2014-04-14
I manually installed the packages listed in the original install, and the system, for the most part has stabilized.  The only thing I found that wasn't working is the network manager.  For now, I've manually added my missing second IP on the box.

---

