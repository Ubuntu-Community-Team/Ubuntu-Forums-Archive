---
title: "Installation Freezes on Splash 10.04"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by Sylvester the Cat on 2010-08-25
I'm trying to install 10.04 Ubuntu using a USB drive. I restart the machine and I get the Ubuntu start up screen. I select to install Ubuntu on my hard drive. It does its loading process and brings up the splash screen. The red lights blink for about 10 seconds then stop. Everything freezes: the keyboard, mouse, screen, lights, everything. I can still perform a reboot, but this situation happens everytime I try to load. 

Here are some system specs for my computer (edit: these are the correct settings. The settings I have in my sig are not correct. I will change them soon. Sorry about the discrepancy)

Intel Core 2 Quad Q6600 2.40Ghz
Nvidea GeForce 8600 GTS graphics card
Trying to create a Windows 7 dual boot
8GB Memory

I tried a few things with sending noapic and nolapic as parameters to boot and that didn't work as well. 

Any ideas? Thanks for any help you may have. :D

---

### Post by lechien73 on 2010-08-25
Welcome to Ubuntu and the forums :)

Have you tried booting with the 'nomodeset xforcevesa' switches? You mentioned trying 'noapic nolapic'.

Also, if you select the option to try Ubuntu without installing, does that boot okay, or does it freeze in the same place?

---

### Post by Sylvester the Cat on 2010-08-25
Now the splash screen continues to blink and blink and blink. The same thing happens when I try ubuntu without installing. :(

---

### Post by davidmohammed on 2010-08-25
have you tried removing quiet splash from grub and replacing with

... nomodeset acpi=off xforcevesa --

---

### Post by GenBattle on 2010-08-25
I would reccomend the same as everyone else above, particularly "xforcevesa", and if that doesn't work, try removing "splash" and "quiet" from your kernel line in the GRUB entry for ubuntu.

---

### Post by Sylvester the Cat on 2010-08-25
Hate to sound like a noob, but I'm not quite sure where to make these changes exactly. Am I typing this in on the same command line as I was when I typed in live nomodeset xforcevesa?

btw just to make sure I was doing that right, what I did was got into the bootmenu screen. Hit F6 and at the prompt boot: typed

live nomodeset xforcevesa

Hopefully that was the right place. As for the other recommendations I think I need a little more detail. ;)

update:
Found a text file where I could remove "splash" and now have a spot where it freezes. It basically freezes on this line

init: ureadahead-other main process (1547) Terminated with status 4
init: ureadahead-other main process (1548) Terminated with status 4

---

### Post by Sylvester the Cat on 2010-08-25
I think I found where to place the commands I was given. I still get the same error however now the numbers are (1420 & 21).

---

### Post by GenBattle on 2010-08-25
There's a known issue with ureadahead. My Ubuntu installation did this to me about 2 weeks ago, and the only solution i could find was to reinstall.

