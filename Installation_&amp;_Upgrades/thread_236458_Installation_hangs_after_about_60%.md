---
title: "Installation hangs after about 60%"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by cvanp11 on 2006-08-14
Hey all I have a pretty weird problem.

I'm running a Compaq Presario SR1120NX desktop computer.  Not the greatest but it gets the job done.  I finally cleared off space so I wanted to do a dual-boot of Ubuntu and Windows XP.

I popped in my CD and no matter how many times I pressed "Start/install Ubuntu" it would just restart.  A few google searches later led me to add "acpi=off" to my boot options which made the CD finally boot into the live CD.

So it's on the live CD now which is great.  I go through the install and set up my partitions (manually, I was guided by a friend who has Ubuntu) and the partitions get made.  Install starts.  The first thing that happens is that it complains about my D:/ drive having errors or something like that (obviously it doesn't call it D:/ drive).  This drive is the backup partition that came preinstalled when I got the computer, and as far as I know most major OEMs do this.  I just pressed continue and let the installation go.

Around 65% (may have been more or less) the installation abruptly came to a halt.  It didn't close out or show any sign of stopping other than the fact that for the next half hour nothing changed.

I turned off my computer and used a pin to open my CD drive.  Fortunately Windows was untouched although it did want to do a disk check which came up with nothing wrong (I think it just needed to verify the partition).  I should note that I tried the normal Live CD twice, and got the same result, exactly, twice.

I then was advised to try the text-only mode of the Alternate Install CD.  Again, I had to have "acpi=off" in Boot Options.  I was able to navigate through that well enough though I did come up with another error (it had something to do with decompressing or unpackaging, something of that nature).  It progressed normally up to 64% where it, again, stopped.  This time though, I saw it was "Configuring linux-sound-base" at this point.

I honestly don't know what is going on here.  Since this seems to stop at something sound related I dug up sound info, and it appears I have Realtek AC97 drivers and because it's a Compaq and they assume computer stupidity I can't really find more than that.

Thanks if someone can help!

Chris

---

### Post by John.Michael.Kane on 2006-08-14
Have you ran md5 checks on the cd's. also have you tried to burn the iso at a slower speed?

---

### Post by cvanp11 on 2006-08-14
I never MD5 checked it or tried burning at a slower speed, my cd app can't do that.  I did however use the tool on the alternative install CD that verifies disk contents and that went through successfully.

---

### Post by knoot on 2007-04-16
I had the same problem trying to install Xubuntu (alternate CD, text mode) on a low mem pentium 100 Mhz. Everything goes well until it reaches 65% in the final installation proces, then nothing changes, even after hours.

---

### Post by scradock on 2007-04-17
Sounds like the same problem I asked about a couple of days ago.

Does anyone have any useful suggestions? I have tried checking the LiveCD, using the alternate install CD. The (older eMachines T1840) desktop machine simply stalls after 60% or so of the install.

I have a 4GB Linux ext3 partition, plus a 600MB Linux swap partition. RAM is only 384 MB. Runs Windows XP Home fine, but it's getting slow with all the virus-checking needed these days, so I want to run Ubuntu........

Could someone who knows what happens during install help us? The partial install is no help, because it doesn't progress far enough to set up Grub or modify the MBR. The only way out is to power off and try again, which simply starts from the beginning, and stalls again.

Sc

---

### Post by cheng on 2007-04-17
i had stalling problem too.
this was because i disabled swap disk.

i was using a via epia sp1300 with 256MB ram.
even this wasn't sufficient!

you guys might want to look at the memory issue.
or check if swap was indeed created during install.

---

### Post by murrayjc on 2007-04-18
Exactly the same problem here. I'm trying to create a dual boot system with win XP and Ubuntu. My partitions are (in order): 50 MB FAT16 (Bootmagic), 29 GB NTFS (win XP), 500 MB Linux Swap, 7.5 GB Ext3 (Ubuntu root). My proc is a Pentium 3, 1.13 GHz and I have 384 MB of RAM. During Ubuntu install, I created the swap and Ext3 partitions and told it to only mount those two (as "swap" an "/" ). Install hangs while "copying files" at 66%. Based on everybody else's posts, I'm not inclined to believe that repeating this process will fix the problem... Can anyone see a problem with what I'm doing? Problem with memory? Problem with Edgy, fixed with Feisty? Thanks,
Jon

---

### Post by badboy_24u on 2007-04-18
[SIZE="3"]I also had that same problem when i first install ubuntu. I think i've tried 6-7 times of installation before it finally worked. And heres what i've notice during those failed installations. Always check if your pc is already too hot. especially your RAM. Coz ubuntu installation most of the time if just running completely trgough it. So, if your RAM is too hot already, chances are it will hang or crash. Second is your Electricity. Check if its current is running smoothly and stably. Coz it contributes a lot to your whole system. And third, of course is your Installation CD. Check it using ubuntu's built-in diagnostic program for cd defects. 
[/SIZE]

---

### Post by murrayjc on 2007-04-21
I was never able to burn the CD image and pass the CD error check provided on the CD. I don't know why... But I just borrowed my friends CD that did pass error check and that fixed the install hanging issue for me... An obvious answer, I suppose.

---

### Post by knoot on 2007-04-29
My CD also failed two times, but trying a different brand recordable CD helped and the checksum was succesfull. I wonder how many disk space the installation needs, since the pc I tried installing Xubuntu on had only about 2 Gb for a root partition so maybe the disk was full? I also thought that the pc might have gotten too warm, but I still need to try cooling it during installation.

---

### Post by steen_jensen on 2007-05-01
I have tried to make an install with Xunbuntu aternate cd  alone no Windows. The iso as well as the cd has been md5sum checked ok. I have only chosen my language but otherwise followed the suggestions from Xubnutu. My internet connection is 10mb/10mb why it is not a question of download speed. And no problems with heat or electiricty. Last time I tried to install I broke the installation after 12 hours as it had stopped at 65%. I have made a bug report but heard nothing up till now.

---

