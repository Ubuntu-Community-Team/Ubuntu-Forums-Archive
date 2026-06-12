---
title: "Boot issues, need help ASAP!"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by JARRODIUS on 2012-11-13
I downloaded Ubuntu 12.10 last night off USB drive, and installed it from said USB to my desktop last night. Now when I go to start the computer, it needs to boot off the USB, how can I get it to boot off the harddrive? :(

---

### Post by stevedude on 2012-11-13
This is just a guess, but what is your computer's BIOS set to boot from?

There is typically a boot order in the BIOS setup that tells your system to boot from a Hard Drive, CD/DVD ROM Disk, USB, etc. Try entering your BIOS (which varies with each system so if you don't know, try doing an Internet search for it. Typically F2 key, or Delete key, sometimes Insert key, etc)

Change the boot order so the Hard Drive is set to boot before the others.

---

### Post by westie457 on 2012-11-13
@ JARRODIUS
Welcome to the Fora.

If 'stevedude's advice does not work for you then try this.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that does not work either then post the url you will be given so we can see what is going on with your set up.

Thank you

---

### Post by JARRODIUS on 2012-11-13
The BIOS doesn't have an option to boot from the hard drive. I've tried setting it up so that it could and gone through all the options but my hard drive doesn't show up as a boot device. currently attempting boot repair...

---

### Post by JARRODIUS on 2012-11-13
update, still can't get it to boot off harddrive, whenever it boots from usb, RIGHT before it opens up after the loading screen for a split-second it displays a message saying "Ubuntu 12.10 ....97.845991[kum] disabled by bios" ... any idea what this means?

---

### Post by darkod on 2012-11-14
The bios HAS TO HAVE an option to boot from the hdd, that's basic that all bioses have.
Also, the hdd HAS TO be recognized correctly in bios. If it's not there might be a problem with the hdd or the cables connecting it to the motherboard.

First double check these things because if it's not correctly recognized in bios there is no point to look further, it will not be presented correctly to the OS.

I am surprised how you managed to install at all if the hdd is not recognized in bios. Or you didn't install yet, only running from live mode.

---

