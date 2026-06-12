---
title: "Ubuntu 24.04.1 Desktop &quot;No Boot Device Found&quot; after clean install on Dell 5810"
date: 2024-11-08
forum: Installation &amp; Upgrades
---

### Post by sdrabot on 2024-11-08
Tried install in Legacy and UEFI, same result

Tried install on different HDD, same result

Tried install in different computers (I have more than one 5810), same result

I have 20.04 running on same hardware with no problems

---

### Post by guiverc on 2024-11-08
Being specific with details can matter, as you've provided few.

I take it you're asking about Lubuntu 24.04 LTS, given you put the question in the *flavor* section of the forum, and Lubuntu specifically.

Lubuntu 24.04 LTS installs with the GA kernel stack, which is the 6.8 kernel, you mention 20.04 but give no specifics there, but the oldest kernel available with 20.04 is 5.4 (GA kernel stack), and newest is only 5.15 meaning you've a much older kernel on that system, thus if its hardware specific issue relating to kernel modules (aka *drivers*), a much newer kernel stack will mean its a different system you're trying to install.

You mention *legacy* and uEFI, where Lubuntu is QA (*Quality Assurance*) tested to install on old *legacy/CSM* hardware, uEFI and *modern *Secure-boot uEFI hardware WHEN the ISO is written to install media correctly; did you *clone* or write the ISO as per documentation? as if its *reformatted during write* using specific options, you do need to match those options *perfectly* to your intended hardware otherwise it'll install but fail to ever boot (*as installer can write the bootloader incorrectly due to your reformatting of the ISO at ISO write time*). I wonder if you create a problem due to your method of ISO write, but you gave no details.

Lubuntu 24.04 uses a much more *modern* version of the *calamares* installer than 20.04 did (*20.04 in fact was released with two different version of calamares, due to issues existing in the first version*) but the installer was the same.. major difference is the kernel options I first covered (20.04 & 22.04 being old has 5 different kernels available on ISOs; where 24.04 still only has the original GA kernel stack, 6.11 not yet on ISOs).

Some clues as to what you actually installed will help; you mention Ubuntu Desktop which uses a different installer, but asked the question in the Lubuntu section, so which are you asking about??  How did you write your ISO?  Was it written as per documentation? or reformatted during ISO write?

---

