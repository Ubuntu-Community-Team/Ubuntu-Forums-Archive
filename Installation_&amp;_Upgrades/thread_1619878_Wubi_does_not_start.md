---
title: "Wubi does not start"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by j-prause on 2010-11-12
After clicking on wubi.exe nothing happens.
Wubi does not start at all.
Windows XP, SP3.

---

### Post by bcbc on 2010-11-12
did you download it from here? [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by j-prause on 2010-11-12
Yes, I did.

---

### Post by bcbc on 2010-11-12
Make sure you're running as an administrator. If nothing happens you might have an antivirus program preventing you from running it. This is just a guess. Check in the %temp% directory for a file wubi-10.04.1-rev190.log (maybe it is running but stops for a reason).

What version of Ubuntu do you want to install? The one at that site is 10.04.1 still. The 10.10 version can be taken from a download mirror e.g. [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/)

---

### Post by j-prause on 2010-11-12
I am running as administrator.
There is no log in temp.
I downloaded Ubuntu 10.10 from [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download") and wubi.exe from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer").
I believe this an official site.

---

### Post by bcbc on 2010-11-12
> **j-prause said:**
> I am running as administrator.
There is no log in temp.
I downloaded Ubuntu 10.10 from [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download") and wubi.exe from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer").
I believe this an official site.
The wubi.exe at the official site is for release 10.04.1 and will only install the same release - it will ignore the 10.10 image and try to download a new version.

If you burn that 10.10 image to disk you can run it from there or mount it and copy the wubi.exe off it. (It has the correct wubi.exe within the 10.10 image itself)

---

### Post by j-prause on 2010-11-14
> If you burn that 10.10 image to disk you can run it from there or mount it and copy the wubi.exe off it. (It has the correct wubi.exe within the 10.10 image itself)
And this version wubi.exe just does not work. !!!
It's rather annoying.

---

### Post by newscollection on 2010-11-19
> **j-prause said:**
> And this version wubi.exe just does not work. !!!
It's rather annoying.

I understand your frustration since I experience exactly the same issue ;). Used Ubuntu before on separate partitions which worked well but wanted to try the WUBI feature this time. 

It seems that all Versions up to 8.X work fine, but after 9.X (the ones with the new icon) not even the GUI starts (no logfiles are created etc.). It does not help to temporarily deactivate firewall and/or virus scanner.

xp pro, service pack 3

any ideas?

ta,
stefan

---

### Post by bcbc on 2010-11-19
> **newscollection said:**
> I understand your frustration since I experience exactly the same issue ;). Used Ubuntu before on separate partitions which worked well but wanted to try the WUBI feature this time. 

It seems that all Versions up to 8.X work fine, but after 9.X (the ones with the new icon) not even the GUI starts (no logfiles are created etc.). It does not help to temporarily deactivate firewall and/or virus scanner.

xp pro, service pack 3

any ideas?

ta,
stefan
I have xp professional, service pack 3. It works for me - I've tried 9.04, 9.10, 10.04, 10.04.1, 10.10.

So I would guess that your antivirus isn't as disabled as you think it is. Otherwise I can't explain it.

---

### Post by newscollection on 2010-11-20
> **bcbc said:**
> I have xp professional, service pack 3. It works for me - I've tried 9.04, 9.10, 10.04, 10.04.1, 10.10.

So I would guess that your antivirus isn't as disabled as you think it is. Otherwise I can't explain it.

Mhm, quite sure that is not the case. I have Antivir Personal and deactivated the Antivir Guard (Realtim Scan) and even tried it when killing all associated processes. 

Maybe it helps to be more precise: It seems that the wubi.exe starts alright and it creates some other file in my %temp% directory (plyXX.tmp.exe) but that seems to be just about it and nothing more happens. I cannot start the newly created .exe because this will cause a crash.

It is also not a problem with the CD because when I download any of the WUBI files 9.X or above it just does not work anymore. Again, with 8.X it worked (even with antivirus and firewall active) so there must be some sort of change in the setup which causes this :).

Thanks for your quick reply though. 

Any other suggestions?
Stefan

---

