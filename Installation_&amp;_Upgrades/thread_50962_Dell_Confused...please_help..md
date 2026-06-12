---
title: "Dell Confused...please help."
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by Emerzen on 2005-07-22
Linux newbie who installed Fedora 3 from a pressed CD easily.  Tried to install Ubuntu from burned iso CD, and system would hang after hitting enter at boot prompt.  Same thing happened w/ burned iso of Fedora 4.  (BIOS set to ignore RAID/AHCI and set up ATA).  As I was pulling the Ubuntu CD out of drive one time, the installer kicked in and everything went flawlessly.  I got curious and tried Fedora 4, which then installed no problem.  Missed Ubuntu and tried going back and the same problem is occurring now.  I've tried every possible variation of BIOS setting w/ no luck.  Install hangs immediately after vmlinuz thing flashes across screen.  It hangs w/ every possible install parameter applied as well.  This makes no sense to me, why would it have worked just that one time?  

Dimension 8400 (P4 w/ HT) BIOS AO6
Intel 925x express chipset
2 SATA 80GB HDD
Hitachi DVD ROM
Sony DVD RW
Integrated ethernet/audio
NVIDIA 

Knoppix runs flawlessly as well.  Sorry for the long post but I'm exasperated.  Thanks.

---

### Post by ltmon on 2005-07-22
Have you been able to check the md5 sums of your ISOs to ensure they burnt correctly?  Perhaps if your burner is misconfigured or has bitten the dust this can happen.

On windows you can use [www.md5summer.org](www.md5summer.org) and check the iso files have the md5 sums which will be available in the same place you downloaded the iso.

L.

---

### Post by Emerzen on 2005-07-22
Thank you but I did check both the md5 and sha1's which were correct.  And, the one time it did install I ran mediacheck which passed.  I'm thinking it must be related to the drive controller and opening the drive door?  But it hasn't worked since.

---

### Post by nyfreakinrican7 on 2005-07-22
i was having that problem at first and I had to format the drive with the harddrive utility from maxtor then try the ubuntu cd. I think it was because i had a failed mandrake install on the drive but i am new to this all so i am just guessing

---

### Post by Emerzen on 2005-07-23
Everyone who replied thanks for the help.  For anyone w/ a Dell Dimension 8400 this may help as it is what I had to do to get Ubuntu installed.  

