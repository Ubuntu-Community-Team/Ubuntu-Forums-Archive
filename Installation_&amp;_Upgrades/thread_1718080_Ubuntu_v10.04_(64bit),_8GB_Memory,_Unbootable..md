---
title: "Ubuntu v10.04 (64bit), 8GB Memory, Unbootable."
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by landstander on 2011-03-30
System Specifications:
----------------------
OS: Ubuntu v10.04 LTS (64 Bit)
Mother Board Brand: ASUS
Mother Board Model: P5E3 Delux
CPU: Intel Quad Core 2 Extreme X9650  @ 3.00GHz
RAM Ammount Currently Installed: 4GB (2 sticks by 2 GB ea.)
RAM To be installed: 4GB (2 sticks by 2 GB ea.)
RAM Brand: Patriot
RAM Model: PC3-10666
RAM Voltage: 1.7V
RAM Timing: 7-7-7-20
Video Card: nVidia G92 [GeForce 8800 GT]

Description of Problem:
-----------------------
Whenever I install the extra 4GB of RAM to bring the system up to a full 8GB of memory, Ubuntu hangs or freezes during the default boot splash screen. (The screen that has a sort of purple background with dots changing color between red and white under the word Ubuntu).

Extra notes about the problem:
------------------------------
All utilities I could find report that the memory chips are in good working condition and report no problems at all. In fact the system runs great with 4GB of memory, and I can swap sticks in and out of the bays and no problems occur as long as I keep it under or at 4GB. Its just when I try to install more than 4GB that the system freezes up during the boot screen, and yes it is a 64bit version of the OS that I'm using.

Questions:
----------
Is there anything else I might try before biting the bullet and spending all my Mom's beer money on new memory chips?

Notes:
------
Its not that important to have 8GB, my reasons for trying to get it to work is that I already have the chips here on the table waiting to go into the computer, and it would be nice to have 4GB available for guest Operating Systems in virtualbox.

Thanks.

---

### Post by Hedgehog1 on 2011-03-30
> **landstander said:**
> System Specifications:
----------------------
OS: Ubuntu v10.04 LTS (64 Bit)
Mother Board Brand: ASUS
Mother Board Model: P5E3 Delux
CPU: Intel Quad Core 2 Extreme X9650  @ 3.00GHz
RAM Ammount Currently Installed: 4GB (2 sticks by 2 GB ea.)
RAM To be installed: 4GB (2 sticks by 2 GB ea.)
RAM Brand: Patriot
RAM Model: PC3-10666
RAM Voltage: 1.7V
RAM Timing: 7-7-7-20
Video Card: nVidia G92 [GeForce 8800 GT]

Description of Problem:
-----------------------
Whenever I install the extra 4GB of RAM to bring the system up to a full 8GB of memory, Ubuntu hangs or freezes during the default boot splash screen. (The screen that has a sort of purple background with dots changing color between red and white under the word Ubuntu).


Thanks.

When you have all 4 sticks of RAM installed, do you get the normal single beep during POST?  Can you see all 8 gigs from the BIOS?

Will the Ubuntu LiveCD/LiveUSB boot with the 8 gigs in the system?

Are the RAM sticks all the same specs?  Not all TAM can be mixed together.

This will give us something to work with....

***The Hedge***

:KS

---

### Post by landstander on 2011-03-30
Q: When you have all 4 sticks of RAM installed, do you get the normal single beep during POST? 
A: Yes.

Q: Can you see all 8 gigs from the BIOS?
A: Yes.

Q: Are the RAM sticks all the same specs?
A: Yes all are exactly the same and were all purchased at the same time from the same place. However, at the time of purchase I couldn't find much information about weather or not these chips would be compatible with Linux, but from what I've seen so far they seem like they should be (sans this 8GB problem).

Q: Will the Ubuntu LiveCD/LiveUSB boot with the 8 gigs in the system?
A: I haven't tried this yet, but I'm thankful for the suggestion as I had not thought of that. I will give this a try soon, and report my results.

