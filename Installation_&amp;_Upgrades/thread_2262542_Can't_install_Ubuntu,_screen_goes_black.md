---
title: "Can't install Ubuntu, screen goes black"
date: 2015-01-25
forum: Installation &amp; Upgrades
---

### Post by benjamin34 on 2015-01-25
I'm running Windows 7 Ultimate 64 bit edition on a 3TB GPT hard drive with the standard three partitions that Windows creates. I have an ASRock Z97 Extreme6 motherboard with an Intel i7 4790k processor and 8GB of RAM.


I've been trying to install 64 bit Ubuntu alongside Windows for several days now and keep running into the same error. I create a bootable USB drive for the installation ISO and boot from it on startup. I am given the option to boot through BIOS or UEFI (two different options for the drive when I pull up the boot menu), but the outcome is not different for each, just the interface. When faced with the menu to choose whether to try or install Ubuntu, selecting either option brings me to a black screen. I've let the screen sit like this for a couple hours and nothing changes. On a USB drive with an activity LED on it, the LED does not flash during this time.


I have tried deleting the installation ISO and redownloading it, to make sure the file downloaded correctly. I have tried rewriting it to the USB drive, trying a different drive (including one that I just recently successfully used to install Windows), and then trying a different USB writer on each USB drive (tried Rufus, Pen Drive Linux's USB installer, and ImageUSB). None of this has changed anything. I have no idea what the problem could be, as on the same hardware I have previously been able to start the installation of Ubuntu (I quit halfway through). The only difference between then and now is that I've installed a better CPU cooler and an additional case fan.

---

### Post by kerry_s on 2015-01-25
you left out the most important part, video card?
i'm guessing something so new there's no drivers for it yet?

---

### Post by benjamin34 on 2015-01-25
No, I've been using the native graphics on the CPU. I haven't needed to run anything too video intensive (most I've done with this system is a Blue Ray disc), so I haven't bought a dedicated GPU yet. Regardless, I mentioned that I've previously been able to get through part of the installation that I am now unable to, and that was without a video card.

---

### Post by kerry_s on 2015-01-25
okay lets try again, my native video driver is a intel 945g, not amd, not nvidia.

if your not sure look in your bios or your manual cause i assume you built this beast. :) a very nice motherboard by the way, whole lot of options on that puppy.

---

### Post by benjamin34 on 2015-01-25
The drivers are Intel HD Graphics 4600. Connected with a DVI cable, I don't have another connection handy.

---

### Post by jorge8 on 2015-01-25
Are you installing the same distro version as the last time you had some success?  I'd try using something like the Ubuntu 14.04 minimal, I've been able to install this on a wide range of setups:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by benjamin34 on 2015-01-25
I tried installing version 13.10 and 14.04.1, both ran into the same problem.

---

### Post by kerry_s on 2015-01-25
a quick google will tell you there are lots of issues with "Intel HD Graphics 4600" , but there are many people who worked through it so just hang in there & hopefully they will chime into help you.

---

### Post by jorge8 on 2015-01-25
[Some posts out there]("http://unix.stackexchange.com/questions/161815/intel-hd-4600-graphics-card-not-supported-in-linux-mint-17") say that linux only supports a low resolution of 1920 x 1200 on the Intel HD 4600 graphics chip.  Can you try lowering the resolution in the BIOS for the purpose of going through the install process?

After that, you can try installing the driver for Intel HD 4600 found [here]("https://01.org/linuxgraphics/downloads").

---

### Post by benjamin34 on 2015-01-25
I didn't see a resolution setting in my UEFI, but the mini installation suggested by jorge8 got me farther than I had before. It stuck at 0% when it got to "detecting disks and other hardware."

---

### Post by kerry_s on 2015-01-25
i would hold off on linux install till they fix the issues. if you want to use linux i would recommend you just run it in virtual box in your windows install.

---

### Post by benjamin34 on 2015-01-25
How long have these issues persisted? I saw results on Google indicating that people were having Intel graphics driver problems with Ubuntu 12 releases, how long do you think it'll be before they're resolved?

---

### Post by jorge8 on 2015-01-25
You may need to configure your settings to set your installer drive as a UEFI boot device... I had better luck burning the Ubuntu Minimal to a CD, and setting it as a UEFI bootable CD drive, but it may be possible to set a USB flash drive as a UEFI boot drive.  While you're at it, can you configure your target disk drive as a UEFI drive too (if it's not set to that already)?

