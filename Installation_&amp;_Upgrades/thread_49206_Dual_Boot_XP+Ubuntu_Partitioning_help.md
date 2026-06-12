---
title: "Dual Boot: XP+Ubuntu: Partitioning help"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by Aikon- on 2005-07-15
First let me lay the groundwork. I am quite experienced with computer hardware, as well as various versions of MS Windows. I am, however, very new to Linux, with my only experience being on the RedHat terminals in the Engineering Computing Facility labs at the University of Toronto.

The background:
   I am currently running Windows XP on a 40GB Maxtor hard drive, with a full-size NTFS partition. I currently have ~55% free space. I want to dual boot XP and Ubuntu. I don't need alot of space because I really just want to use Ubuntu as a sandbox, to get my feet wet with Linux, so to speak. My original plan was to resize my NTFS partition to around 30GB, leaving 10GB for Linux (ignore all the x1024 factors.. 3/4 Windows, 1/4 Linux).

The problem:
   After fighting with the disk defragmenter included in XP, I downloaded Diskeeper 9 and ran it several times on this drive. End result: 0% fragmentation, blazing fast speed, everything at the start of the drive, EXCEPT for a large chunk of data that Diskeeper simply will not move. It is not a paging file, nor any system files (according to both defragmenters), however neither will move this block of data towards the start of the partition.
   When I try to resize my NTFS partition (using QtParted as included in Knoppix 3.3), I get an error message along the lines of "Partition fragmented. Defragment partition or try resizing to 34243MB"  This leaves only ~3.8GB of free space on which to install Linux.

