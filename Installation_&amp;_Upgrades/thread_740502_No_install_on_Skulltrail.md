---
title: "No install on Skulltrail"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by psychokilla on 2008-03-30
Hi, I built myself a nice new Skulltrail system, it already has Vista Ultimate x64 on it which is running nice and stable, still I fancied trying out Ubuntu on it.I downloaded the desktop version but it won't install, it gives a couple of errors (which are far too fast to read) after choosing the setup option in the menu and then the computer reboots. Should I be using the server version since that's what Skulltrail basically is?

---

### Post by chewearn on 2008-03-31
No, the server version will give you a server installation, without the GUI desktop.

1. Try verify the CD burn, by selecting the boot option "Check CD for defects".

2. Use the alternate livecd.  This one is a text mode installer, which have higher chance to succeed compared to the graphical installer

3. It will really help a lot to know the error messages.

---

### Post by psychokilla on 2008-03-31
Well, the message displays twice very quickly says something like "Memory Allocation failed....", then "Please wait.." or something and the screen goes blank very quickly like the PC is restarting or something and then the display doesn't come back up, my monitor (Samsung 275T) just goes into standby.

I also have 2 8800GTS's in SLI, could this have something to do with it?

What is the livecd installer? Is that one of the options on the installer cos I don't see it?

---

### Post by chewearn on 2008-03-31
> **psychokilla said:**
> Well, the message displays twice very quickly says something like "Memory Allocation failed....", then "Please wait.." or something and the screen goes blank very quickly like the PC is restarting or something and then the display doesn't come back up, my monitor (Samsung 275T) just goes into standby.

I also have 2 8800GTS's in SLI, could this have something to do with it?


I don't run this set-up (higher end nvidia with SLI); I couldn't comment.


> What is the livecd installer? Is that one of the options on the installer cos I don't see it?

Livecd is simply the iso file, which you burn to a disc.  You can then boot to this disc, test ubuntu (without writing to harddisk), or install ubuntu into a partition.

When you boot into the livecd, there is one option "Test CD for detect".  Run that to verify that your CD burn is OK.

---

### Post by bobblehat on 2008-04-24
I think I'm seeing the same. I've done several installs on a range of hardware and all were absolutely fine but I've been trying on (someone else's) Skulltrail with a single NVidia 8800 GTS and get very similar symptoms. I initially tried Gutsy (AMD64) then the Hardy Beta. 

Both got to the initial text-based menu, I chose to install, then the screen went blank. Judging by the DVD and hard disk activity, the installation seemed to continue but I couldn't get anything on the screen.

Eventually I downloaded the alternative install and that ran fine. I can boot via the recovery option and get a prompt OK and I'm continuing to work there to try to get X up and running. I'll post here if I get anywhere - I'm no expert but willing to learn.

---

### Post by bobblehat on 2008-04-24
By the way, the message that flashes is sub-second but seems to me to say [some numbers, maybe hex] Failed to allocate memory resource [more numbers]. Sorry I can't be more specific - it really is just a flash of a message.

---

### Post by bobblehat on 2008-05-06
I have a little more info now which might help. I can boot to a root prompt (via recovery mode) and manually start a network and x and get a gnome desktop (but obviously that's not OK for continued use). I managed to download and install the nvidia driver and that seems OK when running as root.

I've also configured grub to turn 'quiet' off when booting as a normal user and can see that the boot starts to run (seems to recognise hardware, etc) but then the screen just goes blank. If anyone can advise on what's best to capture from logs etc to help with the diagnosis I'd be happy to look for that and post it here. It's difficult to see the last message written to the screen before it goes blank but I'm guessing that might also be in a file somewhere?

Any help on the diagnostics would be appreciated. Cheers.

---

### Post by bobblehat on 2008-05-07
This thread -> [http://ubuntuforums.org/showthread.php?t=756708](http://ubuntuforums.org/showthread.php?t=756708) seems relevant to my problem so I'll continue there.

---