Note: 
It doesn't always hang at exactly the same time into the boot splash screen. Some times it hangs right away, and some times it takes a bit longer before it freezes up, but it will always freeze up once the 8GB are in place. I'll give the boot disk a try with the 8GB installed tomorrow morning and report back sometime in the late morning.

Thanks for the suggestion. :)

---

### Post by landstander on 2011-03-31
Update:
This morning I tried installing all 8GB and booting up the computer without the Live CD in the tray. The result was that the first bootup of the morning made it all the way to where you first see your mouse pointer show up on the screen (right before it displays a login prompt)and this is where it froze completely. All successive boot up attempts froze up some time during the boot splash screen.

So then I tried the suggestion of using a Live CD to boot up:
The result was unfortunately the same. It froze up during the Ubuntu splash screen described in my first post.

Current Status:
Unsolved. :(

---

### Post by Hedgehog1 on 2011-03-31
This is useful.  It tells that that those RAM sticks in that motherboard with the current BIOS level  is not properly supporting the 8 gigs (and it is not the Ubuntu install on the Drive).
 
Next thing to check: Is there a more current bios level you can flash the motherboard to? I had to do this to get my current motherboard to get all it's advertised features to work properly.  _It is worth warning you_: **Flashing BIOS carries some risk, and most bios flash utilities require windows to run them.**
 
***The Hedge***
**** 
:KS

---

### Post by landstander on 2011-04-01
**UPDATE:**
I've just spent all day looking into updating my BIOS and I now remember why this is impossible to do for the following reasons:
**1st Problem.)** The Mother Board User Manual says to use a floppy disk, but Ubuntu can't recognize floppy drives any more by default.
**1st Solution.)** Accessing floppy drives can be restored as a feature by downgrading the package udisks (in synaptic package manager) to an earlier version and then manually mounting the floppy drive via the command line.

**2nd Problem.)** Once you figure out how to get access to the floppy drive you then suddenly realize that the BIOS ROM file that you need for flashing the ROM is too large (a 2 MB file) to fit onto a standard floppy disk (1.44 MB capacity limit). 
**2nd Solution.)** The ASUS EZ Flash Utility provided by the BIOS is reported by ASUS to be able to recognize a USB stick. However this leads directly into problem #3.

