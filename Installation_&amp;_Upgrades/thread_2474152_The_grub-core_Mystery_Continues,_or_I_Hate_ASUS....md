---
title: "The grub-core Mystery Continues, or I Hate ASUS..."
date: 2022-04-22
forum: Installation &amp; Upgrades
---

### Post by cubdukat1968 on 2022-04-22
You may recall in a previous post that whenever I tried to boot from a thumb drive to install Ubuntu 20.04.3, I would get an error that said "grub-core: out of memory," and nothing would boot. That problem temporarily solved itself, and I was able to install 20.04.3. Unfortunately, I need to replace it with a clean install of 22.04 LTS because there were a lot of problems in the previous LTS release with broken packages due to unmet dependencies (build-essential and Steam spring readily to mind). Even more unfortunately, the out of memory error has returned, and I have not made any modifications to the BIOS that would provovke that. 

I reached out to ASUS this morning as I believe that there may be a problem with the most recent firmware upgrade that is causing this, as it was also happening with just about every other distro as well. In order to try and get around it, I burnt a 22.04 image to DVD, but that didn't work either. ASUS is looking into it, but I don't expect anything to come out of it; the upgrade is the last one for my motherboard, and I highly doubt there's going to be another one. It's especially problematic because I am unable to go back to a previous version, and Secure Boot has been set to permanently on and locked so that it can't be changed. I will be posting screenshots of various UEFI settings for my mobo that I believe may be suspect, but the problem is basically either the fault of ASUS or with every kernel since 5.13.

---

### Post by oldfred on 2022-04-23
What model Asus?
I have an older z97 motherboard and posted UEFI settings. Many newer boards are very similar.
Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by poorguy on 2022-04-24
I have an Asus Z87 Pro and it won't boot from a usb thumb drive so I just use a DVD which has never failed to work.

At one time Asus made really good motherboards however the Asus Z87 Pro I have has been a disappointing POC.

---

### Post by cubdukat1968 on 2022-04-24
It would appear I may have discovered a possible workaround for my problem. I managed to boot into the thumb drive by going in under the manufacturer/OEM option. That actually worked, for whatever reason. I was then able to get 20.04.3 installed and working. It would appear that the initial install was REALLY borked. On this new one, I was able to get build-essential and Steam installed with no problems at all, and the problem with the Software Store was fixed as well. I was even able to update to 21.10, but when I went to update to 22.04, it's constantly telling me no new version is available. I wonder if it's because not all of the American mirrors have the repositories set up yet, although two days into the official release they really should. 

It still annoys me to no end that I should have to do any damn workarounds for this at all. UEFI and Secure Boot need to go the hell away. This is shaping up to be exactly what I always suspected it was: Microsoft's attempt to shut Linux out of the desktop experience. 

BTW, the mobo in question is an Asus Z370-A Prime (first-generation). Apart from this problem, I've actually been pretty satisfied with the performance.

---

### Post by tea for one on 2022-04-24
> **cubdukat1968 said:**
> but when I went to update to 22.04, it's constantly telling me no new version is available.
Patience is required because
> Upgrades to 22.04 LTS are currently not enabled (due a bug with snapd and update-notifier) but will be in the next couple of days.
Source [https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)
> It still annoys me to no end that I should have to do any damn workarounds for this at all. UEFI and Secure Boot need to go the hell away. This is shaping up to be exactly what I always suspected it was: Microsoft's attempt to shut Linux out of the desktop experience. 
UEFI is superior to the old style BIOS - much easier to manage partitions and boot from disks.
Secure Boot is very useful for enterprise/business users but unnecessary for home users who should have total control over their systems.

---

### Post by cubdukat1968 on 2022-04-27
Glad to know the update issue is not normal. 

I am currently on the phone with ASUS, but and it's about what I expected: completely useless for anything but using up cellphone minutes. They all but completely shut down when I mentioned that this was happening when I was trying to install Linux. It was that instant knee-jerk blanket refusal that seems to hit anyone when you even mention the word Linux. They still don't get that this problem could affect Windows as well because it's something in their damn firmware that doesn't like their implementation of Secure boot, which they had to get from Microsoft to be able to get certified to work under Secure Boot. 

Even though I managed to work around this, it's becoming painfully apparent that I am going to have to use older hardware to build my next Linux box, and definitely not ASUS hardware.

---

### Post by cubdukat1968 on 2022-04-28
Well, after fighting over the phone with ASUS, I think I may have found a definitive, if not somewhat expensive, solution to this problem...

Ripping this motherboard out and getting a new one from a different vendor that doesn't lock down Secure Boot, and that vendor will NOT be ASUS...

Unfortunately, that still will not resolve the issue with not being able to boot from Linux USB sticks reliably on this system. 

It also occurred to me to wonder if this isn't something with GRUB2 itself, since this is something that happens with every Linux distro I've gotten my hands on... 

I think I'll probably just update to 22.04 now that I'm able to, and just know that if the system gets borked, that's it for me and Linux on this system.

---

### Post by oldfred on 2022-04-29
Microsoft required vendors to allow users to turn off UEFI Secure Boot (or used to).
My Asus manual, since older, said if installing Windows 7 use the "other" setting not "Windows" setting. So that is really the UEFI Secure boot setting in Asus as Windows 7 does not support Secure Boot, but could be booted in UEFI mode.

---

### Post by cubdukat1968 on 2022-05-29
That went away almost immediately. The choice was left up to individual vendors, but Microsoft "energetically suggested" (pronounced "threatened") vendors lock Secure Boot and make it otherwise unable to be switched off.

---

### Post by bingodingo on 2022-05-30
I doubt it's an Asus wide policy. 
Using an Asus board with a firmware update from late 2021 I can still boot a linux live usb - selecting CSM off and, for secure boot, 'other os'.
I would recommend: recheck your usb, consider hardware issues, see if booting from internal graphics (rather than an external card) if you use one helps (that worked for me previously with an ASUS board).
(Firmware updates tend to reset bios defaults / CMOS; sometimes clearing the cmos settings may help).
As I'm still able to use linux on an Asus and a Gigabyte board, any conspiracy to lock it out is a little ineffective at the moment, so keep trying.
Good luck!

---

### Post by cubdukat1968 on 2022-10-03
Got a little more enlightenment on this problem. It may have something to do with the Resizable Bar function that many new graphics cards are using. I recently upgraded to a GeForce RTX 3060 Ti Founders Edition, and it seems that in addition to enabling the ReBAR setting in BIOS, you also need to have “Above 4G Decoding” activated as well.

As luck would have it, “Above 4G Decoding” causes problems with GRUB2, and is the probable cause of the problem I was having. It’s been reported as a known bug with quite a few distros, Ubuntu included, but to my knowledge nothing has been done about it. So ASUS is temporarily off the hook because it’s not necessarily their fault. But the way they treat Linux users is still inexcusable, so we’re still done professionally…

---