Might pay to look into it a bit more, but the last time i checked the issue there was no known fix.
EDIT: just found this thread [http://ubuntuforums.org/showthread.php?t=1476730](http://ubuntuforums.org/showthread.php?t=1476730)

They appeared to fix the issue using "i915.modeset=1" in the kernel boot line. But yea the issue with booting and black screens has many causes, so this solution may not work for you.

---

### Post by Maverick_Meerkat on 2010-08-25
You can try using the esc key to boot into safe graphics mode. If that works it would indicate a graphics mode problem during regular boot.

---

### Post by Sylvester the Cat on 2010-08-25
> **GenBattle said:**
> 

They appeared to fix the issue using "i915.modeset=1" in the kernel boot line. But yea the issue with booting and black screens has many causes, so this solution may not work for you.

I tried to add that command to the boot line and that didn't work either. 

So far what I have in the text.cfg file under live-install is

```

  kernel /casper/vmlinuz
  append cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz i915.modeset=1 nomodeset acpi=off xforcevesa--

```

Still same issue. I will try the escape key and see if that works.

edit: Hitting the esc seems to switch me back and forth between the splash screen and the text output. No change past that. Still freezes in the same point.

---

### Post by GenBattle on 2010-08-25
Take the -- off the end of xforcevesa, or separate it with a space. The -- usually has a space between it and the other params (not that i know what its for), lumping them together would cause neither to be properly recognized.

---

### Post by Sylvester the Cat on 2010-08-26
no dice. It still freezes in the same spot. :(

---

### Post by davidmohammed on 2010-08-26
... quite a few people have had success with installs using the alternate CD rather than the desktop CD - probably because its a text based installer rather than a graphical based installer.

Also I have noticed some people say that the 64bit desktop CD works better than the 32bit desktop CD and visa-versa (32 bit instead of 64bit).

---

### Post by Sylvester the Cat on 2010-08-26
Hmm.. I am using a USB pen drive to install with the 32 bit version. I wonder if I should try downloading the 64 bit version and give that whirl.

---

### Post by Sylvester the Cat on 2010-08-26
No luck with the 64 bit version. Again, frozen in the exact same place. downloading the alternate version, however I have a feeling it will be the same. I'm just thinking I'm probably using a machine that's just not configured right for Ubuntu. I've been trying to install it ever since 8.0 with the exact same issue. I've even switched machines since 8.0 and I still cannot install it. Maybe it hates me. :)

---

### Post by GenBattle on 2010-08-26
Some other kernel boot options to try: "acpi=off" and "noapic" (try one at a time). Turning ACPI off may break other stuff though, so its not a permanent fix.

---

### Post by davidmohammed on 2010-08-26
Can I just check that you are adding the boot options in the correct place during the install?

When you first boot, you see those little icons at the bottom of the screen.  Hit any key at that point.  You should see a few options been displayed such as try without installing and install etc.

I think you then press either F6 or tab (cant remember which) - this should display the boot string which ends with ".... quiet splash --"

edit that boot string with the following

"... nomodeset --"  i.e. remove quiet splash, add nomodeset.
Then press the number corresponding to "try without installing".

do you get any further?

---

### Post by Sylvester the Cat on 2010-08-26
I messed a few things up on my machine in trying the alternative cd. Right now I have failed redundancy volumes and missing dynamic disks. I'm sure this was a result of the partitioning section. Because of that once I get this fixed I don't think I will be using the alternative install method unless I find very detailed directions on how to use it. 

Thank god for my mirrored setup or else I have a feeling I wouldn't be here right now. Backing up the whole drive right now and I really have no idea how to fix this. :( Nothing appears to make the disks come back and I get a "The Plex is missing" everytime I try and reset the disks. At this point the only thing I think I can do is either disconnect a disk and hopefully get the computer right, then re-connect the disk, deleting all partitions on, and then resetting it as a mirror. I hope that's a good plan. :) 

When I get this resolved I will return to Ubuntu. 

Just to clarify, I have been creating a pendrive and installing ubuntu from that. When the pendrive boots I get a menu and I tried the "Try Ubuntu" option that froze. I then tried Install Ubuntu which also froze. I then went to the help section and hit F6 and got a boot prompt and tried a few things there. I then found a file called text.cfg in my pendrive under Syslinux and found the boot string there which is what I pasted in an earlier post.

---

### Post by davidmohammed on 2010-08-27
the penny drops...

I strongly suspect the main issue with your ubuntu install is your RAID setup.  Its probably nothing to do with graphics (although nomodeset as a boot option will not adversely harm the installation).

I do know that some RAID hardware & also software RAIDs do not work very well with linux.

If you have the opportunity, I would remove the RAID aspect first (either the hardware or the software RAID), and install ubuntu onto a single disk directly connected into the motherboard (IDE/SATA connection).  Once you've confirmed that Ubuntu installs correctly, then someone better qualified than me can help you with setting up ubuntu with your hardware/software RAID.

---

### Post by Sylvester the Cat on 2010-08-27
I was able to get everything back on track. I don't think I'm running RAID since I didn't install anything RAID related unless setting up a mirrored drive from Disk Management IS a RAID setup and I'm just clueless to that aspect of it. I can try removing the mirror and setting up that partition as basic and then hopefully I can return it back to dynamic. It's worth a shot and I already have it all backed up anyways.

---

### Post by stompy11 on 2010-08-27
yes that is a raid, infact its a raid 1 (redundant array of inexpensive disks) now if you have a raid card of if you are using the integrated mobo chip then that would be a hardware raid, if you use the O/S's controller then that would be a software raid.

---

### Post by Sylvester the Cat on 2010-08-27
Then I have a software raid. I turned it off and was able to actually get an install using the alternate install CD. Now when I tried to boot from GRUB it gives me a blinking cursor on the top and doesn't do anything else. Now I will try it again here soon as there were two options. But I'm a lot futher then I was before. :)

---

### Post by davidmohammed on 2010-08-27
excellent.  Remember to edit your grub (press shift then e - find quiet splash and add nomodeset before quiet splash e.g. ... nomodeset quiet splash -- )

---

### Post by Sylvester the Cat on 2010-08-27
I get a no kernal loaded message. Hmm... it could be lost in finding where it is installed but I did select partition the drive automatically and I received no error messages along the way during the install. The disk where the partitions were created do not show up in Disk Management however in Windows 7 but I'm wondering if that is the case because the drive is formatted as ext4. (basically what automatic partitioning did).

---