**3rd Problem)** The ASUS EZ Flash Utility freezes every time it is run, and gives no access to any drives or files to flash the BIOS with.
**3rd Solution.)** _No solution_ or solution pending. Here is a screen shot of the BIOS EZ Flash utility in its frozen state:
[[IMG]http://img820.imageshack.us/img820/8544/img4754s.th.jpg[/IMG]](http://img820.imageshack.us/i/img4754s.jpg/)
Click the image to enlarge.

**Note:** The use of the word "freeze" or "frozen" in problem #3 above means that the computer is no longer recognizing any input from the keyboard or mouse, and the hard disk drive sounds quite, indicating no activity.

**In short:** ASUS has royally and quite permanently screwed me over.
**Current Status:** _Unsolved._ 

Any tips, tricks, work arounds, or hacks would be greatly appreciated at this point.

---

### Post by landstander on 2011-04-01
**Update:**
**Theory:** Since there are no FAT32 disks present maybe the ASUS EZ Flash utility freezes because it can't find a file system?

**Note:** This theory is flawed because the floppy disk drive is functioning correctly due to tests done on Ubuntu (was able to read and write to a floppy disk in the floppy disk drive), and the ASUS EZ Flash utility was still not able to see or recognize that there was a bootable MSDOS FAT32 formated disk in the drive tray. Not that it would have mattered since the necessary files are to large to fit on a floppy disk any way.

**Testing a useless theory out of desperation:**
I created a bottable MSDOS FAT32 formated USB stick and tried booting the computer with it installed in various USB ports after each reboot (just in case for whatever reason it wasn't being recognized in one of the USB ports).

**Results:**
For each reboot, the ASUS EZ flash utility freezes up the same way as described in my previous post (see the picture).

**Whats Next:**
I might try and start a troubleshooting ticket with ASUS to see if they can help.

**Current Status:**
Unsolved and painfully angry with ASUS for lying to me in order to make a sale.

---

### Post by oldfred on 2011-04-01
I have seen a lot of users with BIOS settings issues. Different BIOS seem to have different names for similar settings. See if any of these look like they may help (or not).

BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by landstander on 2011-04-01
oldfred:
My apologies if my last post was somewhat confusing. 

To be clear there are no problems with accessing any media associated with this computer (sans any chips that bring the computer over 4GB of memory). 
This thread started as a thread dedicated to solving the problem of upgrading the memory on an ASUS P5E3 Delux WiFi/AP@n Motherboard from 4GB to 8GB. 
Through careful examination it has been somewhat determined this might be BIOS problem. However ASUS does not provide a working method for flashing the BIOS.

Thank you for your interest in helping, and thanks for your suggestions.

Note: This is an older version of the ASUS BIOS and does not have any capability to boot from a USB stick, which is another reason I find it strange that the Motherboards user manual would say to use a USB stick to flash the BIOS. (No surprise when that didn't work either.)

---

### Post by oldfred on 2011-04-01
I do not have Asus but do not have to boot from the flash drive. The BIOS will directly read a FAT formated flash drive. 

Mine has three ways, windows boot, boot a floppy or flash, or directly read flash from just booting into BIOS.

We find BIOS settings affect a lot of surprising things. So it was just a suggestion.

---

### Post by Hedgehog1 on 2011-04-02
landstander,

To begin, you get 5 gold stars for both effort and documenting your findings and results!  :KS :KS :KS :KS :KS

Now - I was in a similar situation not too long ago - the mother board I had only supported 4 gigs.  I wanted 12 gigs.  That box became a nice PC for my Dad, and I got a new bare bones system and built that up.

In your case (as I believe the budget is small for you right now), consider a motherboard swap (keeping your CPU, RAM)  This means selecting *just the right* mother board (Like Goldilocks - it has to be 'just right') so everything can move over.

It's just a thought.

***The Hedge***

:KS

---

### Post by Quackers on 2011-04-02
On a different tack altogether - have you tried the nomodeset boot option?
When booting from the cd and at the FIRST purple screen, press any key. Then choose your language and at the next screen press F6. Some options will appear bottom right. Choose the "nomodeset" option and see if the live desktop will then load.

---

### Post by landstander on 2011-04-02
First, thank you all so much for your help and support. I really appreciate it.

**_Responses:_**
**oldfred:**
I wish my BIOS worked as well as yours does, however if you look at the picture in my 4th post you'll see that if I try to boot a flash drive directly read flash from just booting into BIOS that the BIOS just freezes up and doesn't give me any access to any files, folders, directories, disks, flash drives or anything, and I'm determined to stay away from Windows to flash my BIOS because I'm convinced it can be done without the use of Microsoft products. As far as booting from a USB stick, my BIOS is too old and doesn't support booting from a USB drive. As far as booting from a floppy drive? After telling the BIOS that it has a floppy drive to work with, and setting it up to boot from that floppy drive, the light on the floppy drive comes on as if the disk is being read but then, the computer just skips over it and boots as if there was no floppy drive attached. I've tried many different floppy boot disks, I've tried reformatting them in many different ways. I can read and write to the floppy drive so I'm not sure why it doesn't take the floppy disk during boot process especially when the disk has everything on it that it would need (including its boot sector and boot files) in order to boot up and start a DOS environment.

Sorry for the long response its just that oldfred made a lot of really good suggestions and I wanted to give him a chance to understand where I'm at in this process.

**Hedgehog1:**
I think your most recent suggestion might eventually end up being the one I have to take in order to solve this problem. Hopefully I won't get to that dark place where I've exhausted every possible solution.

**Quackers:**
Once I have 8GB of memory installed, that first purple screen is where the computer freezes, so pushing any key at that point produces no results since the keyboard as well as the computer is unresponsive (no hard disk lights... nothing). The only thing I can do at that point is to shut the computer off and reduce it back down to 4GB and since the computer works fine with 4GB then the boot disk option becomes irrelevant. It sure would be nice to have that full 8GB though. ;)

**_Update:_**
I've been reading in other forums that at least a few people found some success by doing the following:
**1.)** Burn a bootable FreeDOS Live CD.
**2.)** Burn a secondary CD that contains the Motherboard manufacturer's (in this case "ASUS") BIOS Flash utility, and the new BIOS file that will be needed when flashing the BIOS.
**3.)** Reboot the computer using the FreeDOS Live CD.
**4.)** Once FreeDOS is booted, take out the FreeDOS live CD and replace it with the CD that contains the BIOS Flashing utility and files.
**5.)** Flash the BIOS.