The question:
   Since this is just going to be a sandbox installation anyway, should I just go ahead and install Ubuntu on the 3.8GB free space, i.e. IS this enough for a generic install (accepting performance decrease due to lack of excess space)?
   Or is there some way to force the moving of this block of data towards the beginning of the partition, allowing QtParted to resize the NTFS partition as I had originally planned?
   Or should I can the whole thing and wait until the next time I reformat my computer and set the partitions up right from the get-go (which won't be until around Christmas, from the look of things...)?

Any and all suggestions are welcome.. I'm looking for advice here. Questions, comments, concerns, opinions, whatever.

Much thanks,

-Scott

---

### Post by jc3835 on 2005-07-15
I use Acronis partition expert for partitioning under Windows... hasn't failed me yet. I think it was $30 or so when I bought it. It lets me resize drive partitions even if there is data at the end of the drive, as long as the drive isn't completely full.
Partition Magic is another program others have used.
Have you turned your paging file off and rebooted before defragging? I know you said it wasn't the paging file, but I thought I'd ask that anyway.

---

### Post by Aikon- on 2005-07-15
[QUOTE=jc3835]Have you turned your paging file off and rebooted before defragging? I know you said it wasn't the paging file, but I thought I'd ask that anyway.[/QUOTE]

Not at first, but once I started using Diskeeper 9, it showed the paging file in a different color, and I saw that it was also found at the end of the partition, immediately before these now-stubborn files.

So I disabled to paging file for that drive and set a temporary one on my storage drive. I then rebooted, ran Diskeeper 9 again, it cleared up a bunch of loose files that had been found near where the paging file *was*, but it didn't move that one big chunk that's still there.

Further question:
Is there a way to determine precisely which file(s) is(are) located there? If I knew what it was, I could just move it to my storage drive for the time-being.. Presuming of course that its not, say, the Windows folder  :wink:

-Scott

---

### Post by jc3835 on 2005-07-15
I doubt it's the windows folder  :wink: 
I don't know of any way to find out what files/folders the chunk actually is, no.
Run check disk prior to defragmenting again... sometimes that will clean up corrupted files that may be un-movable.
I've heard problems arising from the hibernation file... hiberfil.sys or something similar.

O&O makes a defragmenter that I have heard success stories about, fixing problems that Diskeeper could not. Might be worth a look to see if you can "borrow" a copy of O&O.

How many times have you run Diskeeper? Keep running it, see if there's any improvement. Also, the last install of Windows you did... was it over an existing installation or did you reformat the entire disk before the reinstall?

---

### Post by Aikon- on 2005-07-15
I've run Diskeeper multiple times, such that its gotten to the point where it says I have 0 fragmented files and 0 fragmented folders.. When I click "Defragment", it analyzes the partition, displays "Searching..." for 0.5s, then completes and says "Defragmentation successful!".

I've never used the "Hibernate" option with this install.. would that file still be generated?

This was a clean install, and not just a format of the drive but a MOBO-layer low-level format.

I'm just about to leave work for home; I'll give that program you suggested a try and see if I can't get this thing to behave itself.

---

### Post by jc3835 on 2005-07-15
I have seen cases where the hibernate file has been there and caused problems even if the user was not using (or not thinking they were using) hibernation. Might be worth a look at least.

Just save your data and wipe that sucker clean and start fresh!  :-P 

Good luck.

---

### Post by redwinder on 2005-07-15
hello, i also need help with xp and ubuntu i can not boot windows xp with the grub. i first installed windows xp with the installator i partitioned the disk in two one with 30 gb and the other with 10gb i put windows in the 10gb partition wich is in the end of the disk. ok now i boot with ubuntu and with the installator i partition the 30gb in two 
one part with 29gb where ubuntu was installed and a 700mb fat partition to change data between the two os. the disk was set up like this first the 29gb partition with ubuntu, then the 700mb fat partition and the 10gb partition with windows. now my question is this how do i get too boot windows xp and ubuntu with the grub without having to install everything again? i am new here and do not know much will you please help me.

---

### Post by jc3835 on 2005-07-15
[QUOTE=redwinder]hello, i also need help with xp and ubuntu i can not boot windows xp with the grub. i first installed windows xp with the installator i partitioned the disk in two one with 30 gb and the other with 10gb i put windows in the 10gb partition wich is in the end of the disk. ok now i boot with ubuntu and with the installator i partition the 30gb in two 
one part with 29gb where ubuntu was installed and a 700mb fat partition to change data between the two os. the disk was set up like this first the 29gb partition with ubuntu, then the 700mb fat partition and the 10gb partition with windows. now my question is this how do i get too boot windows xp and ubuntu with the grub without having to install everything again? i am new here and do not know much will you please help me.[/QUOTE]

I'm no GRUB expert, as I've had problems like this before, but I do know that Windows likes to be first on the HD.
I'm sure it's not impossible to get it working the way you have it, but I think it will be difficult.
There are a few other threads on this forums, including one in the HowTo section concerning GRUB issues.
Sorry I can't help anymore.

---

### Post by Aikon- on 2005-07-15
Okay we have a new development...

I said "screw it" and decided to go ahead and install Ubuntu into the ~4GB free space. Ok.

What happened:
1/     booted from the Ubuntu CD (5.04)
2/     hit RETURN at the prompt for a default installation
3/     menu came up asking for language, locale etc... picked that stuff
4/     installer went about its business loading modules etc.
5/     partitioner came up; I chose Guided-->Largest contiguous free space (i.e., the 4GB free space)
6/     commit changes.. it created a 250MB swap partition and the rest of the free space was formatted as an ext3 partition and set to "active" (I presume that's what the lightning bolt/smiley dealy is)
7/     installer goes about more business
8/     installer asks me if I want to install GRUB bootloader.. it lists my current operating systems as "Microsoft Windows XP Professional, Windows NT/2000/XP (loader)" (or something very similar to that).
9/     I say sure, so it installs GRUB.
10/   installer finishes all its stuff, tells me to remove the CD and then say okay
11/   the computer reboots, posts, detects all drives properly, and then displays the message "Error loading operating system" without giving me any options.
12/   Since this is the same thing that happened a few weeks ago (and I panicked but was able to fix it after a while), I loaded my Knoppix live CD and used QtParted to switch the active partition from the ext3 partition to the original (resized) NTFS partition
13/   removed the CD, rebooted the computer, and it booted into Windows fine, no problems


AGH

I would ***really*** like to get into Linux.. from what I hear its GREAT, but I must agree that its little stuff like this that reeeeeaaaaally throws people off = \

---

### Post by Aikon- on 2005-07-15
*BUMP*

Anyone else have any ideas?

---

### Post by DancingSun on 2005-07-15
Don't use the guided partition.

Instead:
[list=1]
[*]Go to the manual partition screen.
[*]Select the free space.
[*]And choose to automatically allocate the Linux partitions.
[*]The partitioner should make a "/" and "swap" partition for Ubuntu.  But at the same time, it will mark the "/" partition as primary and bootable (that lightning symbol).  Select the NTFS partition, and choose to make the NTFS partition bootable.
[*]This should move the lighting symbol to the NTFS partition.  Accept changes and continue the install.
[/list]

I don't know if this happens when doing a dual boot install with other Linux's or not, but apparantly, Windows like to be the boss and wants to be bootable.

---

### Post by Aikon- on 2005-07-16
[QUOTE=DancingSun]I don't know if this happens when doing a dual boot install with other Linux's or not, but apparantly, Windows like to be the boss and wants to be bootable.[/QUOTE]

Okay, that does make sense (not that "making sense" is necessarily a sign of being on the right track  :wink: )..

Its late, but I'm bored, and abandoned for the evening, so what the deuce, I'll give it a try.

Let you know in a bit how it turned out..

---

### Post by Aikon- on 2005-07-16
Okay here we go..

I followed the adivce in the post above (by DancingSun), setting the NTFS partition to be bootable, hoping that with that set, the GRUB bootloader would install itself appropriatel.

The installer finished its initial setup, asked me to remove the CD and reboot. Upon rebooting, I skipped right past the POST, meaning no "Error loading operating system" error message, and my heart skipped a beat, praying that it had finally worked.. and then the XP boot screen came up.

It would appear that the only difference following this advice made was that I didn't have to go in and manually change the NTFS partition to active after it didn't work.

It would appear that for some reason the BIOS is seeing the Windows native bootloader as the disk's bootloader.. I don't know alot about these things though. Is there some way to force the BIOS into using the GRUB bootloader instead of the Windows one?

---

### Post by DancingSun on 2005-07-16
Hmm... :?   I could've sworn that's the settings I used to install my dual boot XP-Ubuntu system.  Although, I went ahead and manually setup the "/" and a "/home" partition.  I skipped creating the "swap" partition because I have 1 GB of RAM and think that should be plenty.  Both "/" and the NTFS are primary, while "/home" is logical.

Are you sure you installed GRUB over the MBR?  If you did, that's what the BIOS should see.  I would think that when you install GRUB on the MBR, it will overwrite the Windows bootloader.  When you get the no OS detected error, did you [restore](http://www.wown.com/j_helmig/wxprcons.htm)  the Windows bootloader?  Although I never had to deal with that problem (yet), many posts in the forum will point you to restoring the Windows bootloader fix that problem.

What happens if you try to re-install with "/" set as bootable?

---

### Post by Aikon- on 2005-07-16
[QUOTE=DancingSun]Hmm... :?   I could've sworn that's the settings I used to install my dual boot XP-Ubuntu system.  Although, I went ahead and manually setup the "/" and a "/home" partition.  I skipped creating the "swap" partition because I have 1 GB of RAM and think that should be plenty.  Both "/" and the NTFS are primary, while "/home" is logical.

Are you sure you installed GRUB over the MBR?  If you did, that's what the BIOS should see.  I would think that when you install GRUB on the MBR, it will overwrite the Windows bootloader.  When you get the no OS detected error, did you [restore](http://www.wown.com/j_helmig/wxprcons.htm)  the Windows bootloader?  Although I never had to deal with that problem (yet), many posts in the forum will point you to restoring the Windows bootloader fix that problem.

What happens if you try to re-install with "/" set as bootable?[/QUOTE]
 First, just a quick clarification.. I'm not getting a "no OS detected" error, I'm getting an "Error loading operating system" error. Very similary but they (I think, anyway) mean something slightly different.

No, I did not restore the Windows bootloader. In order to boot back into Windows again, all I have to do is:
1/     Reboot with my Knoppix 3.3 CD in the drive
2/     User QtParted to set the NTFS partition as primary
3/     Reboot and it works

As for whether or not I'm installing GRUB over the MBR, that's a good question, and I think the answer is "no"...  The GRUB installer comes up during the installation, says "I've detected these other operating systems. If they are all here you can probably go ahead okay." It lists "Microsoft Windows XP Professional" as well as "Microsoft Windows NT/2000/XP/2003 (loader)" (which I presume is Windows' boot loader?), which is indeed all that I have installed, so I say "Okay", and it says "Installing GRUB bootloader in the MBR...", then it completes and does the rest of the installation.

If I re-install with "/" set as bootable, I get the original problem, fixed by my original fix (of using QtParted to set NTFS as primary).

---

### Post by Aikon- on 2005-07-16
[QUOTE=Aikon-]First, just a quick clarification.. I'm not getting a "no OS detected" error, I'm getting an "Error loading operating system" error. Very similary but they (I think, anyway) mean something slightly different.

No, I did not restore the Windows bootloader. In order to boot back into Windows again, all I have to do is:
1/     Reboot with my Knoppix 3.3 CD in the drive
2/     User QtParted to set the NTFS partition as primary
3/     Reboot and it works

As for whether or not I'm installing GRUB over the MBR, that's a good question, and I think the answer is "no"...  The GRUB installer comes up during the installation, says "I've detected these other operating systems. If they are all here you can probably go ahead okay." It lists "Microsoft Windows XP Professional" as well as "Microsoft Windows NT/2000/XP/2003 (loader)" (which I presume is Windows' boot loader?), which is indeed all that I have installed, so I say "Okay", and it says "Installing GRUB bootloader in the MBR...", then it completes and does the rest of the installation.

If I re-install with "/" set as bootable, I get the original problem, fixed by my original fix (of using QtParted to set NTFS as primary).[/QUOTE]
 Sigh..
Well, This is proving much more difficult than I had hoped.
I've also read good things about SUSE, specifically that it plays nicely with XP, so I'm going to give that a try and see if I can actually get it to dual boot.

---

### Post by irusun on 2005-07-16
You shouldn't be able to restore your mbr in the manner you're doing it - switching the boot flag shouldn't fix it.  Which as already mentioned, means that your mbr isn't being overwritten.

Check your BIOS for any "anti-virus" settings and turn those off - I've heard that they can prevent the mbr from being overwritten as well as causing other problems.

Or maybe it's something wrong with your hardware.

I think it's possible to chain-load Linux from the Windows boot menu, but I've never tried it.

It's a drag you're having such a hard time, but it's *really* not the fault of Linux.  If you do try to install SUSE, I'd imagine you'd have the same issue - but post back here on the results.

---

### Post by Aikon- on 2005-07-16
[QUOTE=irusun]You shouldn't be able to restore your mbr in the manner you're doing it - switching the boot flag shouldn't fix it.  Which as already mentioned, means that your mbr isn't being overwritten.

Check your BIOS for any "anti-virus" settings and turn those off - I've heard that they can prevent the mbr from being overwritten as well as causing other problems.

Or maybe it's something wrong with your hardware.

I think it's possible to chain-load Linux from the Windows boot menu, but I've never tried it.

It's a drag you're having such a hard time, but it's *really* not the fault of Linux.  If you do try to install SUSE, I'd imagine you'd have the same issue - but post back here on the results.[/QUOTE]
 Hrmm... Yes, I completely agree with you in that I don't think my MBR was being overwritten.

I had already turned off all that kind of stuff in my BIOS as per many tutorials, guides, and posts on the intraweb suggested.

I wiped the partitions Ubuntu had made (i.e. reset it back to the ~4GB of free space) and popped in a SuSE 9.1 Personal CD (I didn't want the hastle of downloading a whole DVD or 5/6 CD's for 9.3....) and went through its installation process (which, I might add is VERY nice with the UI they have set up.. rather intuitive). When it came to loading the GRUB, I went into custom settings. The default was "Overwrite MBR: No" and "Make boot partition active: No"... I switched tese values to "Overwirte MBR: Yes" and "Make boot partition active: Yes", clicked Finish, completed the setup, my computer rebooted, and it loaded the bootloader immediately, with the option of booting Linux or Windows (as well as Linux safe-mode, memtest, stuff like that). Booted Linux, finished configuring everything, and it worked beautifully..was playing around in it for about an hour.  Logged out, rebooted my computer, chose Windows instead of Linux in the bootloader, and XP loaded perfectly fine, no complaints.

It would appear that if I had the option of setting those advanced GRUB settings during the Ubuntu installation, I would probably be able to get that to work as well. sigh = \

---

### Post by Aikon- on 2005-07-16
Hmm.. The more I think about it, maybe if I now wipe the partitions made by SuSE, and install Ubuntu instead, if it will work since SuSE already set up the advanced properties of the MBR..

Perhaps I will try that later tonight.. Or, maybe I'll just stick with SuSE for now, use it to get used to Linux (since it actually works =P)

---

### Post by DancingSun on 2005-07-16
I have to agree what you're experiencing is very frustrating...I'm lucky that my installation went as smooth as a baby's butt.

What's odd is all these inconsistencies when installing Ubuntu.  From the forums, I've seen many posts about problems with dual boot installation.  So I did my homework, and spent around 2 weeks making sure I understand how this installation process works before I took the plunge.  Luckily, I didn't experience any of the problems that some of the unfortunate forumers did.

If I recalled correctly, I also selected what you did for the GRUB installation part.  This is quite disturbing considered you receive no error messages during installation, correct?

Maybe you should search around the forums and the Internet for the specific symptoms that you are having.  I guess it's also possible that GRUB failed to install and that no error messages were prompted, if that's the case, then a bug filing should be in the order.

---

### Post by irusun on 2005-07-16
Aikon, thanks for updating us on your SUSE installation... that's how smoothly it's *suppose* to work.

That's really weird that SUSE worked and Ubuntu didn't... but sometimes that's the way it goes.  

I only briefly tried SUSE several years ago, but it's obviously considered an excellent distro.

Good luck with your Linux travels!

---

### Post by Aikon- on 2005-07-16
[QUOTE=irusun]Aikon, thanks for updating us on your SUSE installation... that's how smoothly it's *suppose* to work.

That's really weird that SUSE worked and Ubuntu didn't... but sometimes that's the way it goes.  

I only briefly tried SUSE several years ago, but it's obviously considered an excellent distro.

Good luck with your Linux travels![/QUOTE]
 Its unfortunate though.. SuSE feels just like every other Linux distro I've tried (mostly various Live CD's and my school's RedHat terminals)..

But the Ubuntu Live DVD I found absolutely wonderful.. everything just plain worked, it looked great, it was fast, easy to use.. just won't boot when I install it = \

At any rate, thank you all for your help, always helpful to have various ideas thrown around.

---

### Post by Skye on 2005-07-16
This is just a thought, but as to your original problem with resizing your windows partition, have you tried using the windows disk cleanup application to try to get rid of any unecessary stuff?  Also, have you tried deleting all of the previous system restore points- maybe just turning system restore off entirely?  In my experience, those system restore points tend to completely frag up a disk.

Ubuntu is a wonderful distro- I had the reverse of the problem you're having; I installed windows XP (for games, and only games) after Ubuntu, and recovering the MBR after windows screwed it over was difficult, but not so much so as the problems you're having.

If i were you, i'd keep trying for Ubuntu- I've heard that Suse is nice, but Ubuntu is better.

---

### Post by Aikon- on 2005-07-16
The disk cleanup has nothing to clean since I keep my OS tidy anyway, and I don't use restore points = \  Good thought though!

Its weird.. as I understand it, KDE in general, and SuSE in specific, are supposed to be "easier" for Windows people to migrate to because they are "more similar" to Windows.. but playing in SuSE for a couple hours paled in comparison to what I could do in 5 minutes off the Ubuntu Live DVD; I felt right at home there! (as soon as I changed the theme to the blue one.. right beneath "Human".. very similar to my current Windows desktop, Souluna through Windowblinds)

I hope I can get it working.. my goal for September (when I go back to school) is to have switched to Linux entirely, keeping a small Windows partition only for gaming and loading my microcontrollers (although I could probably find a Linux version of the com drivers.. anyone have any experience with the PIC16F877?)

Anyway, I will keep fiddling with it..if I can pinpoint exactly what's going on, maybe we could even get it fixed so it doesn't happen anymore (although its most likely something highly specific to the setup I'm using) Oh well, we'll see!

---

### Post by Ragnar on 2005-07-17
I also found myself in knots at this stage.  I tried to compact my full-disk ntfs partion using Norton disk doctor and a whole wodge of stuff remained at the end of the partion.  Same with a freeware defragger.  XP's own defrag tool did best but still left an immovable lump about 3/4 the way up a mostly empty partition.  

I googled and found the Ntfsresize page that indicates that Ubuntu 5.04''s installer uses the most up-to-date tools for resizing ntfs, so that there should be no advantage in using any other partition manager. 

As I had my partition fully backed up I decided to risk resizing even though the partition didn't appear to be compacted.  It worked!  I resized my 30GB Toshiba HD ntsf partition to 11.2 GB and installed Ubuntu in the resulting free-space.  When I looked at the ntfs partition in the XP defragger, all the data appears to be in a nice compact lump at the start of the disk 4.25GB in my case, as I stripped as much as possible out before-hand.  (I also made a Fat32 partition right after the ntfs one for data that I might want to write to in both XP and Ubuntu).  So far everything appears to work, but I'm no expert, have never seen a Linux screen before yesterday, so I might be missing something ;-P.

---

### Post by Aikon- on 2005-07-17
OMG WTF PROGRESS

Okay, so after having installed SuSE (and having it work properly), I set up Ubuntu in the same way as the SuSE partitions had been set up (except using ext3 instead of ReiserFS), which, when I was finished, happened to be identical to how I was setting up the Ubuntu partitions in the FIRST place =\

So, I was very skeptical, and expected the exact same problem to show its ugly head.

But, much to my surprise, upon reboot, the GRUB came up with the options:

Ubuntu [...]
Ubuntu [...] (recovery-mode or whatever)
Ubuntu [...] memtest
Other OS:
Windows XP
Windows 2003 (loader)

So, I chose the top one to load Ubuntu and it gave me the following error:

[QUOTE=GRUB]
  Booting 'Ubuntu, kernel 2.6.10-5-k7 '

root (hd1,2)

Error 22: No such partition

Press any key to continue...
[/QUOTE]

So I press the "any" key, return the menu, choose XP and XP boots fine.

Recommendations?

---

### Post by Aikon- on 2005-07-17
no? no one knows? (bump)

---

### Post by Aikon- on 2005-07-17
wewt!
I am teh pwnernator

Problem was that I had an IDE drive and an SATA drive both plugged in.. IDE for storage, SATA with OSs.  GRUB was pointing to the IDE drive and looking for the boot files stored on the SATA drive.

By right, Windows should have been broken too.. the only reason it wasn't was that at one point, Server 2003 had been installed on that hard drive, so it had its own bootloader that pointed back to the SATA drive.

Stupid HDD complexity =P

Thanks again everyone for your help!  Time to get this baby purring..

---

### Post by DancingSun on 2005-07-17
Gah!! That was why! I should of asked you for you hardware configurations in the beginning! [-X 

Anyway, congrats for getting Ubuntu working!  :grin: 

And you might want to consider filing a "bug" or "RFE" on this issue, since SuSE works fine, but not Ubuntu.

---

### Post by jc3835 on 2005-07-28
You seem to be past the partitioning question that this thread was started on, but I wanted to give you an update on the software I recommended...
I installed O&O defrag recently as I too was having issues with fragments at the end of lots of free space that weren't defragging as I would assume they should. O&O worked GREAT in getting rid of those. Diskeeper was not doing anything more, but O&O did everything. It's also a LOT faster than Diskeeper, plus it has a cooler interface :)
Anyway... just thought I'd share that experience and let you know I solved the initial problem we were having in this thread. :-D

JC

---

