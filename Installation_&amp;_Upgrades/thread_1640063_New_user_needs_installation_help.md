---
title: "New user needs installation help"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by cricketeer on 2010-12-07
[COLOR=black][FONT=Verdana]I am a new user trying to install Ubuntu for the first time.  I have a multicore 64-bit Dell Precision T7500 with a solid state SCSI drive and a traditional SCSI drive.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR][COLOR=black][FONT=Verdana]After downloading and burning the LiveCD for Ubuntu 10.10 from a 64-bit machine (apparently the images don’t burn properly from a 32-bit machine), I was able to boot to the LiveCD.  So, I installed Ubuntu 10.10.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]During installation Ubuntu asked which drive to install to.  The default was the traditional motorized SCSI drive even though the first drive (A) was the solid state drive.  This installation failed upon reboot.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then started over and installed on the traditional motorized SCSI drive (as that was the default in the installation process).  This installation moved further along than the previous attempt, but ultimately failed as well.  Upon rebooting after installation I got to the standard boot screen (the one listing all the OS’s – Ubuntu, Ubuntu Recovery Mode, etc.) and selected Ubuntu before the screen flashed quickly (I think it may have shown the Ubuntu logo) and going to sleep.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I subsequently tried to boot into Ubuntu Recovery Mode, but that didn't work either.  A lot of text scrolled by on the screen before the screen went black.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Does anyone have any idea of what's going on and/or how to fix it?  Is there additional information that I can give that would be helpful?[/FONT][/COLOR]

---

### Post by searchfgold6789 on 2010-12-07
To help you completely, we need to know the exact error messages, or at least a description of them. Maybe you could try installing Ubuntu again, this time taking a screenshot of the error if it occurs again.

Installation problems are prevented by:

[LIST]
[*]Burning the CD at the lowest speed possible (Trust me, this works!)
[*]Verifying the downloaded file by either using bittorrent to download peer to peer; or using an [_**MD5 checksum**_]("http://lifehacker.com/247262/how-to-use-md5-sums-to-verify-downloaded-files").
[*]Testing your memory with memtest86+ (usually more helpful with desktops, but give it a try :p) and seeing if memory errors are preventing you from installing ubuntu.
[*]Making sure that Ubuntu can be installed on your computer with a quick google search.
[/LIST]
Post back what the error message is, most likely I/we will be able to help you further.

---

### Post by Quackers on 2010-12-07
When in the grub menu, make sure your chosen OS is highlighted then press the "e" key. A new screen will appear. In this screen using the down and right arrows (or end key) navigate the cursor to the end of the line that says "quiet splash". Then delete "quiet splash" and replace it with "nomodeset" - without the quotes! Then press ctrl + X to reboot. Hopefully after lots of screen messages the desktop will arrive.
When it does and after connecting to the internet if you go to System menu > Admin > Hardware drivers (or Additional drivers) and run that you may find a driver available for your graphics card. Install that and reboot then hopefully your shiny new desktop will appear without having to use nomodeset :-)

---

### Post by cricketeer on 2010-12-07
Quackers you are my new favorite person!  I don't know what "nomodeset" does, but it got me to the desktop!  I'm downloading drivers/updates right now, I'll update if all goes well (and especially if it doesn't go well).  
 
searchforgold - can you tell me more about memtest86+?  What does it do and how do I know what the results are?  I do think there is something screwy going on with memory but I had assumed that it was separate from my installation issues.  In particular one of my dimms seems to go in and out.  On some (but not all) attempts to boot it warns me that memory has changed.

---

### Post by Quackers on 2010-12-07
Excellent! :-) We like happy endings!

---

### Post by cricketeer on 2010-12-07
A happy ending indeed...I rebooted and it looks to work fine!  Thanks so much!!

---

### Post by Quackers on 2010-12-07
Very nice :-)
If you are happy, please mark the thread as solved, using the Thread Tools near the top of the page.

BTW if you select Memtest from the grub menu it will run a test on your ram and, I suppose, will report any errors. I think, though, it will run forever if you let it! Not too sure about that though. Do a Google search and see what comes up.

---