### Post by Frogs Hair on 2010-11-20
My Wubi experience is with Win 7 . I have installed 9.10 , 10.04 , and 10.10 for others. When installing on Win 7 Wubi  automatically requests that you disable the firewall prior to download , but this is after the program is open. I don't know if the same message appears in XP.

---

### Post by bcbc on 2010-11-20
> **newscollection said:**
> Mhm, quite sure that is not the case. I have Antivir Personal and deactivated the Antivir Guard (Realtim Scan) and even tried it when killing all associated processes. 

Maybe it helps to be more precise: It seems that the wubi.exe starts alright and it creates some other file in my %temp% directory (plyXX.tmp.exe) but that seems to be just about it and nothing more happens. I cannot start the newly created .exe because this will cause a crash.

It is also not a problem with the CD because when I download any of the WUBI files 9.X or above it just does not work anymore. Again, with 8.X it worked (even with antivirus and firewall active) so there must be some sort of change in the setup which causes this :).

Thanks for your quick reply though. 

Any other suggestions?
Stefan

I'm scratching my head :)

Wubi uses python (2.3) - if you look in the %temp% directory you should see a subdirectory py???.tmp containing the python23.dll. This is required to run wubi so if it's not there, that could be the reason. But what would be causing the problem - no clue!

---

### Post by newscollection on 2010-11-20
> **bcbc said:**
> I'm scratching my head :)

Wubi uses python (2.3) - if you look in the %temp% directory you should see a subdirectory py???.tmp containing the python23.dll. This is required to run wubi so if it's not there, that could be the reason. But what would be causing the problem - no clue!

You gave me just the hint I needed! 

It seems there was an old py??.tmp directory which somehow obstructed the installation. After removing it wubi  (created a new py??.tmp directory, py??.tmp.exe and ??.log file as well and) installed correctly.

So if anybody else experiences this issue:

1.) Click on Start - Run
2.) Enter %temp%
3.) Check whether there are any files and folders starting with py and delete them
4.) Start WUBI again 

Hope that helps - Thanks for your support!
Stefan

---

### Post by bcbc on 2010-11-20
> **newscollection said:**
> You gave me just the hint I needed! 

It seems there was an old py??.tmp directory which somehow obstructed the installation. After removing it wubi  (created a new py??.tmp directory, py??.tmp.exe and ??.log file as well and) installed correctly.

So if anybody else experiences this issue:

1.) Click on Start - Run
2.) Enter %temp%
3.) Check whether there are any files and folders starting with py and delete them
4.) Start WUBI again 

Hope that helps - Thanks for your support!
Stefan

That's a strange one! Well done for figuring it out. Maybe you should create a bug on launchpad for it as well. I don't suppose you recall what was in those folders? A different python dll perhaps?

---

### Post by newscollection on 2010-11-22
> **bcbc said:**
> That's a strange one! Well done for figuring it out. Maybe you should create a bug on launchpad for it as well. I don't suppose you recall what was in those folders? A different python dll perhaps?

It really is a strange one - I am not able to reproduce this problem. I believe the name of the .dll file was correct, although I only had a quick look at the contents before removing it.

The computer had a pretty fresh install of windows xp. I know that I first started a 10.04 CD and my firewall asked whether I wanted to allow wubi to start temporary .exe file. After I confirmed nothing else happened. From that point onwards all wubi installers from 9.x upwards refused to work.

Now every time an installer quits it removes the .tmp folder. Even if I copy it before and rename it after quitting (to simulate some sort of process failure) it does not have an effect because every new start of the installer creates all necessary files and folders separately.

No clue what really happened before. Many thanks. Since it works now I even have the chance to have a look at the windows partition install feature :),
Stefan

---

### Post by fuzzyangel on 2011-10-30
I had the same problem.
After reading this thread, I changed the TEMP and TMP folder position* because I could not delete ever py* folder in  C:\Documents and Settings\user\Local Settings\Temp. 

Well after that I am downloading 11.10 version through WUBI now.        
:D

____
* my computer -> right click ->properties -> advanced -> environment variables

---

### Post by Rubi1200 on 2011-10-31
Thread closed.

Reason: necromancy.

---

