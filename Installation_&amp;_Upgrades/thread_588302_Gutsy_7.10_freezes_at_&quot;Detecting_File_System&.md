---
title: "Gutsy 7.10 freezes at &quot;Detecting File System&quot;"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by pikkio on 2007-10-23
I've installed Gutsy on 2 machines up to now.
I'm willing to do the same on an old Athlon PC but I get stuck in a bad issue... it freezes at 15%, on "Detecting File System".

I'll try to download the Alternate version but, hey, it's very sad 'cause on that machine I previously got installed Feisty, Edgy, Dapper and Breezy... :( :(

---

### Post by runescape1143 on 2007-10-24
This is exactly where it freezes for me too. ANd i had feisty on previously. It doesn't upgrade from feisty with the update manager, (a zillion and one dependency issues) and it freezes at 15% on the full install.

At least i know it's not a me thing.

Maybe this could be of some use...

[http://ubuntuforums.org/archive/index.php/t-333754.html](http://ubuntuforums.org/archive/index.php/t-333754.html)

it basically says check for errors using [CTRL] + [ALT] + [F1 thru F12], (assuming of course that ur computer isn't simply stuck) or try the alternate cd's text based installer.

---

### Post by tmcarson1 on 2007-10-24
This is happening to me also, the computer doesn't freeze it just seems the installation freezes.

---

### Post by PrairieShaman on 2007-10-26
me too..

---

### Post by hatewindows on 2007-10-26
I ALSO HAD the problem.. I found that adding more memory--ended the problem! I had like 256MB of ram so i installed another 256 and BINGO--the unstall blew right past the 15%--everything works now!!  Good Luck                MARK

---

### Post by hatewindows on 2007-10-26
Should Of Said Install!!

---

### Post by shaynegryn on 2007-10-27
> **pikkio said:**
> I've installed Gutsy on 2 machines up to now.
I'm willing to do the same on an old Athlon PC but I get stuck in a bad issue... it freezes at 15%, on "Detecting File System".

I was installing Gutsy on a friends PC and it also froze at the same point several times. After looking at some of the suggestions, we realized that we as well had very little in the way of ram. We did not have the alternate cd with the text based installer, or spare ram lying around, so instead we booted from the regular live cd in **Safe Graphics Mode**. It made it to 15% and then beyond, and finally installed successfully.

---

### Post by shafin on 2007-12-03
Weired, I'm also having the same problem.The PC has 1 GB of RAM and System Monitor is saying that only 51% is used.
I'll try the safe mood method now.

---

### Post by shafin on 2007-12-03
> **shafin said:**
> Weired, I'm also having the same problem.The PC has 1 GB of RAM and System Monitor is saying that only 51% is used.
I'll try the safe mood method now.
I overcame it by manually partitioning the Disks.The safe mode method was not needed.

---

### Post by jkohler2 on 2008-01-27
My Dell notebook 4150 with 512 M ram workd ok on previous versions of ubuntu. 
Version 7.10 will freeze while I am using Firefox and moving from one web page to another.
At that point, I cannot quit the browser.  I cannot restart Linux from the System prompt or on/off prompt. 

All I can do is disconnect the laptop battery, AC power, and do a total restart.  I have repeated the failure several times.

John Kohler
Daly City, CA

---

### Post by fattmox on 2008-02-27
I, too, had this problem. I had 256 of RAM and crashed at 15%. I added another stick and VOILA, the install went fine.

Is there a 'System Requirements' I missed?

---

### Post by kernst on 2008-02-29
> **shafin said:**
> Weired, I'm also having the same problem.The PC has 1 GB of RAM and System Monitor is saying that only 51% is used.
I'll try the safe mood method now.

I can confirm that this problem still occurs with the latest Ubuntu 7.10 x86 installer, even *with* plenty (1 GB) of RAM. But I believe I have a solution that doesn't require more RAM, manual partitioning, safe mode graphics, or the alternate installation CD.

I have basically the same situation as what the poster "sweb" described in a similar thread here: [http://ubuntuforums.org/showthread.php?p=4171764]("http://ubuntuforums.org/showthread.php?p=4171764#post4171764") (multiple hard disks, with one having Windows XP preloaded). I don't think the problem is Windows XP or multiple hard disks, but rather mounted filesystems confusing the installer. That is, a bug in the installer and/or the [FONT="monospace"]partman[/FONT] utility that handles the partitioning for the installer.

When I started the installer, I had several of the preexisting filesystems on my internal hard drives mounted (meaning I'd double-clicked on and opened them from *Places -> Computer*)--*including the one I was installing to*, an empty FAT32 partition. So it occurred to me that maybe the fact that those filesystems were mounted was causing the installer to get stuck. And indeed, by running 'top', I noticed a process called [FONT="monospace"]**01unmount_busy**[/FONT] which was using over 60% of the CPU and appeared to be very befuddled trying to unmount the partition I was about to install to:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
17321 root      25   0  5156 2580  824 R 57.3  0.2   6:44.92 01unmount_busy
```

Simply unmounting the filesystem in question didn't seem to make it come back to life, at least not right away, and I got tired of waiting. Even though purpose of the [FONT="monospace"]/lib/partman/commit.d/01unmount_busy[/FONT] script appears to be to wait for mounted partitions to become free so the installation can continue! **DISCLAIMER:** The installer may indeed continue after you simply unmount the mounted filesystems. I'm just saying I was too impatient so I basically short-circuited [FONT="monospace"]01unmount_busy[/FONT] after I knew everything was safely unmounted.

**So here's what I did to kick-start the installer, which *did* in fact finish successfully after that:**

I actually performed these steps *while* the installer was hung at 15%. After I did the steps below, the installer went back to the spot where you can choose manual or "guided" partitioning, I had to click "Next" a few times (but my previous selections were pre-filled), then the rest of the process finished without a hitch.

So here we go:

[LIST=1]
[*]Unmount any physical filesystems you may have mounted by right-clicking on the icon in the "Places" sidebar of the file browser and choosing "Unmount." (*You won't see this option if they aren't already mounted*.)
[*]Open a terminal (*Applications -> Accessories -> Terminal*)
[*]Run the following command as 'root' using sudo (this should be perfectly safe as you're running off the LiveCD at this point, so the next step shouldn't harm anything that's already on your computer):
```
sudo top
```
[*] If your problem is the same as mine, you should see the top process there called [FONT="monospace"]01unmount_busy[/FONT]. Press 'k' for "kill", then type in the process's ID number (in my example it was 17321) and hit ENTER. *Be careful to type the process ID correctly so you don't kill the wrong process.*
[*] Hit ENTER again when it asks you what signal ([15]).
[*] Press 'q' to quit 'top'
[/LIST]

At this point, the installer may go back a few steps, but when you go forward again it shouldn't hang at the 15% mark. That is, if your problem is the same as mine (which seems likely since everyone says it hangs at the 15% mark). I'll try to add this information to whatever bug reports are already out there so maybe we can get it fixed in the next release.

---

### Post by RDL89 on 2008-04-14
Thanks Kernst, it did get me past the 15% mark. It continued but the "progress bar" disappeared. I just let it keep running until finally it said finished and that the computer needed to be restarted. I took the cd out and restarted but it does nothing. It's like it didn't really install. I'm trying to install 7.10 on an external HD. I have 2 partitions, both 20 gigs. I have xp-media edition on the internal drive and am very cautious about not erasing it.

---

### Post by RDL89 on 2008-04-14
Gparted says about 2.5 gigs are on the partition now.

---

