---
title: "Sata Hardware Raid with Ubuntu OS itself"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by 8bit on 2006-10-24
I haven't checked on this in a while and I did do a little (very little) searching the forums on this subject but my question is this.

Is it now possible to install the OS itself Dapper/Edgy to a Raid 0 config without a lot of fuss? I don't mind purchasing the hardware for compatibilities sake (HighPoint Sata Raid Controller for example). I have installed Winbloze to a Raid0 config from the get-go without issue and was just wondering if it were now possible on Ubuntu. I want the increased perfomance and would like to have it for the OS as well as the rest of my partitions using hardware Raid not software.

I'm thinking about building a new system and wanted to use two 10K RPM drives .

Thanks for any input you can provide.

8bit

---

### Post by Duggeek on 2006-10-25
SHORT ANSWER: Yes. If it's true hardware RAID, Ubuntu will see it as one, large drive. If Windows has already used the whole array as an NTFS volume, then you've got other problems. :mrgreen: 

I've only had my Soyo board to test, but it seems to be a typical implementation. (Bear with me if things look different)
[LIST][*]First, go into your BIOS Setup (where it says "Press <DEL> to enter setup")[*]Next, head to Integrated Peripherals (or similar)[*]Now, where it says "RAID MODE" or "SATA MODE", set it to "RAID" (vs. "IDE")[*]Reboot and watch closely.[/LIST]
(Not the same as your PC? :( Sorry, it was my best attempt. Go back to the MoBo manual, or the OEM website, and see what they have to say about it.)

There should now be an extra screen during the BIOS POST process. It should briefly show you that it recognizes the attached hard-drive devices and proceeds to boot. You may also notice a message about "Press <TAB> to configure". You will need to press the Tab key as soon as that screen appears. (Again, maybe not the exact-same as what you see; RTFM)

Presto! You're in the RAID Setup Utility. Here, you can do the basics on setting-up your two drives to operate as a single device. The set-up may take some time as the utility will want to extensively test-out both drives.

**[COLOR="Sienna"]ONE AND ONLY WARNING:[/COLOR] NOTHING, I MEAN **[COLOR="Sienna"]NOTHING[/COLOR]** WILL SURVIVE THE STRIPING PROCESS. WHATEVER WAS ON EACH OF THOSE DRIVES WILL BE GONE. THAT MEANS GONE, DADDY, *GONE!***

[COLOR="Navy"][SIZE="5"]*"How do I know all this worked?"*[/SIZE][/COLOR]

The proof of a successful RAID "merging" is *when you see a program showing the hard-drives as one, big storage device* (and not as two, smaller ones) RAID-striping is "transparent" to any system you would install; Linux, Windows, BeOS, OSX, XDOS, whatever... they would all be "fooled" by the RAID BIOS.

Don't peek at the BIOS screen; it will **always** reveal the two drives; it's showing you that the RAID is working and that both drives are still healthy. You need to load an OS to be sure that RAID has been set-up properly.

Best way to check this out is to do a basic FDISK, or get a minimal boot-stub and use gparted. Booting-up the Ubuntu LiveCD is an excellent way to check this out. (use "Disks & Partitioning")

Even better, once you see that RAID is alive and tickin', you can immediately start setting-up Ubuntu. (or reboot to whatever; the RAID striping is basically permanent) ***wr0k!***

Any questions?

-- Duggeek

---

### Post by 8bit on 2006-10-25
I was worried that I wouldn't get much of a reply but damn that was good. Thanks Duggeek!

I've setup windbloze raid0 before but this new sytem will use only Ubuntu. I've been Win free for almost 2 years now. I may use vmware and win to just play a few games.

I've heard good things about HighPoint raid controllers and thier support for Linux. I may just purchase one of those to be on the safe side.

I plan to build a shuttle box for this but all of the AMD flavors use the promise sata which I keep hearing has problems.

It's good to know I can pull it off.

Thanks again!
8bit

---