**My attempts at step 1 from the above steps:** 
**1st attempt:** I used AcetoneISO (available in the Ubuntu repositories, awesome program, tone of features!) to extract the FreeDOS iso to a directory called FreeDOS. I then added the ASUS BIOS Flash utility and the most recent BIOS from ASUS for my Motherboard to the FreeDOS directory. I then used AcetoneISO to create a new iso file form the files in the FreeDOS directory.
**1st attempt result:** A non-bootable CD which ended up in my recycle/art parts pile.

**2nd attempt:** I used Brasero Dis Burner (also in the repos) to burn the FreeDOS iso to a disk checking the box that leaves the disk open to add more files when its done burning. I then burned the ASUS BIOS flash utility and the new BIOS file to that same disk.
**2nd attempt result:** The disk actually booted! :shock: ...but after the FreeDOS boot screen where I select the option to continue booting FreeDOS, it spits out a bunch of text and then freezes and reports that the BIOS can't recognize the number of sectors or tracks. :( Here is a picture of that pitiful story:
[[IMG]http://img197.imageshack.us/img197/8135/frozenfreedos.th.jpg[/IMG]](http://img197.imageshack.us/i/frozenfreedos.jpg/)

**3rd attempt:** I used GnomeBaker CD/DVD writer this time burning at a slow speed with every safety caching backup checking option to create a good working CD.
**3rd attempt result:** Same exact result as the 2nd result above. See the picture.

**What next:**
I've started an ASUS support request, and 2 days later I'm still waiting to hear back from them. Maybe I'll start a new thread on a FreeDOS forum to see if any one over there can help me understand why there OS doesn't seem to work. Or maybe I'll see if someone on a CD/DVD burning forum can help me create a disk that actually works. 

**Comment:**
WOW computers are almost more trouble then there worth, but when I think of how busy I am with all these wonderful hardware problems to troubleshoot for days on end with no end in sight I feel a strong sense of having staved off weeks of boredom that can now be replaced with school since spring quarter starts on Monday. :)

Thanks again for all your help and encouragement. I seriously would have given up by now if it wasn't for all your great suggestions and helpful constructive comments. Thanks. :D

**Current Status:**
Unresolved.

---

### Post by Hedgehog1 on 2011-04-03
landstander,

Your posts are very well organized and readable!

I am (sorta) glad you were able to stave off boredom...  I think...

*If you get this fixed and need to kill hours of useful time, baseball season is upon us.* :D

Anyway, I do fear we have created a monster (who writes really good posts).  Being tenacious is all good and fine, but is an extra 4 gigs really worth all this? (yes)

Hopefully Asus Tech Support will have a fix.


***The 'are we gonna need an intervention here?' Hedge***

:KS

---

### Post by landstander on 2011-04-03
Thanks Hedgehog1, :)

