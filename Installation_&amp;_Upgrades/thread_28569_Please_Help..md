---
title: "Please Help."
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by soham369 on 2005-04-20
Hi, I have 2 computers.  One is a Gateway and the other is a Dell.  My Dell is an OptiPlex100 with Windows NT 4.0, 63MB RAM, 566MHz Intel Celeron.   You and I will reference them with their proper manufacturer.  I downloaded "ubuntu-5.04-install-i386.iso" on my Gateway so I can get it on my Dell.  I then opened Nero Express, clicked the bottom option (Burn Image or something like it).  I then burned "ubuntu-5.04-install-i386.iso" onto a blank CD-R successfully.  After that, I placed the CD-R in my Dell and booted it up.  For some reason, Ubuntu did not boot nor its installation.  Yes, my Dell's boot sequence is set to  "IDE CD-ROM Device" first, and then second is "Hard-disk Drive C:".  Please tell me how to solve the problem(s) or any ALTERNATIVE WAYS to boot Ubuntu on my Dell.  Thank you very very much.

---

### Post by nad on 2005-04-20
Open the cd on the Gateway computer to confirm that you burned an image of the iso file and didn't just copy the file. If this is not the problem, you will need to confirm whether the file you have is good by comparing the checksum with the known value. Finally, it is usually judicious to burn a large iso image at less than the full rated speed of the hardware to reduce the possibility of errors.

Please let us know of your results.

Dan M

---

### Post by soham369 on 2005-04-20
I have done all that stuff before.  What must I do *now* ?

---

### Post by gunnyman on 2005-04-20
does the cd boot in the gateway?

---

### Post by MajorNewby on 2005-04-20
Sounds to me like you burned it as a file, rather than as an .iso image.

In Nero, you need to make sure you're choose "burn cd image" as your selection for what you want to do.  I did the same thing with another distro when I first started messing around with linux about 2 years ago - (and it took me 2 years to finally find one I'm comfortable with - thank you Ubuntu Developers!!)  \\:D/

---

### Post by NaplesBill on 2005-04-20
Considering the specs you gave for the Dell it sounds fairly old.  If it still has the original cd-rom drive then it's very possible that the cd you burned can't be recognized by it.  Many older cd-rom drives cannot read multisession cds.  Try burning the cd in DAO mode.  This will prevent it from being written as a multisession.  Of course, if it doesn't boot on the Gateway either then ignore this post.

---

### Post by soham369 on 2005-04-21
MESSAGE FOR EVERYONE IN THE WORLD:    Do you think WinRAR, the program, is interfering my burning an .iso?  I have thought about this and I have not got an answer from myself, so I am asking all of you.

gunnyman:  See, I do not want to risk the installation of linux whatsoever on my Gateway because I do not want to screw it up.  My hard-drive has been filled with 30.8 GB and has 6.37 GB remaining.  It is the only "good" computer I have.  Thus, I have not attempted to boot the CD in the Gateway.

MajorNewby:  I have burned the .iso, which has an icon as a RARarchive.  Within this RARarchive, there are many files and folders.  How do I know this?  I have "read" the burned CD by going onto my Dell and clicking "Explore" from the right-click menu of "E:" in "My Computer".  I could even send you (by e-mail of course), if you want me to, screen shots of me burning the .iso and the screenshots of the actual .iso (a RARarchive).

I opened Nero Express and selected "Disc Image or Saved Project" under the category, "What would you like to burn?"  Tell more about "Distro" in an e-mail at [email]soham.gandhi@gmail.com[/email].  

NaplesBill:  I do not think it matters because the CD-ROM drive worked absolutely fine when I installed my Mathematica V3.0 onto it.  I do not remember if I had done a Disk-At-Once.  I will look into that soon.  I have a Biology lab to finish up.  I am a busy sophomore in high school, guys!  What is the difference between single-session and multi-session CDs?

---

### Post by nad on 2005-04-21
You have not burned the image file. As I recall from using the nero software on a customers pc, the process to burn an image file is counter-intuitive. You do not use the menus, but just choose the file and write to disc. The fact that you see an _archive_ on the cd confirms this. If you had burned the image you would see an unarchived file system.

I am sorry if am unclear. The iso image file contains instructions within that when processed will use the included archive to create a filesystem on the output device.

Dan M

---