---

### Post by benjamin34 on 2015-01-25
I did boot it as a UEFI drive. I mentioned in my first post that when I'm at the boot menu, there are two entries for the USB drive. One is UEFI, and the other is BIOS (though BIOS isn't explicitly labelled, it just lacks a UEFI label). Picking the UEFI one doesn't make any difference. I'm not sure how to configure my hard drive as a UEFI drive. I know that it boots through UEFI, otherwise it wouldn't be able to use the GUID partition table that I've got on it. Windows is unable to boot GPT drives through BIOS.

---

### Post by jorge8 on 2015-01-25
Glad you made some progress... but I'm running out of ideas on how to get you to a completely installed setup.  Personally, I install from CD just because I've had issues with UEFI USB drives in the past, but I doubt that would fix your problem.

The next step is to find out what hardware the installer is trying to read when it hangs.  Can you press ctrl-D or Ctrl-Z when it hangs?  This usually brings you to a more advanced menu... I don't recall, but I think it might give you an option to see a verbose output from there, or at the very least an option to get a command line that you can use to read some of the /var/log files.

---

### Post by benjamin34 on 2015-01-25
Alright, so now I'm trying to install 14.10 64 bit from a USB drive. The drive is GPT, FAT32, written using Rufus. I booted it through UEFI, and tried the "try without installing" option. I got to the loading screen ([http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png](http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png)), and it was active for a time, and then froze. Nothing I pushed on the keyboard did anything, including ctrl-D, ctrl-z, esc, or the sweep I did across the whole thing with my hand. The restart button on my case didn't do anything, and pressing the power button once did not shut down. I had to hold the power button to get the computer to turn off.

---

### Post by MAFoElffen on 2015-01-25
So you used Rufus to create your bootable USB thumb drive. I'm familiar with Rufus.

In Rufus:
Check the checkbox to create an EFI bootable drive.
Select ISO.
Creates the drive as an EFI bootable drive.

Your motherboard if UEFI BIOS. So when you go to the Boot device menu on boot, it will show the USB drive in the EFI boot menu. Select that.

*** If you did that without creating an EFI boot... your motherboard won't boot from a legacy BIOS boot USB device.

The internal graphics that you are using is Intel HD, so should come up with the default Intel X drivers...

---

### Post by benjamin34 on 2015-01-25
I know, I talked about that above. If you select GPT for the partition table, there is only UEFI as an option. You can do MBR with just UEFI or both BIOS and UEFI, but I was always choosing GPT for that reason.

---

### Post by MAFoElffen on 2015-01-26
Okay, you are not making much sense to me, so lets lay this out (clearity)....

What are your trying to install from? What you are trying to install from does not need to be anything but an MBR w/ VFat. the EFI support that Rufus adds to it to see is an FileName.efi file for the UEFI BIOS to see as a USB boot device.

For new internal drives, that would be partitioning and such. But you did not say you were adding a new drive, so what are you really talking about. Let us get a common vocabulary so we can understand each other and you could be helped. Good idea?

---

### Post by benjamin34 on 2015-01-26
Sorry if I sound irritable, it's just that I feel like I laid out a lot of those details already throughout the discussion. Anyhow, it can't hurt to summarize.