Yes I must admit that I enjoy troubleshooting my own computer. I used to do this for a living but found that working on other peoples computers somehow took all the fun out of it. I think it might have been the time constraints and the bosses always telling me to just replace stuff instead of actually figuring out what the problem was in the first place. etc... Any way.

**Update:**
For whatever reason, FreeDOS does not boot and FreeDOS doesn't have a forum only a mailing list (to which I posted a message). I've recently discovered a bootable CD called "Ultimate Boot CD" or UBCD for short. It actually boots up and I'm able to get a command prompt. However I'm still not able to access the files I need to flash the BIOS from there.... and still no word back from the ASUS support staff.

**Next step:**
I'll try to modify the UBCD iso file to include the files I need in order to flash the BIOS, but I'm not quite sure how to do that and have a bootable iso when I'm done. AcetoneISO is the only program I've found so far in Ubuntu that lets you extract the contents of an iso file, modify it, then write it back to an iso file, but I'm suspecting that the boot sector of the CD might get lost during this process.

I'll keep you posted on my findings and failures as I go.
Again, if anybody has any idea's on how to flash a BIOS that basically doesn't let you use any of its built in flash utilities please feel free to add your idea's tips or suggestions here. :)

**Note:** I think the firmware is AmiBIOS v3.06 but I'm not sure if I'm spelling AmiBIOS correctly since the name is only on the screen for a few seconds during each boot.

Again, thanks for keeping up with this thread. :)

---

### Post by landstander on 2011-04-03
**Update:**
First partial success. :KS

**Preamble:**
Ok, 1st this task was extremely difficult to pull off. ASUS tech support has still not gotten back to me, and I'm not sure what I've done has solved the problem or has updated my BIOS to the newest version or not because I wrote down the version number from the ASUS EZ Flash utility embedded within the BIOS instead of writing down the version/revision number for the BIOS itself. Now that its updated I'm not sure if I've actually updated it or downgraded it.

**Re-Description of the problem:**
The problem I was facing has multiple parts. I will describe these parts in order starting with the main problem, and each successive problem that unfolded from that main problem.
[LIST]
[*]The 64bit OS would freeze up once its memory was upgraded from 4GB to 8GB. Downgrading to 4GB allowed me to start the computer and continue researching a fix for this problem.
[*]After exhaustive testing of the memory chips to make sure they were all in good working condition, it was determined that this might possibly be a BIOS issue. This meant updating the BIOS, however, my particular BIOS would not let me update it via its embedded update utilities which meant using the flash utility provided by the motherboards manufacurer (ASUS). This ASUS BIOS flashing utility was programed to be executed in a DOS environment which leads to the next problem.
[*]How to get access to a DOS environment in Linux (without the use of Microsoft products) when a 1.44MB floppy disk is too small to host the BIOS files necessary to run through the BIOS flashing procedure.
[/LIST]

**Discoveries:**
[LIST]
[*]ASUS has (for whatever reason) made it so that the download links and driver updates for my particular Motherboard no longer exist from the "P5E3 Deluxe WiFi/ap@n" motherboard webpage. When seraching through the ASUS forums I discovered that a few users had started providing links to the updated drivers and download files for my Motherboard right in the ASUS forums.
[*]Some of these updates include, a beta BIOS file, and an updated version of the "BIOS update" section of the motherboard user manual.
[*]According to this new updated section of this Motherboard manual. One of the reasons I might not have been able to get access to the USB flash drive (from the ASUS EZ Flash 2 utility embedded in the BIOS) is that the USB stick that contains the new BIOS update must be the only USB device plugged into the computer and it must be plugged into a very specific USB port in order for the utility to find and discover the USB stick. (I will try this next)
[/LIST]

