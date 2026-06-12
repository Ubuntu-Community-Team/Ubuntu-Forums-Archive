---
title: "Attempting to revive old HP wind8.1 laptop (HP Envy X2 PC)"
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by biggiebob on 2018-10-29
Been trying to revive my old tab/laptop as I'm not near my desktop any where near as much as I used to be with work.

PC is a HP Envy X2 PC.
Details as follows
Intel Atom CPU (Z2760), @1.80GHz
2.00GB RAM
64GB SSD
32-bit OS (Windows 8.1)

Touch screen hybrid tablet PC - this was one of the very first "Full Windows" tablet PCs.

**First up:**
If Ubuntu won't help my GPU's inability to play videos (youtube, netflix etc), please let me know and I'll stop wasting time and go fork out for a new one!

**Background:**
Frankly, it was never worth a cent for what it cost. (juvenile, poorly researched decision to buy it at the time). Cannot play videos at more than about 5 frames per second, and Opera is the only browser it can handle. Have pretty much wiped everything from the computer to even get that functioning. Was hoping a Ubuntu or Google chrome OS would revive it.... the only problem being HP must have had it out that they wanted to rip people off with this device and make sure they can never change the OS to make it viable.
I've spent hours now scouring the internet and this forum trying to find ideas on how to get past the BIOS to let another OS run on this PC.


**Attempts to date:**

I have the ubuntu-18.04.1-desktop-amd64 file I downloaded as a torrent.

I've used multiple ISO writer programs, first PowerISO, followedby Etcher, and now I've trialled Rufus many times (Rufus is the one I've made the "most progress" with).

I've also tried to install Neverware (the google chrome OS) and haven't had any luck either. Haven't progressed any further than I have with Ubuntu.

When writing the file, I've tried both MBR and GPT as the partition scheme (this is in Rufus). I had trialled file system methods other than FAT32 in powerIso but it didn't seem to make a difference.

When using the MBR partition, followed by selecting "DD Image Mode" (rather than ISO copy mode), is the furthest I've gotten. And with that, I can boot to a screen with an underscore up the top left of the screen (_). This is with secure boot disabled, and the OS boot option as the last on the list.

As for "EFI" boot, it didn't get beyond a completely black screen when I managed to get it to a spot where I could load a boot file without "boot device failed". 

Sorry for the long post, but more or less hoping someone might be able to point out something that I may be missing, or if HP really did succeed in making this device pure ****.

Any help or guidance would be greatly appreciated.

---

### Post by ubfan1 on 2018-10-29
Try Lubuntu instead of Ubuntu, that'll have a better chance of not running out of memory.  That said, I doubt you will get reasonable video performance from that machine.

---

### Post by mikewhatever on 2018-10-29
Stop wasting time. z2760 is a reincarnation of Intel's gma500 abomination. The hardware is actually quite decent, but it lacks a proper driver for the integrated GPU. It doesn't matter how you write ISOs or what browser is used, video playback will still lag. Lubuntu would have been a better choice then Ubuntu, but it will not improve the playback problem.

---

