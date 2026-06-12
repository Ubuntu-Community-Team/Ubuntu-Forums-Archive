---
title: "No GRUB or Boot after multiple install attempts"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by caseydwilder on 2020-05-14
I'll preface this by saying I've run Ubuntu several times and several other distros as well, though I don't consider myself a Linux expert in the slightest (just a lover and enthusiast). With that said, don't assume I know too much more than I say. Haha. 

So, I recently switched from a SanDisk SSD to a Samsung Evo 860 1TB. I feel this is a really important piece of information because these complications never happened until I upgraded. I draw special attention to this because it almost seems as if when I select it as my boot drive, it can't find the Grub or anything to boot (it doesn't say no bootable drive or anything, simply a black screen with a flashing underscore in the top left). 

Basically, I install Ubuntu. The installer doesn't mention issues. I restart and select my Evo as my boot drive, then nothing happens. 

I've previously successfully installed Manjaro, Solus, and a few others on there with no trouble. Most recently, I had Windows on it. 

When I first got this drive I also had issues trying to get Ubuntu up, so I tried others and had plenty of success there. 

If it's relevant, my motherboard is made by ASRock. I don't have the model in front of me, but it's the extreme 6+ with an Intel i7 4790k on it. Bios was updated about 6 months ago and should be fine. Settings on it seem fine (at least have always worked for me previously). 

Things I've tried involve me formatting the SSD with GPT, installing with ZFS (which I prefer--seemed really snappy previously when I tried it), the "erase everything" option during install. 

I have not tried formatting my own partitions on the SSD myself because it's a touch confusing for me. 

Anywho. The big thing I've noticed is I'm used to a Grub loader screen popping up for a couple seconds when I select my drove, but for whatever reason that's not been happening. I've only had the issue with this 860. Idk if there's a special spot the drive looks for a grub loader (and Ubuntu is installing it in the wrong place) or what. I have a feeling it's some super awesome feature the drive has that's not playing nice with the installer. 

I'm about to sleep for the night, so I apologize for delayed replies. Guidance would be appreciated. I'm sure it's something insanely simple, but for the life of me, I have no clue what.

---

### Post by oldfred on 2020-05-14
Have you updated the firmware on the SSD?
I go a new NVMe Samsung. For Linux it had a bootable ISO just for my model. It looked like an old DOS screen. It checked version and when different updated it.

You have an UEFI system, so should be using UEFI with gpt partitioning. 
Know nothing about ZFS.

What video card/chip?

---

### Post by caseydwilder on 2020-05-15
I haven't tried updating the SSD firmware. I'll look into that. 

I have been using the UEFI with GPT. 

nVidia 1080ti for the GPU. 

I've tried installing with and without updates and prop drivers.

---

### Post by caseydwilder on 2020-05-15
Updated my Samsung Evo Firmware. Nothing has improved. 

Any other ideas, anyone?

---

### Post by caseydwilder on 2020-05-15
Since I can't seem to get any where with this, I've decided to just install Manjaro. Seems to be working fine. 

I'm not sure what it has to do with, but it seems there could be room for improvement in the Ubuntu installer since Majaro's installer pulled it off fine.

---

### Post by oldfred on 2020-05-15
What version of grub does Manjaro use? Ubuntu is 2.04.
grub-install -V
uname -a

---