I'm trying to install 64 bit Ubuntu (at this point, any fairly recent release) onto a partition on an internal hard drive. The internal hard drive uses GPT because it's a 3TB drive (MBR cannot recognize more than 2.2TB). I have Windows on one partition of this drive. I understand that because the drive I am installing to is GPT and boots through UEFI (Windows cannot handle GPT drives through BIOS) that my Ubuntu installation must also boot through UEFI. The drive I am installing from is a USB flash drive that I've used Rufus to prepare with the installation ISO (I have tried other programs to do this as well, such as ImageUSB and Pen Drive Linux's Universal USB Installer, along with trying all these programs on a different USB flash drive). Within Rufus, I have tried preparing the drive with an MBR partition table (with the option that allows both UEFI and BIOS), and I have more recently tried preparing it with a GUID partition table (GPT). Though I tried a few times booting the flash drive through BIOS, I stopped when I realized that I needed to boot through UEFI for the install to work alongside my Windows installation. Since then I have booted the flash drive exclusively through UEFI, whether it's MBR or GPT. The formatting on the flash drive I've left as FAT32, which is the default option. I'm not sure how picking a different file system would help, since Linux shouldn't have a problem reading FAT32, though I could try NTFS.

---

### Post by MAFoElffen on 2015-01-26
K.I.S.S.--For your mobo and alongside recent Windows, your USB thumbdrive should be mbr, fat32, created w/ the efi option selected. That is just a defaultly formatted USB thumbdrive, just like they come out of the package... The special part of that is the 64bit *.efi file that Rufus adds if you have a 64bit ISO to put onto that.

Does that explanation work for you and provide you enough info?

Next would be to ask if you verified the md5 checksum of the downloaded image(?)... to make ensure that image is uncorrupted and bootable.

Heading out the door... Will check back later this morning, on my breaks.

---

### Post by benjamin34 on 2015-01-26
I already tried setting up the drive with MBR with the option to boot with efi, again, as outlined above. Have only used FAT32 formatting. I haven't checked the ISO to see if it's corrupted, but I did redownload it numerous times, trying a few different releases. If the ISO is corrupted, every single one I downloaded (like, at least seven or eight) has been corrupted.

---