### Post by davidmohammed on 2010-08-27
The message means that Grub hasn't loaded the linux kernel - normally because it is either looking in the wrong location or because the kernel isn't where it should be. Go through the Grub Command Line section carefully and try booting using the examples found in this section:
[https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode")

---

### Post by Sylvester the Cat on 2010-08-27
I'm nearing the end of my rope with this. I never thought it was going to be this difficult to just get the OS running. I'm afraid of what I will encounter if I ever get through this. 

Currently nothing has changed. I tried entering in the following commands in grub

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

It spits a bunch of text then runs to a cursors where it sits. I know the OS is installed and it SHOULD have the root defined as I made sure of that during the partition section of the install. So at this point, I have no idea what to do. I'm running out of hair to pull. :)

---

### Post by davidmohammed on 2010-08-28
it sounds like you are almost there.  I agree, it should not be so difficult - maybe its due to how the partitioning has happened.

It would be useful to know what the last few lines outputted was. May be a picture of the screen? Hopefully this will give a indication of what the boot is stumbling over.

Can I suggest the following slight modification

```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro **noapic nomodeset**
initrd /initrd.img
boot
```

---

### Post by Sylvester the Cat on 2010-08-28
Here are some screenshots of what is happening right now

[IMG]http://www.monksonline.org/BrDavid/images/screenshots-1.jpg[/IMG]

[IMG]http://www.monksonline.org/BrDavid/images/screenshots-2.jpg[/IMG]

[IMG]http://www.monksonline.org/BrDavid/images/screenshots-3.jpg[/IMG]

---

### Post by davidmohammed on 2010-08-28
hmmm - the "target filesystem doesnt have /sbin/init" is due I think to a corrupt install/need to do a fsck on the ubuntu partition/the fact that the grub commands you have used are not complete.  If its the latter two, the usual remedy is to boot from the live CD and perform a fsck or to reinstall grub2 respectively. 

suggestion - using the grub link I gave you, look at the section "Boot a Specific Kernel Manually" and follow it to see if you can boot a specific linux kernel using the TAB key strokes as suggested to autocomplete text.  If this doesnt work, this I think would suggest the install wasnt successful.

 You did attempt to install from live CD previously, but that was when you were attempting to install via a software RAID.

Have you tried since then to use the 32bit/64bit desktop CD image to "try without installing"?  You may or may not have to add the "noapic nomodeset" boot options

---

### Post by Sylvester the Cat on 2010-08-28
Well I've had it. This has become way to complicated and infuriating for me to even continue today. Right now my machine will not boot. I have no idea why and I can only surmise that somehow my boot.ini file in my windows c: is corrupted. Because of that I am now terrified to continue unless I get absolute detail on a) how to start this process, that is, what EXACTLY does my machine need to have (hardware) and need to be (hardware settings) in order to start. 2) What does my machine need to look like, partitions, explicit setup directions so that I can install the CD and not have it freeze during booting. I unplugged every disk and just tried the live CD with one hard drive plugged in completely unpartitioned, unformatted, etc. Basically as if this was a brand new machine. Nothing. It froze in the exact same spot and no flag setting was able to get it going. 

If I can't install ubuntu from a fresh system then I obviously either 1) don't have the right system to begin with which makes me very frustrated or 2) I haven't the slightest idea what I am doing and need step by step personalized detailed instructions on how to do this. I don't see why this has to be so difficult but alas it is. Sorry about the rant, but I am just so infuriated at this process. Not to bitch but I've had my fair share of problems with Windows, but nothing as bad as this. I was almost positive things should have worked with a fresh system install. When that didn't work and now I can't even boot back to windows with everything plugged back in makes me terrified to continue. 

Again sorry for my rant but all I can say is .... wow.

---

### Post by davidmohammed on 2010-08-28
Yes - fully understand your frustration.  Looks like ubuntu is not going to install on your system.  I would love to get my hands physically on your system to understand why not.  Nevermind...

Plug your Windows 7 hard-drive back in.  If it cant boot, this is likely due to GRUB having overwritten somepart of the Windows 7 Master Boot Record.

This is well documented how to recover this - for example, have a look at this [step by step]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") guide.

To remove the linux partition, use the windows 7 disk management utility - you should  be able to delete, and then resize the windows  partition.  See here for a [step-by-step]("http://www.killertechtips.com/2009/05/05/how-to-resize-partitions-in-windows-7/") guide.  There are other guides available if you Google.

---

### Post by Sylvester the Cat on 2010-08-28
Please don't get me wrong. I fully appreciate all the help that I have received. I will be returning to this at some point but right now my head is not where it needs to be to figure this all out. Again... thank you thank you thank you for your help and patience with me with this. :D


I was able to get my boot record back btw. Oh Internet, how did we live without you?

---

### Post by Sylvester the Cat on 2010-08-29
Yeehaw!

That's right... I'm posting this from Ubuntu. I got the damn thing installed using the regular ISO desktop install disk. How? I got to thinking, everybody seemed to have it easy and yet I have it hard. Okay... let's take this from the other direction. Let's make this machine as "simple" as possible. So I unplugged everything and kept only the essentials: DVD drive, hard drive, graphics card, sound card (not essential), and of course the guts. Popped in the install disk and whammo. Came right up.

So basically something I have plugged into this computer is the culprit. I haven't a clue as to what that is and could be a variety of things: two monitors plugged in, my printer, my second DVD drive, my 12-1 card reader, the wireless modem I removed completely. It could have been any of those things I unplugged. So now it's time to plug things back in and have a little fun here and of course actually do what I set out to do here in the first place.

Unbelievable. I would love to know which device caused the problems. I will mark this as solved and would love to thank everyone here who helped. I apologize again for losing my temper on this as well.

---

