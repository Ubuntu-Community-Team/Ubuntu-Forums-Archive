---
title: "Trouble installing 17.10.1 in UEFI mode. It will install in Legacy mode."
date: 2018-02-03
forum: Installation &amp; Upgrades
---

### Post by irv on 2018-02-03
Downloaded Ubuntu 17.10.1 64bit: Created a bootable USB using Unetbootin. If I set the BIOS to UEFI, turn off the Fast boot and boot off the USB it comes up to the first menu where I chose, "Try without Installing" or just, "install", but it will do nothing. The light on the USB flashes but after 15 minutes I just stop it. Now, If I set the BIOS to Legacy mode it will install just find. I am not using any other OS so this is fine but I was wondering why it will not install in UEFI mode?
By the way, I am installing on a Dell 11" 3000 series 2 in 1 laptop. 17.04 will install in UEFI mode, but 17.10.1 will not. Yes, I checked the USB for Errors and I tried 4 times burning a new USB each time. Anyone have any idea why this is happening? Like I said, I can run it in Legacy mode, it works.

---

### Post by tgm1024 on 2018-04-19
> **irv said:**
> Downloaded Ubuntu 17.10.1 64bit: Created a bootable USB using Unetbootin. If I set the BIOS to UEFI, turn off the Fast boot and boot off the USB it comes up to the first menu where I chose, "Try without Installing" or just, "install", but it will do nothing. The light on the USB flashes but after 15 minutes I just stop it. Now, If I set the BIOS to Legacy mode it will install just find. I am not using any other OS so this is fine but I was wondering why it will not install in UEFI mode?
By the way, I am installing on a Dell 11" 3000 series 2 in 1 laptop. 17.04 will install in UEFI mode, but 17.10.1 will not. Yes, I checked the USB for Errors and I tried 4 times burning a new USB each time. Anyone have any idea why this is happening? Like I said, I can run it in Legacy mode, it works.


Yeah, I've had a miserable time trying to install 17.10.1 on a 2012 Dell Latitude x64 laptop.  Man, this was ugly ***and I didn't succeed***, but I did have some limited success, so many some of this will help.

Long and the short of it is: I feel your agony here.

I'll just list the issues out roughly in order.

1. First pass at installing caused two sets of errors.  A bizarre ugly set of errors regarding UEFI right at bootup, and then continual ACPI errors and then crashes randomly once up and running.  [I]Almost nothing online helps here.  Not even the "acpi=strict" (nor any other acpi= options) Grub-level bootup options worked.
[/I]
2. I was running Dell BIOS A19, and according to many online, it's best to go as late as you can.  So I installed A25.  Not easy.  The only trouble-free install was to reinstall a copy of Windows (you don't need the key, you can run in eval mode), and then run the dell BIOS update.  And THEN punted windows 10, and wend for the reinstall.

---> I will do my level best to *never* have another Dell product in my house again.  It's why I built my latest PC from scratch.  SO worth it.  The Dell driver support has never been solid for me, and their linux downloads are a joke. <---

3. Initial errors on UEFI at boot still.  Not going to go into details here about the UEFI stuff, but the ACPI errors ceased.  Or seemed to.  acpi=strict, and acpi=off, acpi=*whatever* didn't seem to matter: I got no errors.

4. **Periodic crashes continued**.  Randomly.  [SIZE=4][COLOR=#b22222]**Seemed to (maybe) always be related to typing. (????)**[/COLOR][/SIZE]  Whatever that is all about.


Semi Conclusions:
1. Ubuntu (or perhaps Debian in general) is fragile with semi-dated BIOS's UEFI & ACPI support, perhaps by relying on the most current revisions of each.
2. Windows 10 (don't get me started, ugh) has no such issues and works smoothly.  Until it doesn't later on by bogging down to a crawl, of course.
3. ***Perhaps*** (not tried yet), an MBR install will clear everything up, but I'm not getting my hopes up.

---

