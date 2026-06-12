---
title: "Ubuntu 9.10 won't install grub"
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Gina on 2009-11-14
I have been trying to install 9.10 onto my P4 machine and I just cannot get it to install the grub2 boot loader - either into the MBR or into the partition containing the system. The reason for trying the latter was to enable me to dual boot with earlier versions. I get a message near the end of installing saying that it can't install the grub boot loader and that the system will therefore not boot (or words to that effect).

I'm afraid I'm stumped and would much appreciate some help - thank you :)

---

### Post by ranch hand on 2009-11-14
Is this a clean install or an upgrade?

How big is this drive?

How many OS' on the drive?

---

### Post by Gina on 2009-11-14
Clean install into a 20GB partition on 250GB HD, separate /home partition (existing) also of 20GB.  There is over 50GB unused space.  There are 3 or 4 other OSs - one is Win XP the others are versions of Ubuntu.

---

### Post by ranch hand on 2009-11-14
Sounds good.  Should work.

I really do not see why this is not working.  Your setup sounds like the ideal grub2 environment.

The only thing that I can think of right now is the /home partition.  I take it that this is shared with one or more other OS'.

Assuming that I am correct in that, did you create a unique user name for 9.10?

I am not sure what config files could be  screwing things up, but 9.10 has a lot of differences that we do not see right off the bat.

---

### Post by Gina on 2009-11-14
I used the same user name and password as before.  This is what I always do when I install a new version but keep my /home.

If using the same /home partition might be a problem, I can try a new one or leave home in the system partition.

Thank you for your reply :)

---

### Post by ranch hand on 2009-11-14
That might be the thing to do.  I think that using a different user name would take care of it but, as strange as this is, just doing a clean install by itself may be best.

---

### Post by Gina on 2009-11-14
Just tried installing again into sda12 (with format) and not setting up a separate /home partition. In "Advanced" I set it to put grub in sda12 and ran the Install.  Still get the same error at 95% done when it tries to install "grub-pc".  See attached screenshot.

---

### Post by ranch hand on 2009-11-14
Good God what is up here?  This makes no sense at all.

I would have installed grub on the MBR but I am sure that this would have made no difference in your out come at all.

Grasping at straws here - did you check the md5sum of the ISO?

---

### Post by Gina on 2009-11-14
Yes, I checked the md5sum and also ran the CD Test on the DVD I used to install from - both passed.

I've also tried installing grub2 from the desktop system and get the following :-> ubuntu@ubuntu:~$ sudo grub-install /dev/sda12
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ Maybe this might cast some light on the situation?

---

### Post by Gina on 2009-11-14
The reason for using the system partition rather than the MBR is so that I can chainload to grub2 from legacy grub and have access to my older versions that use legacy grub.  I also want to be sure I can boot XP as I need that for certain things (unfortunately) and read somewhere that the 9.10 install won't add the link to load Windows.

---

### Post by SevenMachines on 2009-11-14
maybe have a look at /boot/grub/device.map and see if it looks right. perhaps regenerating it automatically will help
$ sudo grub-mkdevicemap

---

### Post by ranch hand on 2009-11-14
Grub2 actually gets along with MS very well.  In a few instances it will not  be on the menu when you reboot from installation.  Running "sudo update-grub" generally fixes that.

I knew you had checked that stuff.  I was just hoping you hadn't.

We need to start over.  Run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

from Live CD or Ubuntu with ext4 support on drive.

---

### Post by kansasnoob on 2009-11-14
> **ranch hand said:**
> Grub2 actually gets along with MS very well.  In a few instances it will not  be on the menu when you reboot from installation.  Running "sudo update-grub" generally fixes that.

I knew you had checked that stuff.  I was just hoping you hadn't.

We need to start over.  Run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

from Live CD or Ubuntu with ext4 support on drive.

+1!

But I'd also be curious to see what happens if at that last step during installation the person installing chose to NOT install grub.

Of course then they'd not be able to boot unless they mount and chroot from the Live Desktop and revert to legacy grub.

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

To apply those steps from the Live CD see Appendix #1 which needs to be rewritten rather than just being a link to another page.

---

### Post by Gina on 2009-11-14
> **ranch hand said:**
> Grub2 actually gets along with MS very well.  In a few instances it will not  be on the menu when you reboot from installation.  Running "sudo update-grub" generally fixes that.

I knew you had checked that stuff.  I was just hoping you hadn't.

We need to start over.  Run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

from Live CD or Ubuntu with ext4 support on drive.Thanks very much for your reply :)  I'll check it out tomorrow, it's nearing bedtime here.

---

### Post by Gina on 2009-11-14
Thanks for the other replies too :)

---

### Post by ranch hand on 2009-11-14
We may end up going to grub-legacy to get this to work and the link kansasnoobb gave is the way to do it.

I want to give getting this straight one more whack.

The first 3 links in the post in my sig are to guys that can make grub2 sit up and beg.  I have kansasnoobs How To on there too because he can make it lay down and die.

He is real good at making it go too.

---

### Post by DougieFresh4U on 2009-11-14
Hi Gina ):P Long time no see you around here.
Not sure if this will help, but have you tried 'chroot' into other partitions via live-cd and updating grub on all other partitions?
Just a thought. :-k

---

### Post by kansasnoob on 2009-11-14
> **DougieFresh4U said:**
> Hi Gina ):P Long time no see you around here.
Not sure if this will help, but have you tried 'chroot' into other partitions via live-cd and updating grub on all other partitions?
Just a thought. :-k

It's a horrible idea to just randomly chroot partitions. While the process should just refuse to allow it bad things can happen when least expected.

If a box is dropped in your lap that you have no knowledge of it's best to use meierfra's Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

99% of the time that will provide the info needed to proceed.

---

### Post by ronacc on 2009-11-14
I wonder if this is related to my problem of the installer not wanting to put grub2 on the mbr of anything but sda ?

---

### Post by Tuig on 2009-11-15
Hi,

I also had problems installing grub. I tried to install it to /dev/sda5 which is also my root partition.
Since /dev/sda5 is mounting during install, or when you chroot
into it with a livecd, it doesn't work.

What I did was not very clean, but effective:
install grub onto another partition (or usb-stick),
then boot from a live-cd, to make sure that your root partition
is not mounted, and do a:

dd if=/dev/sdbX of=/dev/sda5 bs=512 count=1

---

### Post by Gina on 2009-11-15
I'm now back onto it :)  Thanks for the replies :)

To ***ranch hand*** - I've run the script and attach the RESULTS.txt file resulting.  This is rather big I'm afraid.  There are 3 hard drives with numerous partitions on each.  I've been meaning to sort this out as there's lots of old stuff I could dump but haven't got round to it yet.  Drives sdd,sde,and sdf are memory card readers.  I have some more info in my sig about this P4 desktop.

---

### Post by Gina on 2009-11-15
> **DougieFresh4U said:**
> Hi Gina ):P Long time no see you around here.
Not sure if this will help, but have you tried 'chroot' into other partitions via live-cd and updating grub on all other partitions?
Just a thought. :-kHi Dougie :)  Not had time to do much testing - my "other half" has not been well and I've had a lot extra to do.  He's gradually getting better and I'm hoping to get involved in testing Lucid Lynx.

Thanks for your suggestion :)

---

### Post by garvinrick4 on 2009-11-15
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Hope it helps.

---

### Post by Gina on 2009-11-15
Further to RESULTS.txt...

I've examined this and it looks as I'd expect - I can't see anything obviously wrong.  OTOH I have some thoughts...

