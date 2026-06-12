---
title: "Partitions on new dual-boot system"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by JimNSB on 2007-06-16
Hi, first post.

Built a new system yesterday (E6600, GA-965P-DS3 mobo, 2gb RAM, single 320g SATA hd), installed Win2K on a 40gb partition, and left the remaining ~250gb unallocated for Ubuntu and a '*files*' partition.  I want to access (read/write) '*files*' using either OS, and after reading suggestions on several sites I'm unsure which is the best way to go:[LIST]
[*]Use Win2k to create '*files*' as a FAT32 formatted logical drive (extended partition), and then install Ubuntu's partitions (root, swap, user) in the remaining space.
[*]Use the Ubuntu installer[COLOR="Blue"]*[/COLOR] to make the Ubuntu partitions, and also to create the '*files*' partition (formatted as ext3), then install and use *Ext2 IFS* ([http://www.fs-driver.org/](http://www.fs-driver.org/)) to access those partitions from Win2k.
[*]Another route?[/LIST]

[COLOR="Blue"]*[/COLOR]I have both the *desktop* and *alternate* CDs, and seen numerous suggestions to use *gparted*: which should I use?


Unrelated, but what size should I make the swap partition?  The system has 2gb of RAM in dual channel, and I do alot of memory-intensive tasks (like video editing).

TIA

---

### Post by Pumalite on 2007-06-16
> **JimNSB said:**
> Hi, first post.

Built a new system yesterday (E6600, GA-965P-DS3 mobo, 2gb RAM, single 320g SATA hd), installed Win2K on a 40gb partition, and left the remaining ~250gb unallocated for Ubuntu and a '*files*' partition.  I want to access (read/write) '*files*' using either OS, and after reading suggestions on several sites I'm unsure which is the best way to go:[LIST]
[*]Use Win2k to create '*files*' as a FAT32 formatted logical drive (extended partition), and then install Ubuntu's partitions (root, swap, user) in the remaining space.
[*]Use the Ubuntu installer[COLOR="Blue"]*[/COLOR] to make the Ubuntu partitions, and also to create the '*files*' partition (formatted as ext3), then install and use *Ext2 IFS* ([http://www.fs-driver.org/](http://www.fs-driver.org/)) to access those partitions from Win2k.
[*]Another route?[/LIST]

[COLOR="Blue"]*[/COLOR]I have both the *desktop* and *alternate* CDs, and seen numerous suggestions to use *gparted*: which should I use?


Unrelated, but what size should I make the swap partition?  The system has 2gb of RAM in dual channel, and I do alot of memory-intensive tasks (like video editing).

TIA

Give 15GB to '/', 3GB to 'swap' and the rest to 'home'. Use Gparted.

---

### Post by JimNSB on 2007-06-16
> **Pumalite said:**
> Give 15GB to '/', 3GB to 'swap' and the rest to [COLOR="SeaGreen"]'home'[/COLOR]. Use Gparted.

Thanks; I forgot to mention that.  I'll be creating a '*home*' partition for progs and other things I'll want to 'persist' *down the road* (thru upgrades), but since I do alot of *torrent*'ing of huge files like TV series and movies, I want to keep those in a separate partition as well.  Thanks too for the Gparted *nod* ...I grabbed and burned the *LiveCD*.

While *Ext2 IFS* (full name = *Ext2 Installable File System For Windows*, version 1.10c) will give me full r/w access of files in ext3-formatted partitions when running Win2k, I'm still wondering if there are *more* advantages to formatting the 'files' partition as FAT32.  For instance, it seems adding/removing drives is a little '*touchy*' when running the *Ext2 IFS* program, and I have several USB HD's that I use quite often.  But I do like the '*journal*' feature of the ext3 file-system.

I researched this for a few days, and wound up with a '*tie*'. :confused:
But I'm a n00b and probably 'weighed' some of the *ups & downs* wrong.


...another *piggyback* question: I've already installed Win2k, but when creating these remaining partitions is their a required/preferred 'sequence' I should (need to) follow? 

thanks

---

### Post by floke on 2007-06-16
I'd use FAT32 for shared file space. And don't use 3g for swap - its a complete waste. 1g is more than enough.

---

### Post by logos34 on 2007-06-16
> And don't use 3g for swap - its a complete waste

I second  that.  With 2gb of ram you'll probably never even use swap.

But FAT32 fragments more easily and has a 4GB file size limit (so no big video files, image/ghost backups, etc)...

---

### Post by Pumalite on 2007-06-16
> **logos34 said:**
> I second  that.  With 2gb of ram you'll probably never even use swap.

But FAT32 fragments more easily and has a 4GB file size limit (so no big video files, image/ghost backups, etc)...

The rule is: one or one and a half times your RAM. But, they are right you have a lot of RAM, nevertheless, it depends a lot on what kind of activities you get involved in. If you are a heavy video coder and transcoder, then its nice to have 2GB of swap. Also if you work with any kind of very large files. Decompressing very large files, etc. Especially if you have a very large hard drive.

---

### Post by JimNSB on 2007-06-16
I'm trying to figure out why my install failed:> -used GParted to create and format these partitions in the free-space following my Win2k partition:
[LIST]
[*][COLOR="Blue"]/[/COLOR] (primary, ext3)
[*]extended partition with [COLOR="Blue"]/windows[/COLOR] (FAT32) and [COLOR="Blue"]/home[/COLOR] (ext3) logical drives
[*][COLOR="Blue"]swap file[/COLOR]
[/LIST]
-used the alternate CD to complete the partition setup ('manual') and then install
-install went OK till "*choosing and installing software*" (red screen; almost immediately)
-retried that step a couple times (same result), then selected the next step (GRUB) which seemed to install
-selected 'finish'
-on reboot I chose Ubuntu from the GRUB menu, but it didn't start-up ...just a prompt: (username)@(computername)$

I retried installing with the alternateCD, and noticed something odd during the (manual) partition step.
The table listing the partitions I previously created looked like this:[LIST]
[*]SCSI3 (0,0,0):
[*]#1 pri (size) B K nfts [COLOR="Blue"]/media[/COLOR]/sda1
[*]#2 pri (size)  . K ext3 [COLOR="Blue"]/media[/COLOR]/sda2
[*]#5 log (size) . K ext3 [COLOR="Blue"]/media[/COLOR]/sda5
[*]#6 log (size)  . K FAT32 [COLOR="Blue"]/media[/COLOR]/sda6
[*]#4 pri (size)  .  K swap[/LIST]

Could that /media entry in the path (which I assume Win2k created in the original partition) be the culprit?

---

### Post by JimNSB on 2007-06-17
I restarted the installation (alternateCD), recreated and reformatted the partitions, but the installation kept spawning red-screens (at the 'choosing/installing programs' step).  After 5-6 attempts I tried using the 'rescue' selection; it seemed to take me a bit further, but after a long period of HD & CD activity the installation again went to a red-screen during the same step (choosing progs).

Then the inevitable happened: I *accidentally* clicked on the LILO booter during another attempt and no longer get a GRUB screen on startup.  I tried 'reinstall GRUB' (in 'rescue') several times, but no-joy.

Can anyone offer some guidance on how to get my Win2k installation to start?

(BTW, I was using this guide [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm))

---

### Post by Pumalite on 2007-06-17
> **JimNSB said:**
> I restarted the installation (alternateCD), recreated and reformatted the partitions, but the installation kept spawning red-screens (at the 'choosing/installing programs' step).  After 5-6 attempts I tried using the 'rescue' selection; it seemed to take me a bit further, but after a long period of HD & CD activity the installation again went to a red-screen during the same step (choosing progs).

Then the inevitable happened: I *accidentally* clicked on the LILO booter during another attempt and no longer get a GRUB screen on startup.  I tried 'reinstall GRUB' (in 'rescue') several times, but no-joy.

Can anyone offer some guidance on how to get my Win2k installation to start?

(BTW, I was using this guide [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm))

Use Gparted again and this time do the largest partition that you can and format it ext3. Then install. Give the installer the option: Guided Largest Available Space.

---

### Post by JimNSB on 2007-06-17
> **Pumalite said:**
> Use Gparted again and this time do the largest partition that you can and format it ext3. Then install. Give the installer the option: Guided Largest Available Space.

I was just returning to post additional info and saw your reply... before I try that please look at what I found ...if you still think I should try it I'll give it a shot:

I just checked the HD using GParted (from the DesktopCD); upon launching the prog an error box appeared: *Cannot mount volume* (*Details: mount: wrong fs typr, bad option, bad superblock on /dev/sda1 ; missing codepage or other error*).  
-does that mean Ubuntu somehow got installed (and is trying to launch from) my Win2k/NFTS partition???

Also, it shows an exclamation-mark next to my first (Win2k/NFTS) partition  ...'info' says:

[I]failed to startup volume : invalid argument
failed to mount device '/dev/sda1' : invalid argument [/I]

(originally, that partition was shown as /media/sda1 ...did it somehow get changed?)

How should I proceed?

---

### Post by JimNSB on 2007-06-17
Using the steps here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I now get a GRUB menu, but only Ubuntu and recovery-mode are listed.

Could these install problems be stemming from my SATA (not IDE) HD?

---

### Post by JimNSB on 2007-06-17
Booted from my Win2k CD and entered recovery-console.
I typed 'DIR' at the c: prompt (to see what was there) and got "an error occurred during directory enumeration"

At this point I'd really like to save my Win2k installation (instead of spending Father's Day scrubbing the HD and installing/updating from scratch!) ...could FIXMBR/FIXBOOT get it back up?

Since I'll be starting my Ubuntu install from scratch losing the GRUB menu won't matter.

TIA

---

### Post by Pumalite on 2007-06-17
> **JimNSB said:**
> Booted from my Win2k CD and entered recovery-console.
I typed 'DIR' at the c: prompt (to see what was there) and got "an error occurred during directory enumeration"

At this point I'd really like to save my Win2k installation (instead of spending Father's Day scrubbing the HD and installing/updating from scratch!) ...could FIXMBR/FIXBOOT get it back up?

Since I'll be starting my Ubuntu install from scratch losing the GRUB menu won't matter.

TIA

You could boot your windows cd>Recovery>fixmbr. But I think your problems are more profound at this point. Try fixmbr and report back with results.

---

### Post by JimNSB on 2007-06-17
Ran FIXMBR: was warned of a 'non-standard or invalid' item, but proceeded and MBR was rewritten.  Upon reboot Grub _still_ launched ...I hit Esc to enter the menu, which still only shows Ubuntu and recovery-mode.  

Will FIXBOOT be of any help?  Any way to manually remove GRUB & restore Win2k's MBR?  I'd rather spend an hour or two at recovery-attempts vs. losing the rest of the weekend to a scrub/reinstall! <g>

> **Pumalite said:**
> But I think your problems are more profound at this point
Sadly, from what I just learned, it looks you're right. :(
While scanning thru mounds of info in order to fix all this, I BELATEDLY found this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)

...seems my new 965P mobo and Ubuntu '*do not get along*' ...supposedly the problem was fixed (in Edgy, if I read it right), but its still being reported with Feisty.  Is there a workaround/solution, or is my hardware[COLOR="Blue"]*[/COLOR] incompatible with Ubuntu?



[COLOR="Blue"]*[/COLOR]My SATA HD is connected via the ICH8-controlled port, but my optical drive use the (affected) IDE connections ...which might explain why my installation kept failing when data was being retrieved from the install-disks.

---

### Post by mrphantastic on 2007-06-17
Hey JimNSB, I sent you a PM regarding your issue, it may be the only way to solve this big problem you have going down here...a sort of fresh-ish start...check the links...

---

### Post by JimNSB on 2007-06-17
> **mrphantastic said:**
> Hey JimNSB, I sent you a PM regarding your issue, it may be the only way to solve this big problem you have going down here...a sort of fresh-ish start...check the links...

Thanks bro, but my system has only one HD; when I add another I'll be sure to give your guide a shot.

---

### Post by mrphantastic on 2007-06-17
Ahh...well, sorry about that...maybe I should set up another guide...that could be usefull too, eh?

---

### Post by JimNSB on 2007-06-17
Tried FIXBOOT & FIXMBR: my Win2k installation is now in doggie heaven...

The irony is that I planned and built this system to give Ubuntu (and dual booting) a test-drive.

Back to the drawing board! ;)

