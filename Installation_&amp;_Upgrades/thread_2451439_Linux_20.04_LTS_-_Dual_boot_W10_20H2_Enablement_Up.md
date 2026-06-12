---
title: "Linux 20.04 LTS - Dual boot W10 20H2 Enablement Update"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by maddenjmf on 2020-10-04
As the 2nd half of this year's Windows feature update, I'm posting to ask if you guys think that this update will overwrite my Linux partition (or best case, break GRUB), or whether this only occurs for major spring releases.

Thanks!

---

### Post by CelticWarrior on 2020-10-04
If you have both OSes in UEFI mode then that happening would be a first, with ANY Windows update.
Changes to the partition table happened in the past in BIOS/MBR systems only.

---

### Post by maddenjmf on 2020-10-04
That's good to know for future installations, I did this on an old machine that runs fine but with MBR partitioning.

Cumulative updates have not given me errors, but I have read up on Windows ignoring Linux MBR partitions (not because it's Linux, but because it treats every partition like Microsoft owns it).

I looked at converting my system to UEFI but for the work involved, as I'm just experimenting, I thought I'd wait until I get a new SSD machine that's UEFI

---

### Post by CelticWarrior on 2020-10-04
Systems cannot be "converted" to UEFI. UEFI is the motherboard's firmware that replaced / is used instead of BIOS in almost all computers from the last decade on.

Now, with most UEFIs it's still possible to "emulate" BIOS - AKA "Lagacy" or "CSM" - and install in the same way / with the same requirements as if in a old BIOS machine. There's really no point in using Legacy unless when installing an OS that doesn't support UEFI. Not the case here.

---

### Post by maddenjmf on 2020-10-04
[https://youtu.be/f81qKAJUdKc](https://youtu.be/f81qKAJUdKc)

This is what I was referring to as my BIOS settings includes UEFI mode. I'm not doing it.

Looking to clarify whether or not at this point with my current setup, what you think my chances are of this update breaking my partitions.

Thanks for all information!

---

### Post by CelticWarrior on 2020-10-04
The main mistake was to use Legacy as I already commented.
It's easy to reinstall properly but "converting" as you wanted to do in a previous thread can (will) result in data loss and all sorts of problems. Also as already commented there, with Linux it can be done but with Windows not really.

The problem with partitions happened years ago and only affected MBR which is what you have now. The chances of it happening again are very slim. Before it had to do with optimizations that Microsoft introduced with a certain feature update that broke some partition tables.

So, again repeating what was said already months ago, if you want piece of mind with Windows updates then reinstall both OSes in UEFI mode and GPT. GPT is a must beacuse of Windows requirements for UEFI mode. Linux install in UEFI mode to MBR but maybe it shouldn't.

---

### Post by maddenjmf on 2020-10-04
This makes sense, thank you. I will pause the update and wait until I get a new machine and then install both OS versions in UEFI, and copy over my personal files.

Once I've backed up my data I may even test the update Windows side to see what happens, and report back. But as you say, threads like this will soon be redundant as MBR disappears.

---

### Post by scriber on 2020-10-05
Well I have an Asus Strix Z270E motherboard with UEFI BIOS setup in Legacy mode, and have Win10, Ubuntu 18.04, Ubuntu 20.04, Mint 19.3 and Mint 20.04 all installed in Legacy mode.

I had put off installing the Win10 2004 upgrade for weeks because I wasn't sure if it would affect anything.

I finally decided to do the upgrade last week ( after imaging the whole system just in case of problems ), and nothing was changed in any of the partitions, everything booted normally after the upgrade.

I use TeraByte Unlimited BIBM for the Boot Manager, and image everything with their image program.

---