### Post by MAFoElffen on 2015-01-26
Win 8, you can check via commandline, for Win7 --> Free at M$:
[http://www.microsoft.com/en-us/download/details.aspx?id=11533](http://www.microsoft.com/en-us/download/details.aspx?id=11533)

---

### Post by benjamin34 on 2015-01-26
Alright, I checked the md5 hash. It matches the one Ubuntu lists on their website for one of the ISOs I've been using to create the bootable USB drive.

---

### Post by jorge8 on 2015-01-26
imho I think the problem is with a hardware compatibility issue.  The installer seems to hang when discovering components on your motherboard.  Too bad your computer completely hangs during the install.... I'd like to know what it was doing when it hangs.

I've searched for ways to get a verbose output from the installer but haven't found anything.  Does anybody else out there know how to perform a verbose ubuntu install?  Perhaps an unattended install distro that just spits out every command that it's doing during the install?

---

### Post by benjamin34 on 2015-01-26
> **jorge8 said:**
> imho I think the problem is with a hardware compatibility issue.  The installer seems to hang when discovering components on your motherboard.  Too bad your computer completely hangs during the install.... I'd like to know what it was doing when it hangs.

I've searched for ways to get a verbose output from the installer but haven't found anything.  Does anybody else out there know how to perform a verbose ubuntu install?  Perhaps an unattended install distro that just spits out every command that it's doing during the install?

I agree with you, I think it's likely hardware, but I'm still bothered by the fact that I've gotten this installation further in the past on the same hardware (save for a couple case fans and a CPU cooler). Previously, I got to the point where you choose the partition to install on, but I wasn't sure how I wanted to split it up at the time so I quit the installation. That was about a month and a half ago, and I don't remember the exact details of how I wrote the USB drive and such, but the internal drive was MBR at the time.

---

### Post by MAFoElffen on 2015-01-26
I just re-read all your posts... I see that you have tried 13.10, 14.04 and 14.10. I see you have tried desktop edition and mini. On the mini, where the install graphics are VGA palette,  you said it stopped right after searching for 'devices and hardware." That is not at a point in the install where you would be able to pop over to tty terminal to do any tests is it(?)

What you did not say is if you could select the option "Try" and even run Ubuntu. That is what we usually suggest. Try to run it without installing to see if it will run or to see what will be needed extra to do that. If you can get "Try" running in the live image, then you can pop over the the live image during the install, to view the installation logs and query the sys to see what or what is not going on.

What I also didn't hear was at what point did it fail on the desktop edition installation disk. Did you see the initial dark purplish panel that has the person/keyboard icon at the bottom? If so, what did you do on that panel? Did you left that pass? Or did you [press escape to get the the advanced install menu? At least at that menu, if you can get to it, you get a change to change some startup options...

EDIT- I see that Intel updated their Linus Drivers for HD4600 8/13, so they are in xorg...

---

### Post by benjamin34 on 2015-01-26
I found out that the mini installation can't be done in UEFI ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), "Note: While the mini ISO is handy, it isn't useful for installing on UEFI-based systems that you want to run in UEFI mode. The mini lacks the proper files for booting the computer in UEFI mode. Thus, the computer will boot in BIOS compatibility mode, and the installation will be in BIOS mode"), so I don't think that's worth pursuing.

About half the time at first I was choosing the "try" option and getting the same result. The last few times I've chosen the "try" option every time.

I did not see the screen you described since it only appears that way (orange, keyboard at bottom) in the 32 bit installation. The screen I see is black, and looks like this: [http://pix.toile-libre.org/upload/original/1347445084.png](http://pix.toile-libre.org/upload/original/1347445084.png)

I select the option to "try" and I get to a screen that looks like this: [http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png](http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png)

Sometimes it will show the dots moving for a bit before freezing, sometimes they never start and remain frozen, but this is where the installation sticks. At this point, pushing ESC, CTRL-D, CTRL-Z, or any other single key (tried them all) does nothing.

---

### Post by jorge8 on 2015-01-27
Just curious, is there a chance your hard drive might be failing?  I might be off base, but the last time my computer hung on the [boot screen]("http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png") was when one of my drives was corrupted.

---

### Post by benjamin34 on 2015-01-27
That's possible, but I hope it's not the case. It's a month and a half old drive. I ran a check disk last week and it came up with no errors, but otherwise I'm not sure how to diagnose it.

---

### Post by kerry_s on 2015-01-27
i think it's just the motherboard not fully supported by linux. like i said you have great specs, hopefully you have windows that's still working. you can run linux in virtual box & not worry about compatibility.

---

### Post by benjamin34 on 2015-01-27
Oh my God, dude, thank you. That prompted me to do a Google search for the motherboard having issues with Ubuntu and I found the solution. Had to disable ASMedia SATA3 mode deep in the UEFI settings. Installed just fine after that.

---

### Post by MAFoElffen on 2015-01-27
Okay... Was curious what my Lenovo showed as. The photo's here were on my Lenovo. UEFI Bios. Booted to boot menu. USB thumbdrive was made with Rufus, selecting efi boot and using an Ubuntu 14.04.1 LTS Desktop Ed., 64 bit ISO file.
[ATTACH=CONFIG]259546[/ATTACH][ATTACH=CONFIG]259550[/ATTACH][ATTACH=CONFIG]259549[/ATTACH][ATTACH=CONFIG]259548[/ATTACH][ATTACH=CONFIG]259547[/ATTACH]
Notice the third photo above? EFI USB boots to a grub Menu... You say yours doesn't?

EDIT-- Never mind, just noticed your last post... Good finding that. Please mark this thread as solved.

---

### Post by benjamin34 on 2015-01-27
It looked like the third, but I just fixed the problem.

---