### Post by soham369 on 2005-04-21
Dan M,

 	Actually, I definitely have burned the image file.  I simply selected the .iso after I selected the Image burn option.  Many people whom I have asked have told me that same method; however, you are the very first to oppose me by saying the process is not how you think it would be.  What is this "_archive_" you are talking about?  I have no clue about that one, Dan.   Now that does not mean that it is now obvious that there is no "_archive_" located on the CD.  First, explain to me what it is.  Then, I will search for it.  I had burned the image.  I also explored "E:" in "My Computer" and saw many files and folders on that CD-R.  Obviously, it became automatically "unrared", if you will.  But, what is an "unarchived file system"?

It is fine if you are unclear.  I will try my very best to express the specifics in my situation as needed.  Everyone only has to ask me what information they need, and I will be glad to tell.  

> The iso image file contains instructions within that when processed will use the included archive to create a filesystem on the output device. 
I know, however, it is just not working for me.   :mad: 

Thanks for your time,
Soham Gandhi

---

### Post by gunnyman on 2005-04-21
You can put the cd in the gateway just to see if it boots, nothing gets installed until you tell it to.

---

### Post by MajorNewby on 2005-04-21
hrm, I'm perplexed... from your last 2 posts, I'm sure that you burned the .iso image as you should have - meaning it was burned in the proper format, etc.  I can't really understand why it wouldn't work for your computer, unless it's too old... but I don't think it's the reason.  Sure, it's not exactly the latest technology, but I'm sure I've read posts in here from other people running on systems older/slower than yours.

You asked what about the distros I have tried in the past... well, there were only a few of them.  I spent about 1 1/2 years (on and off) trying to get Gentoo running on my system, figuring the best way to learn Linux was to build it and compile it from scratch... while I learned quite a bit in the numerous times I started from Step 1, I never had a usuable system.  I've also tried Slackware and RedHat... however, I had some difficulty with the installation and, after getting rather frustrated, I decided to try Gentoo again.  I got it installed and running, then followed the Guide for updating some of my packages and ended with a Gentoo system that was totally b0rked and wouldn't boot.

That certainly didn't help my frustration.... however, I was so angry about not having a stable running linux system, I got on Google and typed in "easy install linux" and came across Ubuntu - now the only things I have to worry about are the same things others users moving from Windows to Linux worry about... adapting to the system, figuring how to make our games run correctly and the little things we take for granted from the bloated Windows platform... once I get these things worked out, I will probably move over to Ubuntu for all but the latest games that don't have the linux binaries available...

---

### Post by nad on 2005-04-21
From the RARLAB website:

>WinRAR 

>Knowledge Base > General 	 

>How to handle RAR files?


>WinRAR provides the complete support for RAR files, so you may both create and unpack them.

>If you installed WinRAR on your computer and downloaded RAR file from Internet, you may double click on RAR file icon to open it in WinRAR, select all files, press "Extract To" button, enter a destination path and press "OK".

>Another way is to click on the RAR file in Explorer using the right mouse button. If you enabled "Shell integration" option when installing WinRAR, the file context menu will contain "Extract to ..." item.

I may be mistaken, but I still think this may be what is happening. When you right click, winrar is transparently showing you the contents of the iso on the cd. What is the result if you right click E: and choose the Properties tab? How many files are on the cd?

Dan M

---

### Post by soham369 on 2005-04-21
You absolutely, positively, definitely sure about doing that?  I want to make sure, man.  This is my only computer that is good and my dad does not want to buy a new one yet, although, I do have $600 in my wallet.

---

### Post by gunnyman on 2005-04-21
you will boot to the install program
just  power the pc off once you see the cd boots.

---

### Post by clb137 on 2005-04-22
HI,

What speed are you trying to bhurn your ISO Image at?  Often it is best to lower your speed to x8.  I have had problem buring at higher speeds, once lowered it boot ok.  Can you try the disk you have burned on a friends PC? Or get ome else to burn for you?

Clinton

---

