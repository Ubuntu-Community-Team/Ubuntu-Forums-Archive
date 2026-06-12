---
title: "Fluendo &amp; messages issued after installation of Maverick"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2010-12-24
I normally use the ALTERNATE install CD for installing Ubuntu.

This is an installation of Maverick.

However, this time I decided to use the LIVE CD instead.

I noticed that there is a check box during the LIVE CD install for installing something call "FLUENDO".

Can someone tell me if I should check this box to install this FLUENDO and what are the consequences of doing that ?

On another note, when the LIVE CD installation finished and I hit the restart prompt, during the restart procedure a long string of error messages were displayed - something regarding input/output error at certain locations.  Then the computer would not restart.  I never got a prompt asking me to remove the CD but I removed it anyway.  I decided to press the ENTER key and it then displayed a text line saying that the computer was being restarted.

What does that string of input/output error messages mean ?

Should I scrap this LIVE CD installation and install from the ALTERNATE CD version like I usually do ?

Thanks.

---

### Post by lemming465 on 2010-12-26
> **wpshooter said:**
> I noticed that there is a check box during the LIVE CD install for installing something call "FLUENDO".
This is a commercial repository where you can buy officially licensed DVD and MP3 codecs for multimedia playback.  This is entirely optional.  Whether or not you want it depends on the legal situation in your country (sensible countries, unlike the US, don't allow software patents), whether or not you are multibooting with other operating systems on your PC which already have codec licenses, whether or not you are planning to do multimedia playback, etc.
>  ... when the LIVE CD installation finished and I hit the restart prompt, during the restart procedure a long string of error messages were displayed - something regarding input/output error at certain locations.  Then the computer would not restart.
How serious the error message are depends on what they were.  Inability to read past the end of the CD-ROM might not matter, and could be an artefact of the way the CD was burned (not all methods put enough zero sector padding at the end).  Unrecoverable read errors from the data being copied would be fatal, as the install would be corrupted.  Does the CD self-test as OK?

Failure to reboot automatically after the install is not necessarily a big problem; some BIOS's don't handle this well from Ubuntu.  (If a BIOS update is available it might improve things.)

Does the installed system boot successfully?

---

### Post by wpshooter on 2010-12-27
> **lemming465 said:**
> This is a commercial repository where you can buy officially licensed DVD and MP3 codecs for multimedia playback.  This is entirely optional.  Whether or not you want it depends on the legal situation in your country (sensible countries, unlike the US, don't allow software patents), whether or not you are multibooting with other operating systems on your PC which already have codec licenses, whether or not you are planning to do multimedia playback, etc.

How serious the error message are depends on what they were.  Inability to read past the end of the CD-ROM might not matter, and could be an artefact of the way the CD was burned (not all methods put enough zero sector padding at the end).  Unrecoverable read errors from the data being copied would be fatal, as the install would be corrupted.  Does the CD self-test as OK?

Failure to reboot automatically after the install is not necessarily a big problem; some BIOS's don't handle this well from Ubuntu.  (If a BIOS update is available it might improve things.)

Does the installed system boot successfully?

Yes, the install "seems" O.K. after rebooting.

I have checked the integrity of the burned CDs and they again "seem" O.K.

I have burned at slowest speed possible and also used different burning programs and STILL get these I/O error messages at the end of the LIVE CD installation of Maverick.  This may be just cosmetic but it sure is something that they need to fix because I would sure hate to try to show a friend the installation of this O/S and have to try to explain to them why all these weird error messages are being displayed at the end of the installation !!!!  I don't think this O/S is going to be gaining many recruits if they keep on outputting untested products like this !!!

Thanks.

---