**Links to discovered files:**
ASUS forum where they talk about the files and updates for the "P5E3 Deluxe WiFi/ap@n" motherboard 
[http://vip.asus.com/forum/view.aspx?board_id=1&model=P5E3+DELUXE%2FWiFi-AP&id=20090315020406924&page=1&SLanguage=en-us]("http://vip.asus.com/forum/view.aspx?board_id=1&model=P5E3+DELUXE%2FWiFi-AP&id=20090315020406924&page=1&SLanguage=en-us")
Note: The above URL, in the BIOS section, contains a broken link to the most up to date beta version of the BIOS. So I'm providing a link to the spot in the forum thread where I found the link to that bleeding edge updated version of the BIOS as well as a direct link to where the file is currently being hosted:
_Forum Thread:_
[http://vip.asus.com/forum/view.aspx?board_id=1&model=P5E3+DELUXE%2FWiFi-AP&id=20100924121701622&page=1&SLanguage=en-us]("http://vip.asus.com/forum/view.aspx?board_id=1&model=P5E3+DELUXE%2FWiFi-AP&id=20100924121701622&page=1&SLanguage=en-us")
_Direct Link to hosted file:_
[http://www.mediafire.com/?3e4h8e7m8jcmky7]("http://www.mediafire.com/?3e4h8e7m8jcmky7")
(Or you can try follow the links at the ASUS website Location : Forum > Motherboard > P5E3 DELUXE/WiFi-AP > Topic : [Sharing]New (custom) Bios)

**How I updated my BIOS:**
Warning: This took a ridiculous amount of research and effort on my part. If your having the same problem, with the same motherboard and OS, but your not comfortable with the command line then you might consider a different approach to solving your problem.
[LIST=1]
[*]I downlaoded the Ultamate Boot CD (UBCD) to a directory on my hard drive. (Note: UBCD is an iso file found here: [Ultamate Boot CD]("http://linuxfreedom.com/ubcd/ubcd503.iso") <--This link was found by clicking on a tiny hard drive icon located at the bottom of this link: [UBCD Website.]("http://www.ultimatebootcd.com/download.html"))
[*]Using AcetoneISO (found in the Ubuntu repositories) I extracted the contents of the UBCD iso file to a directory called "ISO_extracted" (but if your reproducing these steps for yourself it could be a directory of your choice).
[*]I also extracted the boot image from UBCD to the same directory (Note: I'm not sure I needed to do this, but I'll check and report back)
[*] **_WARNING:_** The UBCD website has a section called "customizing UBCD" which is where I figured out how to do most of this, however the website tries to instruct you to create a system of menu's to run your files from inside UBCD. (1st This is dangerous when updating the BIOS and its better to have direct access to the command prompt when using these files. 2nd It is always dangerous to flash your BIOS and you should never do this unless your willing to purchase a new Motherboard if something goes wrong. 3rd I've discovered a method of using UBCD which is much easier than the method described on there website). Just add the two files you need to use to the UBCD root directory (the directory you extracted the iso file to).
[*] I added the 2 files found at the ASUS website to the root of the "ISO_extrated" directory. These files were called "AFU236U.exe, and "P5E3-Deluxe-1415.ROM". where AFU236U.exe is the ASUS BIOS flashing utility and the other file is an older BIOS file. The newest files as of this post is P5E3-Deluxe-1503.ROM and both of these files can be downloaded from one of the ASUS forum links previously mentioned.
[*]After adding the files to the UBCD root directory (the directory you extracted the iso file to). You then use this directory tree to create a new iso file. Since I didn't have any luck making a bootable iso file using AcetoneISO in an earlier attempt I decided to go with a linux version of a utility found in UBCD itself. This utility needed execution privileges before it could be used. So I did the following: 
[LIST]
[*]Open up the Nautilus file browser and go to the "/ISO_extracted/ubcd/tools/linux/ubcd2iso" folder where "ISO_extracted" is the name of the folder where you extracted the files from UBCD.
[*]Right click on the file "ubcd2iso.sh"
[*]Select "Properties" from the bottom of the pop up menu.
[*]Select the "Permissions" at the top middle of the window.
[*]Select the checkbox to the left of the words "Allow executing file as program"
[*]...and lastly select the "close" button at the lower right hand side of the window.
[/LIST]
This gives the file the ability to be executed from the command line.
[*] Then simply run the ubcd2iso.sh file from the command line by giving it the path to your directory tree, followed by the path to where you want the new iso to be created. Example:
Lets say you've extracted your files to /home/user1/ISO_extracted and that you want to use the ubcd2iso.sh script to create a file called "ubcd_custom.iso" in a folder you've created in your $HOME directory called ISO_Disks. (By default Ubuntu comes with the bash scripting engine installed. So to use a script that has the ".sh" extension we use the "bash" command.) We would do this by the following line of code:
```
bash ubcd2iso.sh /home/user1/ISO_extracted /home/user1/ISO_Disks/ubcd-custom.iso

```
[*]Burn this iso file to a new CD or DVD (I used Brasero Disc Burner (also found in the Ubuntu repositories if you don't already have it installed)).
[*]Reboot the computer using this new customized Ultamate Bood CD.
[*]Once your booted into the UBCD's first main menu, select boot to FreeDOS option. (Sorry I'm having to do this part from memory because I don't have those menu's in front of me for reference).
[*] There should be an option from there to View or Browse your files.
[*] From here choose "drpDown" located at the lower right hand side of the screen (it will be listed next to the number 9). This brings up a new menu at the top of the screen.
[*] Select "right" and choose the C:\ drive.
[*] Then quit or exit UBCD, (Again I'm very sorry but I don't have these menu's in front of me so its difficult to remember how I got out of the program to the C: prompt, you'll just have to do like I did and search through as many of the menu options as possible until you find the right one).
[*]Once your at the command prompt the two files you've chosen to download from the ASUS website will be listed by issuing the "dir" command. From here you can update your BIOS by using the 2 files you've downloaded from the ASUS forum links as well as the instructions from the updated version of the BIOS section of the Motherboards Manual (Found in the ASUS forum links at the beginning of this thread).
[/LIST]

**Drawbacks to the above method:**
Every time it is necessary to flash the BIOS (which hopefully isn't that often) using this method would mean it will also be necessary to burn a new Ultimate Boot CD with new BIOS files on it. If the instructions in the new Motherboard manual do the trick and I'm able to flash the BIOS from a USB stick then this entire post will be a mute point.

**Current Status:**
Still testing and working on updating to see if I can get the 8GB to work. I'm actually not that optimistic that the BIOS update will fix this problem, but I did find a bunch of solutions to related problems, so if I do reach a conclusion about this thread, I'm not sure what I should label the thread as... maybe [Sort of solved]? *shrug* I guess I'll just have to cross that bridge when I get there.

Thanks. :D

---

### Post by Hedgehog1 on 2011-04-03
Your bios has been updated (Hurray!).  And here I thought it might **never** really happen! :P

And look Ma! ***Only _92_*** :confused: ***simple steps, too!***

I wonder what the odds are this update will support the 8 gigs?

This is a real page-turner!

***The Hedge***

:KS

---

### Post by landstander on 2011-06-15
Final Update:
After extensive testing and talking with tech support at ASUS, I've come to the conclusion that the memory chips that I have are not supported by ASUS for this specific motherboard, in other words they are incompatible over 4GB but somehow compatible at 4GB and under.

*shrug* makes no sense but there you have it. :?
Sometimes you don't get what you pay for.

So the moral of this story is:
You should always read your motherboards qualified memory vendor list very carefully and only purchase memory sticks that are listed as qualified for the specific configuration your going to be using.

Note: I would mark this thread as solved but that would give the wrong impressions since it is very much unsolved and unsolvable without the purchase of very expensive qualified memory sticks. There is no option to mark this thread as "intractable" or "unsolvable" so I guess I will just have to leave it as is.

---

