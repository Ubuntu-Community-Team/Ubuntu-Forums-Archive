---
title: "VAIO Tap 20 - Unable to Clean Install Ubuntu 20.04 (Multiple Issues)"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by Gregory.Opera on 2020-04-24
When I try to "clean" install Ubuntu 20.04 LTS ("Focal Fossa") onto a Sony VAIO Tap 20 SVJ20215CGB with secure boot *enabled*,  everything goes fine, until I restart... Once I restart the computer, I  see the "VAIO" logo, then only a black screen - this is *before* the full-disk encryption password box appears.

As is to be expected, I cannot access Terminal or anything else at this time.

If I try to "clean" install Ubuntu 20.04 LTS ("Focal Fossa") with secure boot *disabled*, everything installs just fine - but after the reboot, various components are missing - the Ubuntu Software Center is the most *obvious* example, but I am *sure*  there are plenty of others, if I was to take my time and have a deeper  look (yes, I picked a "normal" installation - I did it twice, just to be  sure!).

This installation media has been used to "clean" install Ubuntu 20.04  LTS ("Focal Fossa") on multiple other computers (different  manufacturers and models), *without issue*, so there is nothing wrong with the installation media.

Full-disk encryption is essential on this particular computer.

This computer has previously run every other version of Ubuntu and  Linux Mint thrown at it without issue... Ubuntu 20.04 LTS ("Focal  Fossa") is the first distro that has experienced problems.

I'm out of ideas - does anyone have any suggestions?

---

### Post by CelticWarrior on 2020-04-24
The black screen with Secure Boot enabled could be explained if it had a Nvidia card but supposedly it has an Intel HD Graphics 4000? With the Intel Graphics this typically doesn't happen because Secure Boot doesn't prevent the default signed open-source Intel drivers from loading like what it does with the proprietary unsigned Nvidia drivers.

So, maybe it needs additional tweaking in the UEFI settings? And very likely UEFI update? But if it works fine with just Secure Boot disabled maybe not (I mean, additional settings changed, not the firmware update because that you should definitely do)?

Then > after the reboot, various components are missing - the Ubuntu Software Center is the most *obvious* example, but I am *sure*  there are plenty of others, if I was to take my time and have a deeper  look
Well, this is probably nonsense and lack of updated information. Ubuntu 20.04 comes with a Snap Store. The Ubuntu Software Center, the one that actually had that name, has been deprecated years ago. If memory serves me right, the USC was replaced by something based on gnome-software up to 19.10. But please look deeper for the things you think aren't there and do your own research to find out if they're actually missing or if, most likely, they shouldn't be there because, you know, removed or replaced.

---

### Post by Gregory.Opera on 2020-04-24
> **CelticWarrior said:**
> So, maybe it needs additional tweaking in  the UEFI settings? And very likely UEFI update? But if it works fine  with just Secure Boot disabled maybe not (I mean, additional settings  changed, not the firmware update because that you should definitely  do)?

It *is* running the most up-to-date UEFI firmware (I checked the version number).

As to settings which need to be changed, I have not needed to change  anything in the past and I could need see anything that I suspect *needs* to be changed - but if you have any suggestions, I'm all ears... Bear in mind that this is an *older* UEFI - it was one of the *first* commercial UEFIs, from the Microsoft Windows 8 days - so its functionality leans more towards the *BIOS* side of the house, as opposed to the "flashy" and "feature-packed" UEFIs that many manufacturers offer these days.


> **CelticWarrior said:**
> Then 
Well, this is probably nonsense and lack of updated information. Ubuntu   20.04 comes with a Snap Store. The Ubuntu Software Center, the one that   actually had that name, has been deprecated years ago. If memory  serves  me right, the USC was replaced by something based on  gnome-software up  to 19.10. But please look deeper for the things you  think aren't there  and do your own research to find out if they're  actually missing or if,  most likely, they shouldn't be there because,  you know, removed or  replaced.

Don't be *that* guy.

You *know* what I mean - the "snap" version of the Ubuntu  Software Center, which is included with Ubuntu 20.04 LTS ("Focal Fossa")  by default in *all* new installations - is what is _not_ installed, but *only* if I run the installation with secure boot *disabled*... Obviously I cannot verify that the Ubuntu Software Center *is* installed when I install Ubuntu 20.04 LTS ("Focal Fossa") with secure boot *enabled* - but *every* other computer which I have just installed Ubuntu 20.04 LTS ("Focal Fossa") on, all of which have secure boot *enabled*,  have installed the Ubuntu Software Center alongside the "clean" install  of Ubuntu 20.04 LTS ("Focal Fossa"), so I have no reason to think it  would be any different on *this* computer.

For reasons I cannot yet explain, the ISO seems to be performing a "broken" installation when secure boot is *disabled*, even though the ISO file-check on startup shows no errors and all of the other computers (with secure boot *enabled*) have a "perfect" installation.

And I don't need you to tell me to do some digging on my own - I have been *doing* that and I am *continuing* to do that (I have an unrelated problem with my Microsoft Surface Go for example, and I have not yet posted about *that*  because I have a couple of other things I'd like to try first!)... I  have posted here in hope that somebody will offer some constructive help  _whilst I continue to seek a solution_.


--

So I "clean" installed Ubuntu 19.10 ("Eoan Ermine") with the  intention to immediately upgrade it to Ubuntu 20.04 LTS ("Focal  Fossa")... I've had to try it in "legacy" mode though (i.e. not "UEFI"  mode), because I kept getting UEFI errors (the same as those below) when  attempting to boot from a USB "thumb" drive.

I did get a strange error right before I started the upgrade:[I]
Connection to Snap Store failed
Your system does not have a connection to the Snap Store. For the best  upgrade experience make sure your system can connect to  api.snapcraft.io.
Do you still want to continue with the upgrade?[/I]

I would have thought that all the Snapcraft stuff would have been  installed during the upgrade (seeing as it's largely used as the default  in 20.04)?

Anyway, the results were weird.

Ubuntu appeared to half-upgraded - there's a mix of *new* software (the "Snap" version of the Ubuntu Software Center) and *old*  software (the pre-20.04 version of Files / Nautilus), plus Ubuntu still  thinks its running 19.10 with no new updates or upgrades available.


In an attempt to fix this, I also tried installing Ubuntu 18.04 ("Bionic Beaver") with Secure Boot *enabled*,   with the intention of waiting for the first "point" upgrade (e.g.   Ubuntu 20.04.1 or higher), but I get this error message on startup   (immediately after the manufacturer logo):
[I]Failed to open \EFI\BOOT\mm64.efi - Not found
Failed to load image \EFI\BOOT\mmx64.efi: Not found
Failed to start MokManager: Not found
Something has gone seriously wrong: import_mok_state() failed: Not found
[/I]

At this point, I suspect either the UEFI is corrupt - which I don't know *how* to fix - or the UEFI is faulty - which I *can't* fix (Sony haven't manufactured computers in a long, *long* time)... But I'm out of ideas, so if anyone has any suggestions, it would be appreciated.

--

*Lots* of people on *other* sites have suggested *loads* of solutions, and not one of them has worked... Furthermore, neither a "lightweight" Linux distro nor the previously-working distro (before I had these problems) will work; I have the same problem as described above.

So I'm putting this down to some sort of hardware fault, likely with the UEFI, and marking this thread as "solved" due to the fact that I have given up (I was planning to replace the computer in the near-ish future, anyway).

Disappointingly, the Ubuntu Forums has shown why it has the reputation it does these days because unlike the early days of Ubuntu, for those of us that have been around long enough to remember, nobody here has actually been of much help...

---