### Post by patrac on 2005-04-22
Read this guide on how to boot from floppies if you can't boot the CD. This requiers that you have a network connection.
[http://www.ubuntulinux.org/wiki/InstallWithFloppiesHowto](http://www.ubuntulinux.org/wiki/InstallWithFloppiesHowto)

---

### Post by soham369 on 2005-04-22
gunnyman:  Ok, I am going to try booting the CD-R onto this computer (the Gateway).  Thanks.

clb137:  Hi Clinton,
I am burning my .iso image at 8x (1200 kb/sec or whatever).  What do you mean by, "Can you try the disk you have burned on a friends PC?"  I have this friend who knows how to burn Mandrake and boot it.  I will talk to him soon.

patrac:  	I do not have a network connection.  Sorry for your trouble.   :|

---

### Post by clb137 on 2005-04-22
[QUOTE=soham369]gunnyman:  Ok, I am going to try booting the CD-R onto this computer (the Gateway).  Thanks.

clb137:  Hi Clinton,
I am burning my .iso image at 8x (1200 kb/sec or whatever).  What do you mean by, "Can you try the disk you have burned on a friends PC?"  I have this friend who knows how to burn Mandrake and boot it.  I will talk to him soon.

patrac:  	I do not have a network connection.  Sorry for your trouble.   :|[/QUOTE]


Do you have a friend who has a PC that you can try the disk in?  If not try to down load the LIVE version,  that way you do not need to install it on a pc, but it will prove if you cd buring is good..  Does NERO do a checksum check to ensure that the download is sound?

clinton

---

### Post by soham369 on 2005-04-22
Hi Clinton,
No, I do not have a friend that has a PC that I can try to boot the CD-R.  Please give me the URL where to download the LIVE version!  Nero, itself, does not do a checksum check to ensure that the download is sound; however, I have a program that does so:  md5.exe.  Please give me the link to download the LIVE version!  Thanks.

---

### Post by clb137 on 2005-04-22
[QUOTE=soham369]Hi Clinton,
No, I do not have a friend that has a PC that I can try to boot the CD-R.  Please give me the URL where to download the LIVE version!  Nero, itself, does not do a checksum check to ensure that the download is sound; however, I have a program that does so:  md5.exe.  Please give me the link to download the LIVE version!  Thanks.[/QUOTE]


hi there

try this link and scroll down for the live version  

[http://se.releases.ubuntu.com/5.04/](http://se.releases.ubuntu.com/5.04/)


clinton

---

### Post by clb137 on 2005-04-22
[QUOTE=clb137]hi there

try this link and scroll down for the live version  

[http://se.releases.ubuntu.com/5.04/](http://se.releases.ubuntu.com/5.04/)


clinton[/QUOTE]


i will be back in the moring if you are still having problems please feel free to mail me direct I will help you as much as I can.  I know what it is like to start out we have all been ther but stick with ot the rewards are fantastic


clinotn

---

### Post by soham369 on 2005-04-22
Eureka!  Just one major problem:  after everything was "installed", there was something with "error" instead of an "ok" in red.  After that, there would be a brown screen and a small mouse pointer.  My CD-R would still be spinning and nothing new would appear on the screen.  I think there is something wrong, guys.  :roll:

---

### Post by clb137 on 2005-04-23
[QUOTE=soham369]Eureka!  Just one major problem:  after everything was "installed", there was something with "error" instead "ok" in red.  After that, there would be a brown screen and a small mouse pointer.  My CD-R would still be spinning and nothing new would appear on the screen.  I think there is something wrong, guys.  :roll:[/QUOTE]


hi,


try to read the error and report back

ty

clinton

---

### Post by soham369 on 2005-04-23
Hi Clinton,

The error reads exactly as the following:

[COLOR=Red]*[/COLOR]ror    :  Temporary failure in name resolution         [[COLOR=Red]fail[/COLOR]]

---

### Post by clb137 on 2005-04-23
[QUOTE=soham369]Hi Clinton,

The error reads exactly as the following:

[COLOR=Red]*[/COLOR]ror    :  Temporary failure in name resolution         [[COLOR=Red]fail[/COLOR]][/QUOTE]


Soham 

Can you get anythig to boot? If so are they any errors during the boot process?

---

### Post by clb137 on 2005-04-23
it sounds like the name problem is with a server that you do not need to be runing possilbe 'Apache'

---

### Post by soham369 on 2005-04-23
The only 2 problems I have are that error and when everything is done doing its thing, there is this brown screen with a mouse pointer, which I can move around.  That brown screen does not change whatsoever.  My CD-ROM drive keeps reading the CD-R constantly.  It keeps making squeaking noises.  This is how I know.  There are no other problems nor errors.

---

### Post by soham369 on 2005-04-27
Is anybody willing to help me or what?

---

### Post by tread on 2005-04-27
I'm reading this thread a bit late, but here goes anyway.
1. Burn the install iso to a cd. (Reading your posts, you seem to have done this the right way)
2. Pop it in the drive of the Gateway (thats the one you dont want to touch right?) If the cd starts booting, then we know the cd is ok. Dont worry, you can turn the computer off without damaging anything the minute you come to the prompt which asks what you want to install.
3. If step 2 works, then try again in the Dell.
4. The Live cd seems to be running into trouble with some network stuff .. Are you connected over a wirless or a wired lan? Wireless may have trouble on the live cd if the correct drivers arent present and if some network services are on. Even then, it should eventually time out and give you control .. though that may take time.
5. Excessive cd accesses are normal on the live cd.

---

### Post by soham369 on 2005-04-28
I am not connected through LAN whatsoever.  That computer sucks so much that it's not worth LANing to.  Anyways, I'll do your steps tomorrow.  I wanna get sleep because it's 11:00 p.m.  Thanks for your help, tread.  Good night.

---

### Post by hambone on 2005-05-05
Gateway E-1800, Intel Celeron 1.2Ghz, 512MB memory
40GB WD HDD, Memorex DVD+/-RW optical, Memorex 52Max CD/RW optical(boot)
PCI VisionTek Xtasy Nvidea GeForce2 MX/MX 400 graphics card (on board video disabled)
PCI Belkin USB 2.0 card
PCI 10/100 Ethernet card for DSL, no local network,no modem (no more PCI slots)
USB soundblaster device (onboard sound disabled)
USB HP psc 1350 all-in-one printer
USB San Disk Image Mate memory stick RW
Microtek 710S 17" LCD display

Talk about newbeeeees.  I first became aware of Linux only a week ago while looking for an alternative to MS XP.  Days of searching Google led me to this discussion after repeated failed attempts to load live Ubuntu from CD.  (I used Isorecorder V2 to copy the download to a CDr and it does boot, but I didn't retry the download, as it takes over an hour, even on DSL.) 

The problem I am having with the install is the same as the described failure in this thread.  The default installation makes it to the boot screen and displays as follows:

Starting Ubuntu...                                                          
* version 2.86 booting                                                      
* Mounting a tmpfs over /dev...                                       [ ok ]
* Creating initial device modes...                                    [ ok ]
* Setting disc parameters...                                          [ ok ]
* Setting the System Clock using the Hardware Clock as reference…     [ ok ]
* Cleaning up ifupdown…                                               [ ok ]
* Calculating module dependencies…                                    [ ok ]
* Loading modules…                                                    [ ok ]
* Creating device-mapper devices…                                     [ ok ]
* Starting RAID devices…                                              [ ok ]
* Setting up LUM Volume Groups…                                       [ ok ]
* Starting Enterprise Volume Management System…                       [ ok ]
* Checking all file systems…				              [ ok ]
* Mounting local filesystems…                                               
tmpfs on/tmp type tmpfs (rw,nosuid,nodev)                                   
* Running 0dns-down to make sure resolv.conf is ok…                   [ ok ]
* Initializing ifupdown state…                                              
* /dev/shm/network/…                                                  [ ok ]
* Reading desktop files…                                              [ ok ]
* Starting hotplug subsystem…                                         [ ok ]
* Configuring network interfaces…                                     [ ok ]
* Setting up general console font…                                          
* Setting the System Clock using the Hardware Clock as reference…     [ ok ]
* Synchronizing clock to ntp.ubuntulinux.org…                               
[COLOR=Red]*[/COLOR]ror : Temporary failure in name resolution                           [[COLOR=Red]fail[/COLOR]]
* Initializing random number generator…                               [ ok ]
* Setting up X server socket directory…                               [ ok ]
* Setting up ICE socket directory…                                    [ ok ]
* Entering runlevel: 2                                                      
* Starting system log daemon…                                         [ ok ]
* Starting kernel log daemon…                                         [ ok ]
* Setting up ALSA…                                                          
* Starting GNOME Display Manager…                                           
* Starting Common Unix Printing System: cupsd                         [ ok ]
                                                                            
After a less-than-a-second pause, the screen blanks and then displays a static and unmoveable cursor, top left corner.  Waiting 30 minutes did not produce a timeout.  The system was locked tight with no keyboard function and the CD went on spinning.  Pressed and Held the power button for 8 seconds to shut down.

I tried the boot-up several times and removed various hardware (printer, card reader).  I have been watching this thread anticipating a resolution.  I am not a programmer and was hoping to just run the CD and start the Linux experience.  The attraction of Ubuntu is the live CD.  I am anxious to see what I have been missing without risking my existing OS.  Any help would be appreciated. :-? 

Thank you.  *M*  


BTW  I used my digital camera to capture the boot screen.  It went by too fast for me to read it.

---