---

### Post by Pumalite on 2007-06-17
> **JimNSB said:**
> Tried FIXBOOT & FIXMBR: my Win2k installation is now in doggie heaven...

The irony is that I planned and built this system to give Ubuntu (and dual booting) a test-drive.

Back to the drawing board! ;)

There are a number of things you could do with Ultimate Boot Rescue CD ( google it )(ubcd) regarding Windows. Give it a try. I hope you have access to another computer. It's a 214MB download. You can also try True Image; create a rescue cd and TrueImage your entire Windows to an external drive.

---

### Post by JimNSB on 2007-06-18
> **Pumalite said:**
> There are a number of things you could do with Ultimate Boot Rescue CD ( google it )(ubcd) regarding Windows. Give it a try. I hope you have access to another computer. It's a 214MB download. You can also try True Image; create a rescue cd and TrueImage your entire Windows to an external drive.

Since it just arrived Friday, I'm giving serious thought to returning the 965P mobo I used in the new system (a Gigabyte GA-965P-DS3, rev 3.3) ...but anything suitable for my C2D E6600 looks like it might suffer from the same bugs.  Intel's decision to go 100% SATA seems to have forced manufacturers to '*wing it*' (with components like the JMicron controller chip) in order to supply the features buyers want.

Any suggestions as to an Ubuntu-friendly chipset, one worthy of slapping a C2D onto?

---

### Post by Pumalite on 2007-06-18
> **JimNSB said:**
> Since it just arrived Friday, I'm giving serious thought to returning the 965P mobo I used in the new system (a Gigabyte GA-965P-DS3, rev 3.3) ...but anything suitable for my C2D E6600 looks like it might suffer from the same bugs.  Intel's decision to go 100% SATA seems to have forced manufacturers to '*wing it*' (with components like the JMicron controller chip) in order to supply the features buyers want.

Any suggestions as to an Ubuntu-friendly chipset, one worthy of slapping a C2D onto?

Intel Desktop Board D975XBX Don't use Raid Arrays on your SATA drives.

---