sda9 is the main 9.04 partition I use for Ubuntu.  It's where the MBR goes to find the menu list.  The first entry I added to chainload to sda12 where I installed Ubuntu 9.10.  Examination of the file system in that partition confirms it contains 9.10 I believe.

sda12 is where I asked it to put the grub2 loader but it would not do that.  During the installation it is the **/target/** and is mounted for the purpose of writing the system files into.  Question :- Does install-grub need to work with an **unmounted** partition?  Might this be the reason for failure?  OTOH I thought this was the method suggested elsewhere in Ubuntu Forums for getting round the problem of grub2 not being able to link to a legacy grub loader.  Though I think the author used a separate grub partition.

The installation is finding 2 swap partitions, one on sda and the other on sdc.  This has not caused any problem with 9.04 and earlier.

---

### Post by ranch hand on 2009-11-15
> **Gina said:**
> I'm now back onto it :)  Thanks for the replies :)

To ***ranch hand*** - I've run the script and attach the RESULTS.txt file resulting.  This is rather big I'm afraid.  There are 3 hard drives with numerous partitions on each.  I've been meaning to sort this out as there's lots of old stuff I could dump but haven't got round to it yet.  Drives sdd,sde,and sdf are memory card readers.  I have some more info in my sig about this P4 desktop.
I love your set up.

I should have run the script on my box at the end of 9.10testing (40 partitions on 4 HDD with 22 OS').   People do, for some reason, claim I am nuts.  Right now I cleaning things up (the drive I am using as my main needs reformatted) so I am way down.

You have everything extremely neat and functional.  I still am baffled about grub2 not installing.  I always go to the MBR but many people don't.  The only thing about your set up that should mess with grub2 is the number of old kernels.  I still think it is a set up made for grub2.

Grub2 does not seem to agree with me.  I think that what I would do is go with kansasnoob s Tutorial on reverting to grub-legacy.  With the amount of stuff on board, all working well under 0.97, the various attempts to install 1.97beta4, all failing, why fight it?

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I am sorry that I am no more help than that.  I really had hoped to get it to work.  If it doesn't like your system (such a neat, working system) then I think changing grub versions is a lot better than changing your system.

---

### Post by Gina on 2009-11-15
> **garvinrick4 said:**
> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Hope it helps.Thanks for that :)  In fact I don't need to recover my boot loader - the legacy grub loader is still OK.  I've set it to chainload the 9.10 grub2 loader.  As I said, the problem is actually getting the grub2 loader into the 9.10 system partition.

In fact, I did TRY to get it to install grub2 into the MBR but it refused to do that too!

---

### Post by Gina on 2009-11-15
> **ranch hand said:**
> I love your set up.
----------------- snip -----------------
You have everything extremely neat and functional.Thanks for that - I thought it was rather a mess myself :lolflag:

The reason for trying to go with grub2 was to use 9.10 as a base for Lucid testing - yet still have my older systems available.  I'll think about your suggestion of using legacy grub instead.

Thanks very much for your help.  I thought this wasn't an easy one!!

I think I'll have a clean-up, or disconnect a couples of drives and see it that helps.  It would be nice to get grub2 working for testing.  Another thought... I could try installing it on my AMD64.  That has just the one 500GB drive and fewer OSs.  That would eliminate the possibility of it being hardware related - not that I think it is.

---

### Post by ranch hand on 2009-11-15
I run my testing on an external dual drive enclosure.  I turn off my internals when messing around with the testing OS'.

I am on it now.  10.04testing is my "main" OS for the daytime hours.

Last cycle I also used one of my internals.  It was the only drive "live" when I was on it too.  I will risk the hardware (don't feel a real threat there to my desktop box) but not my other drives and OS'.

---

### Post by Gina on 2009-11-16
> **ranch hand said:**
> I run my testing on an external dual drive enclosure.  I turn off my internals when messing around with the testing OS'.

I am on it now.  10.04testing is my "main" OS for the daytime hours.

Last cycle I also used one of my internals.  It was the only drive "live" when I was on it too.  I will risk the hardware (don't feel a real threat there to my desktop box) but not my other drives and OS'.How do you turn off your internals?  Do you disable them in th BIOS or something?  What's the best way?

I've decided I'm not going to be beaten by grub2 yet - the fight is on :lolflag:

I have a couple of ideas to try :)

I tried installing 9.10 on my AMD64 machine last night and it crashed near the end at "configuring grub".  I'll try again shortly.

Having read that the daily's are available, I'm downloading now with edited rsync script (karmic->lucid).

---

### Post by VMC on 2009-11-16
"P4 HT 3.2Ghz 1GB RAM 250GB IDE + 2x160GB SATA"

This is the setup that doesn't work?

Try this. I'm assuming the ide is the primary hd. Temporarily remove the sata hd's and see if you can then update grub2. If it installs correctly on the ide hd, than re-install the sata cables and when booted up, issue an update-grub and see if it passes.

---

### Post by alexfish on 2009-11-16
hi / been follow threads of installing and grub broblems
using a seperate external hard drive is good advice this is a i do /switch of the computer
open it up and disconect the sata cables the ( normaly red) from the harddrives
 if you have a hard drive thats spare and no valuable bits on it (no os or home directories you want) then use that drive make ensure that that power and sata cables are connected only to this drive if its a usb drive then ensure that the bios sees the drive and also can boot from a usb drive   reboot the computer and do a clean install 9.10 ive had no problems with ext4 but you have a option for ext3 ,see what happens

i've heard that there are issues with grub in 9.10 

have you been trying to install with ext3 or ext4 ?
also check the boot sequence of your hard drives in the bios
and also are the sata connections to the hard drives in the correct sequence on the motherboard like sata 0 ,1,2 3 etc .
Interested in finding the outcomes of this thread

---

### Post by kansasnoob on 2009-11-16
I see nothing wrong in the Boot Info Script. 

Actually quite a good job of installing everything, nicely done!

Just a thought, would you consider trying the Alternate CD?

It shouldn't be necessary but it's just a thought.

Another thought, if after installing and having grub2 fail to install from the Live CD, perhaps you could try to mount and chroot either from a Live CD or from another Ubuntu OS in your setup, then try to install grub2 basically like this:

> sudo mount /dev/sdXY /mnt (of course replaceXY with proper device # ie: sda1)
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf (may or may not be necessary to establish an internet connection)
sudo chroot /mnt
ls /boot (just to be sure /boot/grub exists, if it doesn't you'll need to "mkdir /boot/grub")
apt-get install grub-pc grub-common os-prober
update-grub
grub-install /dev/sdXY (of course replace XY with intended location for grub ie: sda for mbr of a disc or sda1 for specific partition)
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot (if you're ready to reboot)

Clear as mud????????????

---

### Post by oldfred on 2009-11-16
I know with my old motherboard and mixed Sata & Pata drives I had issues with old grub and boot order. BIOS, grub and Ubuntu did not agree. With my new motherboard I do not have that issue and now I am only SATA. I believe the issue is worse with new grub.

I installed grub2 to the partition as part of the install of alpha, I did not remember it giving me a warning then and have chainbooted from old grub into new grub without an issue. I now get the block list warning on just about every update as it reruns the grub update.

I believe blocklists are how old grub chainbooted.

Herman has info on reinstalling to a partition with a force command, You will get the blocklist warning:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

### Post by ranch hand on 2009-11-16
> **Gina said:**
> How do you turn off your internals?  Do you disable them in th BIOS or something?  What's the best way?

I've decided I'm not going to be beaten by grub2 yet - the fight is on :lolflag:

I have a couple of ideas to try :)

I tried installing 9.10 on my AMD64 machine last night and it crashed near the end at "configuring grub".  I'll try again shortly.

Having read that the daily's are available, I'm downloading now with edited rsync script (karmic->lucid).
Yes, I turn them "off" in bios.  I did try pulling the plug(s) on the buggers as SATA drives are (scares me) "hot plugable".  The problem is that when you reboot bios still wants the bugger to be there.  So I had to toggle them off anyway.

I only have 2 trays internally but enough power an data connections for 4 drives.  I could do this internally.

It is just easier with the external with its own fan.  Random stacked HDDs do not cool well inside.

---

### Post by Gina on 2009-11-16
Plenty to answer here :lol:  Thank you all for your replies :) :)

**P4 HT 3.2Ghz 1GB RAM 250GB IDE + 2x160GB SATA** is indeed the machine I've been trying to install onto.

I used to install regularly using the Alternate CD as it was quicker and easier in earlier times when my graphics wasn't properly supported OOTB.  Now I have no graphics problems and the Desktop CD allows me to take screenshots of the error messages and copy them over the LAN.  Simarly with text in a command line box.  But there's no reason for not using the Alternate CD.  I can certainly try that.

My laptop has few OSs on it - mainly just 9.04 and Win XP and one older Ubuntu (8.10 I think).  It's only a 120GB HD so not a lot of space by today's standards.  I'm going to try installing 9.10 on that with grub2 directly to MBR, since it seems that MS systems are picked up OK.  Anyway, if it won't boot I can always re-install 9.04 and it's grub to the MBR.  Or just reinstall grub with the SystemRescueCD.  I've fixed all sorts of problems with the utilities on that, in the past.

I shall also try again with my P4 with the SATA drives turned off in the BIOS setup.  Then there's various options for my AMD64.  Surely it must work on something?!

---

### Post by plun on 2009-11-16
Hi Gina 

I helped a user within my country with this challenge and he must use a Jaunty CD for restoring Grub.

Followed this guide for restoring **legacy Grub**

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

> WARNING

Do not use Ubuntu 9.10 live CD to restore the boot loader from a previous version. It will leave you with Grub in shell mode and no menu. If this happens, repeat the procedure with 9.04 or earlier -- **preferably the same version that installed Grub originally.** 

---

### Post by Gina on 2009-11-16
> **plun said:**
> Hi Gina 

I helped a user within my country with this challenge and he must use a Jaunty CD for restoring Grub.

Followed this guide for restoring **legacy Grub**

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)Thanks for that :)  I realise that it's no good trying to restore grub legacy with a grub2 based OS :) Fortunately, I won't have to :)

NOW THEN....  I seem to have cracked it as far as my P4 is concerned - with the help of suggestions here :)  I installed 9.10 using the Alternate CD.  First I tried to install grub into the partition as the included instructions said would work, but got a fatal error message.  So I back-tracked and re-ran the boot loader installation but choosing the MBR this time.  It proceeded without a grumble :)

After rebooting the new system started up perfectly.  The start menu also listed my other operating systems.  I checked out Firefox and then restarted again to see it other systems booted.  Firstly Windows XP and then other versions of Ubuntu.  All booted fine and worked!

Tomorrow I'll try installing on my other machines.

If that works I'll be thinking which machine I'll be using to test Lucid.  I have the daily ISOs all ready to go - downloaded from chromium using rsync as I mentioned in another thread.

---

### Post by ranch hand on 2009-11-16
Well that is GREAT.

As usual, kansasnoob has good ideas.

I never even think of the altCD.  I have never had trouble with the live variety and they are SO handy.

Geeze I am happy that worked, and that everything is working.  You may want to turn your grub.cfg menu entries into a custom file so that they stay the way they are.

---

### Post by kansasnoob on 2009-11-16
You know, what we call the alternate install is basically the default Debian install :D

Karmic was a brave and yet reckless move. So many things changed at one time it's almost mind boggling but someone has to be bold enough to make the jump!

Hardy will be supported for nearly another year and a half so I think it's reasonable to wait until about 4 to 6 months after the release of Lucid to expect true stability.

Then again I play with Sidux and such.

---

### Post by ronacc on 2009-11-16
glad to see I'm not the only one having problems getting the 9.10 (gnome) installer to do what I want . I also tried the lucid daily live and it failed to install grub2 to the mbr of sdd twice and to the / partition sdd1 once . I tried the chroot route ,  no help there, downloading the alternate now and will try that tomorrow . The strange thing is the release of kubuntu 9.10 installed to sdf with no problems and put its grub2 in the mbr of sdf like it was told to .whats the difference between the kubuntu and ubuntu installers ?

---

### Post by Gina on 2009-11-17
> **ranch hand said:**
> You may want to turn your grub.cfg menu entries into a custom file so that they stay the way they are.Yes, I intend doing that.  Got some reading to do!!

Installing to AMD64 (MBR) went fine.  All OSs listed and working :)

However, I have a problem with the laptop.  Put Alt CD in the drive and ran the CD check - all OK.  Sorted out a partition to install into and ran the installation (using MBR and internal /home).  Went fine, showing it had found my other OSs, and rebooted.  The boot menu appeared showing all the OSs including the new install (grub 1.97beta).  I let it count down and choose the default new OS.  Then just a blank screen - no visible activity, just the fan running flat out.  I left it a minute or two then gave up and hit the power button - it turned off.  Turning back on it booted to the menu and I tried moving the selection with the up/down keys.  NO RESPONSE!! It just sat there doing nothing.  Ran it again and tried the Return key to select the default OS - again no response.  I'll try again later then re-install 9.04 if 9.10 won't work.

---

### Post by Gina on 2009-11-18
No joy with Karmic on the laptop, keep getting the same problem.  So I've re-installed my trusty 9.04 and everything is working again.  

Think I might try Lucid - you never know... :lolflag:

---

### Post by Gina on 2009-11-18
No, Lucid won't work either :(  Oh well, I'll stick with what I've got for now.  Something might come to light later.

Meanwhile, I have installed Lucid on my AMD64 and will be using this for testing again - I always back up anything of any importance anyway.  I was thinking of using the laptop this time.  Maybe later.

---

### Post by ranch hand on 2009-11-18
I think that they are going to be awfully conservative with Lounge Lizard.  Kinky Kitten (9.10) did not kill any kittens.

I doubt there is much danger in running the Lizard just about anywhere (says the guy with it on an isolated drive).

---

### Post by Gina on 2009-11-24
I'm still having problems with Lucid and Karmic on my laptop. Prior to installing a grub2 version, I had 3 OSs on the one hard drive. Ubuntu 9.04 and 8.10 and Windows XP all booting and running happily. I then installed Karmic aka 9.10 letting it install grub2 into the MBR. On re-start all the OSs were listed in the boot menu but nothing would boot. Moving the selection bar caused a system total freeze as did allowing the time-out to boot 9.10. It showed a flashing text cursor in the top left corner for a couple of seconds then blank screen and total freeze.

I reinstalled 9.04 to a spare partition replacing the MBR with a grub legacy loader. Now all OSs are found including 9.10 and all boot and run except 9.10 which gives the same system lockup as above. Replacing the menu entry for 9.10 with chainloader didn't help - I get the Error 13 message.

I used the Alternate CD version for installing as I had found the Desktop CD refused to install the grub2 boot loader on either of my two main desktops although it would run as a Live CD.  I've now tried the Live CD (Desktop) version but it won't boot - it produces the same system lockup as attempting to boot an installed version.

I think I may have upset the partition table on the HD when using GParted to try and make a separate boot partition to see if I could get grub2 to boot (as suggested in another thread).  GParted now hangs at the point where it looks for partitions.  Otherwise, Ubuntu 9.04 runs fine - there is just one partition which won't mount, the one I was playing with.  No surprise there as that operation resulted in GParted not finding partitions.  The rest of the HD seems fine.  However, this doesn't explain why the 9.10 and Lucid Live CDs won't run - and I've tried both the DVD drive and USB stick with the same results.

---

### Post by Gina on 2009-11-24
I'm attaching the RESULTS.txt resulting from running Boot Info Script.

BTW the partition I was trying to change was sda4.

---

### Post by ranch hand on 2009-11-24
When you try to boot to 10.04 again try editing the entry by removing;
```

        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi

```
It might help.

---

### Post by Gina on 2009-11-24
> **ranch hand said:**
> When you try to boot to 10.04 again try editing the entry by removing;
```

        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi

```
It might help.Thank you :)  I'll give it a go.

---

### Post by ronacc on 2009-11-24
I'll be interested to see if that helps also. Grub2 does seem to be a bit particular about where it is installed .On my box it would not install to the IDE slave MBR but would to the IDE master mbr or any of my sata's . also I had the freezing at the boot menu sometimes on one motherboard but not on another .I had tried editing some of the things in grub.cfg but not what ranch hand suggested .

---

### Post by Gina on 2009-11-25
I've reinstalled Karmic to have grub2 in the MBR - using the Minimal CD this time and installing just the OS and Ubuntu Desktop.  Same result, not surprisingly, so I'm running Jaunty Live CD (USB stick) to edit the grub2 setup ATM.

Back soon :)

---

### Post by Gina on 2009-11-25
> **ranch hand said:**
> When you try to boot to 10.04 again try editing the entry by removing;
```

        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi

```
It might help.Firstly, I can't edit the boot entry from the list - pressing the "e" key causes it to hang.  

So I booted from the 9.04 (Jaunty) Live CD (on USB stick) and worked on the appropriate partition.  i looked at grub.cfg - yes, there they are.  Then went to the grub.d config files and found it in 10_linux and commented the lines out.  Then I realised that that would only work if grub is updated from that OS. So I edited grub.cfg directly - commenting out the lines in question. 

Rebooted from HD to see if this had achieved anything but NO it's just the same.

Any other suggestions, please? :)

---

### Post by ranch hand on 2009-11-25
I am clueless.  This has got to be a  hardware based problem.

My son has a strange AMD setup (tri-core 64 bit) and he doesn't have any trouble with the "normal" kernals.  He can't get Studio to go because the RC kernel will not install.

Your setup looks like one that Linux in general and Ubuntu in particular ought to just fall onto and work.

---

### Post by Gina on 2009-11-25
Well, it has in the past!  Absolutely no problem with 9.04 Jaunty or before.  I started with 5.04.  In the early days I had fun with wireless but that works OOTB these days.  For ease of installing I've run a cable to where I use my laptop and generally use that.

---

### Post by Gina on 2009-11-25
I've run a test to check that the grub.cfg file I edited was actually being run.  I added an extra bit to the titles of the Karmic entry (first in the list) and checked it turned up in the boot menu (it did).  So since I can't even edit the grub entry I infer that the problem might lie in the grub.cfg file or the grub software.

I have another "funny" - I can't get a partition listing with GParted, run from 9.04 Live CD, yet all file systems on these partitions are accessible from nautilus.  I'm wondering whether to try running another install of Karmic and letting it wipe the whole HD and use it all for it's installation.  I haven't got anything particularly important on the drive - everything of any value to me is backed up.  I've been keeping Windows XP on the laptop but I can't remember using it for years.  I have a backup partition image anyway.

Although I could continue using 9.04 aka Jaunty, I would really like to take advantage of the extra features of later versions.  And I could use it for testing.

I'm attaching my grub.cfg file in case it helps.  I've had a look through it but nothing stands out.

---

### Post by cariboo on 2009-11-25
I had a similar problem, with the drive I wanted to install Karmic, it seemed no matter what I tried, the drive wasn't detected. There are several support threads suggesting that if dmraid is either unchecked on the Live Cd startup menu, or removed after you have booted to the desktop, that the disk/partition will be detected. None of those solutions worked for me. 

I mounted the drive manually and then started the install. The partitoner detected that the drive was mounted, and asked me if I wanted to unmout it, it then showed up in the partitioner.

I have reported the bug, but can't seem to find it at the moment, and email notification is on another computer. I will add the bug number when I get back to the other system.

Bug report #[lpbug]486481[/lpbug]

---

### Post by ronacc on 2009-11-25
just a question gina , is the drive you are having a problem on IDE or SATA and if IDE is it master or slave ? after much testing and playing around I ended up wiping both IDE's putting lucid on the master and leaving the slave blank .What is happening to you sounds alot like what waws going on on my testing desktop , grub menu locked up on occasion and although I could edit from the menu (if it hadn't locked up ) the edits would not take effect .

---

### Post by Gina on 2009-11-25
It's an IDE and I presume it must be master, as it's the one and only hard drive.  Though I guess the DVD drive is also IDE.  I've just checked the BIOS settings and there's no mention of master or slave, just HD and CD drives (and USB drive when I plug a USB stick in).

Just had a thought.  I wonder if installing onto an external USB HD would offer any insight into the problem.  Actually, I've got a 4GB USB memory stick I could try.  That should be big enough for a test.

---

### Post by ronacc on 2009-11-25
if you only have a dvd drive and one hard drive the hd may be the slave . whether it is master or slave may or may not show up directly in the bios but should show up on the initial boot screen that is there before grub loads , you may have to enable that screen in bios , boxes that originaly had windows on them often have it toggled off .

---

### Post by Gina on 2009-11-25
I'll check that later.  ATM it's installing Karmic on 4GB USB stick - minimal system.

---

### Post by Gina on 2009-11-25
Well, it refused to install grub2 to sdb (the USB stick) but was able to install LILO instead.  I'm not sure what to make of that!!  However, it's booted into Karmic - very very slowly!!  Ten second boot???  More like ten minute!! :(:(

---

### Post by ronacc on 2009-11-25
I haven't tried to install to a usb stick , mabye later tonight . Here is the bug# 486151  that I filed but there are 350 against grub2 that you can choose from , many for won't install to various places , it looks like they have a problem .

---

### Post by kansasnoob on 2009-11-25
@Gina,

Why not just install legacy grub?

I just did one today like this:

(1) Using the Live CD installer at the last step click on Advanced and choose not to install grub at all!

(2) When installation is done don't choose to restart, rather choose to keep using the Live CD.

(3) Since you just installed you should know the drive/partition # of your Karmic (or Lucid) so keep that in mind. If you have no idea the Boot Info Script should be helpful:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

(4) From the Live Desktop run:

```
sudo mount /dev/sdXY /mnt
```

(of course XY must represent your drive and partition #'s!)

Then:

```
sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

You should notice that the command prompt changes from ubuntu@ubuntu$ to # which means you're now root in that OS. I like to be sure I am where I want to be with "cat /etc/issue" and "df -H".

Then revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And when you're done:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

---

### Post by Gina on 2009-11-26
> **kansasnoob said:**
> @Gina,

Why not just install legacy grub?

I just did one today like this:

(1) Using the Live CD installer at the last step click on Advanced and choose not to install grub at all!

(2) When installation is done don't choose to restart, rather choose to keep using the Live CD.

(3) Since you just installed you should know the drive/partition # of your Karmic (or Lucid) so keep that in mind. If you have no idea the Boot Info Script should be helpful:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

(4) From the Live Desktop run:

```
sudo mount /dev/sdXY /mnt
```

(of course XY must represent your drive and partition #'s!)

Then:

```
sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

You should notice that the command prompt changes from ubuntu@ubuntu$ to # which means you're now root in that OS. I like to be sure I am where I want to be with "cat /etc/issue" and "df -H".

Then revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And when you're done:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```Well, I may well do that but I think I have hard drive problems which want fixing first.  

I installed **testdisk** into my Live CD USB stick system (Jaunty) and did a deep search.  That found all partitions, old and current.  Some I wanted were marked as deleted.  I carefully went through the list changing the Deleted flag to either P or L as appropriate and checked they were all contiguous.  Then I wrote all that back to the Partition Table.

Next it said the boot sector was corrupted (which I had suspected) but there was a good backup, and choices of restoring that or rebuilding the boot sector - I chose to restore.  So there ***have*** been problems with the HD.  Next thing, I think, is a thorough check of the HD itself.  I'll have to check again because I've been asleep since :lol: but I think I found GParted still wouldn't work on that drive though it found the USB drive.

So I think I've got to make sure the hardware and disk structure are OK before I abandon grub2.  Because, although there are known bugs in grub2, I feel it's the way to go.  If after all the checks and repairs, there are still currently insurmountable problems, I shall revert to grub legacy until the worst bugs are fixed in grub2.  Thank you for the tutorial on the best way to do that :)

---

### Post by Gina on 2009-11-26
Confirmed - GParted still won't read the partitions on sda.  So the hard drive has a problem that needs sorting out before anything else.

---

### Post by Gina on 2009-11-26
I've just run fsck which found lots of errors, particularly on the partition I was playing with. I've marked that deleted in the Partition Table. Could only check Linux partitions with that so I put the MBR back to grub legacy and now running XP and checking the NTFS partitions for bad sectors etc.

Once the repairs are done I'll try GParted again. But I've already pretty much decided I don't really want Windows XP on the laptop any more so I'm thinking of installing Karmic and letting it grab the whole HD and format it how it likes. See if that works and take it from there. The drive is really in a bit of a mess and I'm hoping a whole drive install will wipe the PT and start from scratch.

---

### Post by Gina on 2009-11-26
The repairs worked and GParted worked again.  Anyway, decided to wipe everything and start afresh so installed Karmic and chose the **Use whole HD** partitioner option and let it install grub2 to MBR.  Now have 9.10 system and swap partitions only.  But the system freezes on startup still :(  So it looks like a downgrade to grub legacy.

---

### Post by drs305 on 2009-11-26
> **Gina said:**
> Now have 9.10 system and swap partitions only.  But the system freezes on startup still :(  So it looks like a downgrade to grub legacy.

This is on a normal hard drive?

At what point does the system "freeze"? If you get the Grub 2 menu, can select an entry, and the process continues it may be a problem with the video, kernel or something not related to Grub. Remember Grub only transfers control to the kernel.

---

### Post by Gina on 2009-11-26
Yes, normal hard drive - IDE 2.5" laptop drive.

Since there's only one OS on the machine, the menu is hidden (I think) - anyway, no menu is shown and after a couple of seconds of text cursor the screen is blank and nothing responds except the power button.

---

### Post by ronacc on 2009-11-26
if gina is having what I was getting he can't select anything. cursor won't move , return won't boot the autoselected entry ,if set for a time it don't count down . The only way out is a hard reboot .

---

### Post by Gina on 2009-11-26
Tried again hitting Esc at the appropriate time and got the grub v1.97beta menu.  FULL STOP!  Yes!!  Only way out is a hard reboot.  The same problem still.

---

### Post by ronacc on 2009-11-26
just for grins boot a livecd and mount your / and have a look at your grub.cfg file and check to see if set root (2 places , right near the start after insmod ext2 and again in the menu entries) is pointed at the right place and also that the uuid is correct for your boot drive , early on grub2 uas getting the uuid wrong for some people .and I had noticed on mine when it was screwing up that set root was pointed at a different at the start then it was in the menu entry .

---

### Post by Gina on 2009-11-27
> **ronacc said:**
> just for grins boot a livecd and mount your / and have a look at your grub.cfg file and check to see if set root (2 places , right near the start after insmod ext2 and again in the menu entries) is pointed at the right place and also that the uuid is correct for your boot drive , early on grub2 uas getting the uuid wrong for some people .and I had noticed on mine when it was screwing up that set root was pointed at a different at the start then it was in the menu entry .Right... Booted from USB Live CD of Jaunty (Live CD of Karmic or Lucid won't work)and listed grub.cfg.  
Also ran **sudo tune2fs -l /dev/sda1** in a terminal to get the system partition info for UUID.  The UUIDs are the same.  

Next checked the root locations ***and they are wrong***! grub.cfg says (hd0,1) but partition is sda1 = (hd0,0)!

I'll go and edit the grub.cfg file and see what happens :)  

I'm attaching the grub.cfg and sda1-info files.

---

### Post by Gina on 2009-11-27
No change!  Still won't work.  Exactly the same thing happens.

Thinking about it, I don't think it gets as far as using the menu entries other than to display them.  The menu UI doesn't work.

This is strange!  Why should it work on one machine and not another?

I presume the grub application is hard coded rather than using a script which would be easy to debug.  I don't think I'm up to examining the source code any more.  I'll have a closer look at the grub.cfg file though.

LATER...  Had a good look through grub.cfg and can't see anything obviously wrong but I don't quite follow some of it.

---

### Post by ranch hand on 2009-11-27
Actually (hd0,1) would be correct for sda1 in grub2.  The drive is numbered the same as in grub-legacy but the partition is numbered starting with 1 instead of 0.

---

### Post by kansasnoob on 2009-11-27
> Next checked the root locations and they are wrong! grub.cfg says (hd0,1) but partition is sda1 = (hd0,0)!

Remember numbering changed in grub2:

In legacy-grub, the following were the mappings:

/dev/sda1 - (hd0,0)
/dev/sda5 - (hd0,4)
/dev/sdb2 - (hd1,1)

However in grub2, the above translates to:

/dev/sda1 - (hd0,1)
/dev/sda5 - (hd0,5)
/dev/sdb2 - (hd1,2)

Drives still begin with 0 but partitions begin with 1.

---

### Post by Gina on 2009-11-27
Well, that's confusing!!!  How ridiculous!!  :(:(:(  Wonder whose idea that was.

In that case there seems to be nothing wrong with grub.cfg!  But there's something wrong somewhere.

I can't file a bug report because I don't know what the bug is.

---

### Post by ronacc on 2009-11-27
want some more confusion ? ubuntu doesn't list the drives the same way the bios does , bios lists IDE first then  SATA . on my 6 drive box the IDE master is hd0 and slave is hd1 then the sata's however since ubuntu sees the sata drives 1st it calls the ide drives hd5 & 6 . That is bull**** .

---

### Post by Gina on 2009-11-27
> **ronacc said:**
> want some more confusion ? ubuntu doesn't list the drives the same way the bios does , bios lists IDE first then  SATA . on my 6 drive box the IDE master is hd0 and slave is hd1 then the sata's however since ubuntu sees the sata drives 1st it calls the ide drives hd5 & 6 . That is bull**** .Yes, I came across that with my P4 when I added an IDE drive to the two SATAs that were already there.  Why add an IDE?  Because the MB in that machine only supported two SATA drives and I had an IDE drive spare.

Confused??  You will be :lolflag:

---

### Post by Gina on 2009-11-27
Well it seems that grub2 doesn't like my laptop (or vice versa) as grub2 is ATM so I'll revert to grub-legacy as per ***kansasnoob's*** tutorial.  Then I'll try it again in a month or two with Lucid.

EDIT...  @ ***kansasnoob*** does your method require running a Karmic/Lucid Live CD to work on the grub stuff?  Or can I install with the Alt CD without installing grub2 then use the Jaunty Live CD to install grub-legacy components.  The reason I ask is that the grub2 based Live CD won't run on my laptop.  (Or at least it didn't before.)

Another Edit...  I'll leave it until tomorrow now - when my mind is fresher.  I might be able to work it out for myself then :)

---

### Post by kansasnoob on 2009-11-27
> **Gina said:**
> Well it seems that grub2 doesn't like my laptop (or vice versa) as grub2 is ATM so I'll revert to grub-legacy as per ***kansasnoob's*** tutorial.  Then I'll try it again in a month or two with Lucid.

EDIT...  @ ***kansasnoob*** does your method require running a Karmic/Lucid Live CD to work on the grub stuff?  Or can I install with the Alt CD without installing grub2 then use the Jaunty Live CD to install grub-legacy components.  The reason I ask is that the grub2 based Live CD won't run on my laptop.  (Or at least it didn't before.)

Another Edit...  I'll leave it until tomorrow now - when my mind is fresher.  I might be able to work it out for myself then :)

I've been busy out in the yard most of the day and I'm cooked, mentally and physically.

One thing I can tell you is that I just recently tried the Alternate CD to see if it allowed for installing legacy grub rather than grub2. No it doesn't, so there's no benefit to using the alt rather than the Live CD.

In fact I think you'd still have to use the Live CD to do what I spelled out earlier. I certainly don't know how you could do it using the alternate.

And, since you keep playing with different options, before we even start I'd want to see the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

But I'm using this last spurt of half-way decent weather to make sure my fainter goats are safe this winter. Wet, cold fainter's die!

The goats and the dogs run things around here and if I mess up I'm gone :D Seriously I love my animals and their living conditions suffered while I was laid up with a badly broken leg.

As far as what Live CD you need, I have run into some difficulties using Karmic Live CD's to revert to legacy grub. Anything prior to Karmic should work fine I think.

Please give my brain time to adjust from tending to the animals back to this techie stuff.

---

### Post by Gina on 2009-11-27
No problem :)  We have goats too - lovely animals :)  And I hope your leg's better now :):)

I'll post the RESULTS.txt from the Boot Info Script tomorrow - just after midnight here.

Goodnight and thanks for your help :):)

---

### Post by ronacc on 2009-11-27
@ Gina , not hijacking your thread just trying to add info , we will get this sorted one way or another . I tried to install jaunty to the drive that has been giving me problems , it installed and it did put grub-legacy in the mbr but trying to boot from that drive gives "GRUB loading stage1.5ReadError " . on my box boot info script shows that drive having grub-legacy and that it is pointed at the correct place . at this point I don't know what to think . this weekend I am going to disconnect all other drives in the box , make that one hd0 and see if I can install to it that way just to make sure something isn't flaky that disk tests don't show .

---

### Post by Gina on 2009-11-28
> **ronacc said:**
> @ Gina , not hijacking your thread just trying to add info , we will get this sorted one way or another . I tried to install jaunty to the drive that has been giving me problems , it installed and it did put grub-legacy in the mbr but trying to boot from that drive gives "GRUB loading stage1.5ReadError " . on my box boot info script shows that drive having grub-legacy and that it is pointed at the correct place . at this point I don't know what to think . this weekend I am going to disconnect all other drives in the box , make that one hd0 and see if I can install to it that way just to make sure something isn't flaky that disk tests don't show .Have you run a disk surface test?  I wouldn't know what to suggest, I haven't needed to run one for many years now - drives have proved very reliable.  My only problems have been software or user related.

Suspecting a surface problem on part of your drive I would suggest installing to a different partition - a different part of the drive surface.  Might be something else, of course.  

That's all I can think of for now.

---

### Post by ronacc on 2009-11-28
thanks for the sugestion , I'll give it a try before I strip down to one drive . Right now I can think of 3 possibilities .
1. some kind of disconnect between grub,ubuntu, and the bios .
2. a physical problem with the drive.
3. the fact that both master and slave are the same make, model and size of drive . I remember way back when having 2 WD drives of a certain model caused problems, but these are maxtors .

---

### Post by Gina on 2009-11-28
The SATA drives in my P4 are same make, model and size but I haven't seen any problem with that.

---

### Post by ronacc on 2009-11-28
well I now know it is not a fault with the drive . I tried your sugestion no help then I disconnected the IDE master and rejumpered the former salve as master and installed and booted jaunty with no problem . just to be through I'll install lucid with grub2 .

---

### Post by Gina on 2009-11-28
@ronacc An advance then :)  Good luck with Lucid :)

Re. my laptop...  I installed Lucid using the entire disk.  It took it all except for 1.33GB for swap.  Expected result.  As I said above - won't run.  Then I decided to see what installing Karmic would do, letting it resize sda1 and use the gained space.  I told it to take 20GB.  Also, stopped the grub2 install ready for reverting to grub-legacy.  It left 18.4GB and grabbed the rest making yet another 1.33GB swap partition.  So - two swap partitions - that isn't very clever.  Furthermore, runnung GParted from Jaunty Live CD (on USB) showed a corrupted sda1.  Now that is BAD!!

I conclude there are a number of problems in Karmic still to be fixed.  Not to worry, I have a free HD to play with without worrying about messing it up.  Just wipe the lot and start again :lol:

With that in mind I'm starting again, this time with Jaunty grabbing the whole HD and wiping the partition table.  This gives me grub-legacy on the MBR ready for reverting Karmic later.  Next I'll repartition as I would like and install Karmic using manual partitioning and without grub2. After that I'll install grub-legacy into Karmic and add an entry to my Jaunty menu list for Karmic.

I'll post the results when I've done all that :)

---

### Post by ronacc on 2009-11-28
ok I attempted to install todays (nov 28) live cd , tried twice fails to boot both times . tried the first live cd from nov 16 and that worked although it had failed when the drive was in the slave position , I have 2 other installs of lucid one gnome one kubuntu on sata drives and both worked first try , I think the problem may be in the way karmic and now lucid with grub2 handle IDE drives .

---

### Post by ronacc on 2009-11-28
one more interesting piece of the puzzle , I designated the drive back to slave and reinstalled the original master . now the slave wont boot , "GRUB loadingReadError"  again before it even gets to the menu ??? damn I wish I knew of a sector editor for linux like they used to have for the Amiga so I could look at the raw contents of the mbr .

---

### Post by Gina on 2009-11-29
> **ronacc said:**
> one more interesting piece of the puzzle , I designated the drive back to slave and reinstalled the original master . now the slave wont boot , "GRUB loadingReadError"  again before it even gets to the menu ??? damn I wish I knew of a sector editor for linux like they used to have for the Amiga so I could look at the raw contents of the mbr .That's a strange one.

Been googling - see if any of **[_these_]("http://en.wikipedia.org/wiki/Disk_editor")** are any good.

Another thought :- Did you sawp drives or connect the other in addition.  If the latter it could be PSU trouble - now unable to supply enough current for the extra drive.

---

### Post by Gina on 2009-11-29
Back to laptop...  Cleared PT and installed Jaunty to sda1 and grub-legacy to MBR.  Used manual partitioning and assigned partitions for / /home and swap.  Tested and set up Jaunty - using it now.

Next, installed Karmic using Alt CD using manual partitioning and set it's own / and /home.  No grub2 install - so MBR is grub-legacy.  Booted HD and Jaunty ran as expected. Ran GParted to examine partitions.  Correct sizes and places but dashes shown for the Used amount for the Karmic partitions rather than the MBytes :(  Something wrong there.  At this point I downloaded and ran the Boot Info Script and obtained RESULTS.TXT which I'll attach.

Continuing after lunch...

---

### Post by Gina on 2009-11-29
Resuming tests...

Used GParted to label the Karmic partitions and now the bytes used is being displayed.  Very odd.  I'll attach a screenshot.

---

### Post by Gina on 2009-11-29
Followed ***kansasnoob***'s instructions but seem to be having problems - some things seemed to go alright but get errors in places :(  I'll attach my terminal record. ATM I can't seem to get the Grub Info Script to work from Live CD.  I'll try again later.  Going to see what happens when I boot the HD.

---

### Post by Gina on 2009-11-29
Laptop tried to boot into Karmic - all trace of Jaunty booting had been removed.  But it got as far as the boot menu - where I could select the two Karmic entries and memtest (memtest worked) but selecting Karmic or letting it time out left me with a blank screen.  So the installation of grub-legacy into Karmic was not complete it seems.  I could edit the boot entries this time but using "b" to boot just led to a blank screen.  

After a break, I'm going back to look at what various folders contain and the menu list.  Also to see if I can get Grub Info Script to work.

It's looking more promising but not quite there yet.

---

### Post by ronacc on 2009-11-29
thanks for the link , I had checked source-forge before but I missed a couple of those , I'm playing with them to see if they'll do what I need . the errors you mention in the term record you posted look like its looking for /home on the live cd  but you are chrooted to your hd . about boot info script ,did  you remember to change permissions on it to make it executable ? as downloaded it isn't executable , that bit me a couple of times .

---

### Post by Gina on 2009-11-29
> **ronacc said:**
> the errors you mention in the term record you posted look like its looking for /home on the live cd  but you are chrooted to your hd .Ah yes, I think you may be right.
> about boot info script ,did  you remember to change permissions on it to make it executable ? as downloaded it isn't executable , that bit me a couple of times .DOH!! Think you may be right there too.

I copied the boot stanzas for Jaunty from the Jaunty grub menu list into the Karmic one and saved back.  Rebooting gave me access to Jaunty.  Ran the Grub Info Script from there.  I'll attach the RESULTS.txt.  I've looked at the various folders and files and can't as yet see why Karmic won't boot.

---

### Post by Gina on 2009-11-29
*UPDATE*

I've very carefully examined the contents of folders and files comparing Jaunty and Karmic and checking things such as UUID and can find nothing wrong.  Just one difference - Jaunty installed with ext3 (it's default, though lately, on other machines, I've been using ext4), whereas Karmic used ext4.  Both systems were installed to brand new partitions from the free space.  (Obtained originally by clearing the partition table.)

Then did minor edits to menu.list in Karmic such as commenting out hiddenmenu and setting the timeout to 10 from 3.  So I could see the boot menu easily.  

Starting from the normal menu item gave a quick "booting ext4" or something like that, in text mode, then just a blank screen.  

Then tried booting the **recovery mode** menu item and got the command line log in. At the recovery menu I chose "boot normally" and it did, giving me the command line.  **startx** and I was in! :)  **Normal graphical start up.** 

The menu entries are the same except for the boot options.

From the normal GUI desktop (obtained via recovery mode) I'm currently doing the updates using Synaptic.  After that I'll try again with the standard GUI start up.

(Typing this on another machine)

---

### Post by Gina on 2009-11-29
The updates didn't make any difference.  I didn't let it change menu.list and added the new entries myself. (New kernel)

One observation - Ctrl-Alt-Del reboots from the blank screen.

---

### Post by ronacc on 2009-11-29
what is your video driver ?

---

### Post by ronacc on 2009-11-29
thinking about your problem I dont think it has anything to do with grub . you are getting a menu , the difference between the "normal " entry and recovery mode is  "single" which as far as I can tell sends you to a console login .then when you run startx it takes you to the desktop by a different route than a normal boot would , I am pretty sure startx does not run upstart so that may be where the problem is , not grub , I am not an expert on what runs when during bootup so take the above with a grain of salt but it might be worth exploring .

---

### Post by Gina on 2009-11-30
> **ronacc said:**
> thinking about your problem I dont think it has anything to do with grub . you are getting a menu , the difference between the "normal " entry and recovery mode is  "single" which as far as I can tell sends you to a console login .then when you run startx it takes you to the desktop by a different route than a normal boot would , I am pretty sure startx does not run upstart so that may be where the problem is , not grub , I am not an expert on what runs when during bootup so take the above with a grain of salt but it might be worth exploring .Yes, that was it! :):)  I took "splash" off the menu entry and it now starts up fine :)

Problem solved. :)

Now to do the same with Lucid - reverting that to grub-legacy and removing "splash".

---

### Post by kansasnoob on 2009-11-30
A couple of things, from the installation script (thanks for saving that BTW):

> Copy of actions in grub shell
----------------------------------------------------------------
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,6)

grub> setup (hd0)

Error 12: Invalid device requested

grub> 

You skipped a step, should be like:

> grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,6)

grub> **[COLOR="Red"]root (hd0,6)[/COLOR]** or root (hd0,0)

grub> setup (hd0)

For simplicity sake I'd personally recommend going with grub on 9.04 so just boot the live CD, open terminal and hit the grub shell:

```
sudo grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

You should see this:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

If so just:

```
quit
```

Then just reboot and you should boot 9.04, I'd then make the following changes to 9.04's menu.lst (all edits in red just for visibility):

(of course: "gksudo gedit /boot/grub/menu.lst")

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**[COLOR="Red"]#[/COLOR]**timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]**hiddenmenu

(..........skip down a bit..........)

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[B][COLOR="Red"]title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=44b7153f-0c0f-49ec-888a-7be93b3a332c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=44b7153f-0c0f-49ec-888a-7be93b3a332c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic[/COLOR][/B]


That will at least get 9.04 booting from grub, of course we can also hope for 9.10, but then we can do a lot of work from 9.04 instead of having to boot the live CD which is time consuming.

FYI those first two edits:

(1) **#timeout 3** creates an infinite timeout, nothing will boot until you've made a selection and hit enter.

(2) **#hiddenmenu** just un-hides the menu so you don't have to fiddle around hitting esc to see the menu at boot.

Also when you edited 9.10's menu.lst you added the 9.04 boot options in the wrong place:

> ## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=44b7153f-0c0f-49ec-888a-7be93b3a332c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=44b7153f-0c0f-49ec-888a-7be93b3a332c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

They should have been below the ### END DEBIAN AUTOMAGIC KERNELS LIST like this:

> ## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=44b7153f-0c0f-49ec-888a-7be93b3a332c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=44b7153f-0c0f-49ec-888a-7be93b3a332c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		44b7153f-0c0f-49ec-888a-7be93b3a332c
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		1d29160f-39c9-4b93-b25d-a2bb314a2da7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1d29160f-39c9-4b93-b25d-a2bb314a2da7 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic



Anyway see if you can get that far and let me know what happens, then we can go from there ............. after I've had more coffee :)

---

### Post by kansasnoob on 2009-11-30
> **Gina said:**
> Yes, that was it! :):)  I took "splash" off the menu entry and it now starts up fine :)

Problem solved. :)

Now to do the same with Lucid - reverting that to grub-legacy and removing "splash".

Oh, I was slow.

---

### Post by Gina on 2009-11-30
Thanks :)  You're right, of course, I should have put the 9.04 stanzas outside of the automagic kernels list.

And yes, plenty of coffee is a must!! :lolflag:

---

### Post by Gina on 2009-11-30
I'm considering what to do about what happens when a kernel upgrade occurs in one or other of the systems installed.  In the past, with everything using grub-legacy I used **configfile** in the first boot menu.list to point to the menu.list of the others.  That way, when the other OSs have a kernel number change this is applied to their own menu and is recognised on boot-up.  Now I'm wondering if this idea will work with Karmic and Lucid when they've been designed to use grub2 but now use grub-legacy.  I guess I can try it and time will tell if it works or not :lol:

---

### Post by kansasnoob on 2009-11-30
> **Gina said:**
> I'm considering what to do about what happens when a kernel upgrade occurs in one or other of the systems installed.  In the past, with everything using grub-legacy I used **configfile** in the first boot menu.list to point to the menu.list of the others.  That way, when the other OSs have a kernel number change this is applied to their own menu and is recognised on boot-up.  Now I'm wondering if this idea will work with Karmic and Lucid when they've been designed to use grub2 but now use grub-legacy.  I guess I can try it and time will tell if it works or not :lol:

Let's not get the cart ahead of the horse. Do both Jaunty and Karmic boot now?

I may still be slow posting for a couple of days.

---

### Post by Gina on 2009-11-30
> **kansasnoob said:**
> Do both Jaunty and Karmic boot now?Yes, been using both :)> I may still be slow posting for a couple of days.OK - no problem :)  I have plenty to do anyway.

---

### Post by kansasnoob on 2009-11-30
> **Gina said:**
> Yes, been using both :)OK - no problem :)  I have plenty to do anyway.

So, correct me if I'm wrong, you could never get Karmic to boot with grub2 - is that correct?

I also need someone to shake some cob-webs out of my noggin because I've never replaced "ro quiet splash"
with "ro single" in an actual boot stanza - I'd think doing so would kill the quiet splash, but I've never tried it.

I'm just tired and when I take a look at this again I'll need to know the current state. Just be patient.

As far as updating after a kernel update on an OS other than that "housing" legacy grub it does require a moment of editing, but my intention is to get you up and running with grub2!

Although even that will require a manual "update-grub" if updating the kernel on an OS that the controlling grub2 is not installed on.

Just out of curiosity where is grub installed right now? Jaunty like I suggested?

---

### Post by ronacc on 2009-11-30
@ kansasnoob if you don't want splash to run just remove splash from the boot line DO NOT add single or you will end up at a console . single does not load xorg or gdm . if you are having problems  remove quiet and you will see each cmd as it is run so you can see where it stops and know where it went wrong .

edit :  single dumps you to run level 1 see here for an explanation of run levels [http://en.wikipedia.org/wiki/Runlevel#Typical_Linux_runlevels](http://en.wikipedia.org/wiki/Runlevel#Typical_Linux_runlevels)

---

### Post by Gina on 2009-11-30
I'll do a proper reply later, but basically I couldn't get Karmic to boot with grub2.  Though I didn't try removing "splash" from the appropriate config file.  I couldn't try the recovery mode boot because I couldn't change the selection.

Currently, Karmic is controlling the boot - providing the boot menu, but I may reinstall grub by re-installing Jaunty.  It might detect Karmic and Lucid with those using grub-legacy.  

Just installed Lucid (from daily build) without installing grub2.  Tomorrow I'd planned to revert it's internal grub2 to grub-legacy.

---

### Post by ranch hand on 2009-12-01
I have had some problems that required editing the /boot/grub/menu.lst when using 9.04 mixed with 9.10 using grub2 but usually noo problem at all.  I always liked to have a grub-legacy OS on my test platform during 9.10 testing.

---

### Post by Gina on 2009-12-01
> **kansasnoob said:**
> So, correct me if I'm wrong, you could never get Karmic to boot with grub2 - is that correct?Not on my laptop but I could on the AMD64 and P4 desktops> I also need someone to shake some cob-webs out of my noggin because I've never replaced "ro quiet splash" with "ro single" in an actual boot stanza - I'd think doing so would kill the quiet splash, but I've never tried it.**ro single** creates a "recovery mode" bootup which bypasses the splash screen.  **Quiet** suppresses the text startup output.  **Splash** enables the splash screen.  Having reverted to legacy grub, the startup gets further and then crashes at the splash screen.  Removing **splash** from the boot line bypasses the splash screen and hence the problem.> I'm just tired and when I take a look at this again I'll need to know the current state. Just be patient.No problem - patience is my middle name - well almost :lolflag:> As far as updating after a kernel update on an OS other than that "housing" legacy grub it does require a moment of editing, but my intention is to get you up and running with grub2!I think I'll rope my AMD64 into Karmic and the testing of Lucid in addition to my laptop so that I can use grub2.  As for the laptop and grub2, we'll have to see.  Admittedly, it would be very nice to find out why grub2 won't work with the laptop.> Although even that will require a manual "update-grub" if updating the kernel on an OS that the controlling grub2 is not installed on.Yes, agreed.> Just out of curiosity where is grub installed right now? Jaunty like I suggested?I have now installed Lucid, reverted that to legacy grub and added the Jaunty stanzas to Lucid's menu.list.  So I can boot Lucid and Jaunty ATM.  Next I intend installing grub-legacy from Jaunty to make the MBR point to the Jaunty boot menu and if the "update grub" doesn't find the Karmic and Lucid systems, I shall add them manually.

---

### Post by Gina on 2009-12-01
OK - have set the MBR to load and display the Jaunty boot menu.  Edited Jaunty's menu.lst to un-hide the menu and remove timeout plus added boot stanzas for Karmic and Lucid.  I used the grub-legacy **configfile** command to link to the boot menus for Karmic and Lucid.

I can now boot into any of the three systems and they all run fine :)  I'm in Lucid ATM on the laptop.

---

### Post by ronacc on 2009-12-01
add your info to one of the many bugs against grub2 , as of last count there were >400 between grub2 and grub-pc .

---

### Post by kansasnoob on 2009-12-01
@ronacc,

Thanks for the info regarding "quiet" and "single". Regarding the "showing text during boot" I always just used the option provided in SUM, because I'm lazy :)

@Gina,

I'm glad you're making some headway even though it's basically a temporary work-around. I'm kind of worthless at the moment, I guess I kind of overdid things a bit, and I'm back on the Percocet which makes me downright stupid!

I try not be advise others when I'm rummy like this so don't think I'm shunning your dilemma. I'm just not bright enough to respond with any level of reliability :p

---

### Post by Gina on 2009-12-01
@ ronacc - Yes, I'll see what I can do.

@ kansasnoob - Sorry you're not well - hope you feel better soon :):)

Since I can install grub2 systems on my AMD64,  I think I might change my mind again and use that for Lucid testing in addition to my laptop.  I can always make sure everything I want is backed up.  I backup anything important as I go along.

---