Go into the system BIOS (latest is AO6).
Under Drives I used "combined" (don't know if this is necessary)
Under devices, select "usb controller"
choose the "no boot" option (this is necessary)

Installed perfectly after that.  I'm don't know exactly why this worked, but from bug threads I read, it seems there is a conflict between the BIOS usb controller and the linux one w/o this selected.  Good luck.

---

### Post by Spano on 2005-08-21
Re: Dim8400 user needs help 

> Hi Emerzen,
hope this is not an interruption.
I have installed ubuntu onto Dim 8400 using bios settings you suggested in a post. I boot into Ubuntu
but can't see desktop, audio works. Any ideas for me?
I can boot into recovery mode - maybe an update kernel command from there?
Help for this noob appreciated.
Dan 



Hi Spano, it's not an interruption at all. I'm a noob myself, but I'll take a shot at it. A couple of questions first: what version of Dell's BIOS do you have (I believe the latest is AO6)? How many hard drives do you have? What's your video card? Do you still have Windows installed somewhere?

Lemme know and I'll see what I can figure out.

Thanks Emerzen,
Bios is A06.
I have two 80Gb hard drives, a Seagate SATA with With Windows XP on the 1st primary partition, GRUB is located on the MBR of this disk.  A Western Digital PATA (IDE), partitioned with a 4Gb scratch/swap for Photoshop on 1st primary, 40Gb 2nd primary where Ubuntu is installed and 30 something GB extended for storage.

Vid card is Nvidia GeForce 6800 PCI express 256Mb.  Monitor is 21" Samsung SyncMaster 1100DF CRT.  When I boot Ubuntu the display is a bunch of staticy long vertical stripes.  I can log in blind and get a console with Ctrl Alt F7 and have
downloaded and installed all updates using command line - no improvement.  I have also formated and reinstalled.  I know the iso. I'm using is un-corrupted because I used it to install on an older Dell.

That's all the details, what do you think?

---

### Post by Emerzen on 2005-08-22
Hi Spano, good idea about moving this thread.  Unfortunately, I didn't have these difficulties and I'm a newb myself, so I don't have any really helpful advice.  Given your description, it sounds like your having trouble between the Xserver and your NVidia drivers.  I've seen alot of posts w/ people having difficulty w/ Nvidia drivers.  I don't have the same card as you, so I didn't run into this problem and haven't done any research on it.  There's some stuff on the Wiki when I did a general search.

 [https://wiki.ubuntu.com/NvidiaHoaryRemoval?highlight=%28nvidia%29](https://wiki.ubuntu.com/NvidiaHoaryRemoval?highlight=%28nvidia%29)

I'll keep an eye on this thread, but I would repost asking for any similar problems w/ Nvidia drivers specific to your card.  Do you have a live CD?  You could try booting from a live CD and see if you have similar problems.  I'll run through my BIOS settings one more time to see if any ideas pop up.  You could also try Breezy, which I hear is pretty stable now, and see it doesn't solve your problems.  Good luck, I hope you figure it out soon, 'cause I've thoroughly enjoyed Ubuntu and you should too.  -Take care

---

### Post by Emerzen on 2005-08-22
[QUOTE=Spano]Re: Dim8400 user needs help 



Thanks Emerzen,
Bios is A06.
I have two 80Gb hard drives, a Seagate SATA with With Windows XP on the 1st primary partition, GRUB is located on the MBR of this disk.  A Western Digital PATA (IDE), partitioned with a 4Gb scratch/swap for Photoshop on 1st primary, 40Gb 2nd primary where Ubuntu is installed and 30 something GB extended for storage.

Vid card is Nvidia GeForce 6800 PCI express 256Mb.  Monitor is 21" Samsung SyncMaster 1100DF CRT.  When I boot Ubuntu the display is a bunch of staticy long vertical stripes.  I can log in blind and get a console with Ctrl Alt F7 and have
downloaded and installed all updates using command line - no improvement.  I have also formated and reinstalled.  I know the iso. I'm using is un-corrupted because I used it to install on an older Dell.

That's all the details, what do you think?[/QUOTE]
 Spano, I just looked at the BIOS and I realize there are two primary video driver settings.  One is PCI and the other is PEG.  I don't know which yours is set to, but you could try changing whatever setting you have to the other one and see if that helps.  You could also try reinstalling w/ the opposite setting that you have now.  I would see if you can boot into Windows w/ the opposite setting before reinstalling, just to make sure that it works.  Hope that helps.  By the way, mine is set to PEG.

---

### Post by Spano on 2005-08-25
Emerzen, 
thanks for keeping me in mind.  I have solved my display problem.  As usual it came down to reading the instructions :-?  The Unofficial Ubuntu 5.04 Starter Guide.
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)
I installed the driver from recovery mode, got a 800x600 display, then ran
"sudo dpkg-reconfigure xserver-xorg" from console to get the resoloutions and
refresh rate options I wanted.

I am going to look into that PCI PEG setting prior to reinstalling Hoary or upgrading
to Breezy, but I believe that setting is specific to ATI vid cards.  Check this:
[http://www.findarticles.com/p/articles/mi_zdext/is_200408/ai_n7184147](http://www.findarticles.com/p/articles/mi_zdext/is_200408/ai_n7184147)

---

### Post by Emerzen on 2005-09-03
Spano, glad you got it figured out.  Ubuntu (OSS in general) is awesome and I'm glad you can join in the fun.

---

