---
title: "Windows Installer"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by harlanwolfe on 2010-08-26
I tried using the Windows installer, after not having success burning the ISO to cd, and I received another error message.
"There is no disk in the drive. Please insert a disk into drive.
\Device\Harddisk3\DR3"

What now?

---

### Post by sikander3786 on 2010-08-26
Couldn't actually understand the problem. Please explain a bit more.

---

### Post by tejashs on 2010-08-26
may be the iso image is corrupted.

---

### Post by harlanwolfe on 2010-08-26
Thanks for your help. This is what happened when I tried using the windows installer.
[IMG]http://www.box.net/shared/static/vc908ta05c.jpg[/IMG]
Am I supposed to setup & format a partition before using it?

I tried this after wasting a half dozen CDs trying to burn the iso with Infrarecorder. Also tried the download from the main page, as well as a couple of the mirror sites, and kept getting the same error message when verifying "Could not read file".

---

### Post by harlanwolfe on 2010-08-26
Also, I couldn't cancel this operation, had to shut down the computer to remove this screen from my desktop..
Can anyone confirm that the pyrun.exe is the legit file for the wubi installer?

---

### Post by harlanwolfe on 2010-08-26
Sorry to ramble...I'm using Windows Vista with Service Pack, have excellent memory & hard disk capacity. No other problems with CD burner or hard disk. I searched the forums for these particular issues, but couldn't locate relevant answers.
I appreciate the assistance. I've had it up to here with Windows after 10 years of headaches. Thinking of going to Mac, thought Ubuntu looked even more promising.

---

### Post by Maverick_Meerkat on 2010-08-26
I was unable to install from the live CD. I ran WUBI and the ISO directly from my HDD. Additionally, I had to use the esc key to boot into safe graphics mode to complete the install. After that, everything booted normally and worked flawlessly. Except of course for the sleep/suspend/resume... which seems to be a problem on many laptops.

---

### Post by arubislander on 2010-08-26
pyrun.exe seems to be legit. What version are you trying to install? There have been bug reports on 9.04

---

### Post by arubislander on 2010-08-26
So you're set now?

---

### Post by harlanwolfe on 2010-08-26
Got it to start installing, missed this thread. Keep you posted.

I had this same issue and got it resolved following this thread:
[http://ubuntuforums.org/showthread.php?p=8208814](http://ubuntuforums.org/showthread.php?p=8208814)

Which basically just says to disconnect external drives / devices (in my case was an ipod and android phone).

---

### Post by harlanwolfe on 2010-08-26
All is running fine now, an thanks to all. I really like the ease of switching between OS to use particular programs. The one thing is I haven't figured out how to install Flash. Do I need to download software to open the Linux file options, and which should I use for this version of Ubuntu 10?

---

### Post by arubislander on 2010-08-27
```
~$ sudo apt-get install ubuntu-restricted-extras
```

Should install flash and a few other stuff that's handy to have around.

---

### Post by harlanwolfe on 2010-08-27
Where do I install that code? Total Ubu newbie here!

---

### Post by harlanwolfe on 2010-08-27
Almost added the Firefox plug-in, but dont have the Ubuntu CD, so it wasn't able to finish installing.

---

### Post by harlanwolfe on 2010-08-27
The terminal, thanks, getting the hang of it. Worked fine, but apparently needs the CD to finish as well?

---

### Post by bcbc on 2010-08-27
If you're getting errors about needing the CD, then likely it's set in your software sources. 
Click on: System, Administration, Software Sources.
Look at the bottom where it has the CD and uncheck the box. Then it will reload the software sources upon exit and shouldn't prompt you for it again.

---

### Post by harlanwolfe on 2010-08-28
Unchecked the CD box in software source, and that appeared to result in a successful installation. I still can't view any online video. Also installed other flash-alike players with no luck.

What else do I need to view flash and online videos?

---

### Post by bcbc on 2010-08-28
Are you running 32bit or 64bit ubuntu? I understand the 64bit has some issues with flash. 32bit is recommended for normal desktop use.

As far as I know, installing restricted extras enables flash.

But anyway - I just chimed in because I recognized that CD error. So hopefully someone else knows more about flash.

---

### Post by harlanwolfe on 2010-08-28
I appreciate the help! The only place that I can see is that AMD 64 it refers to as my computer, which is a 32 bit. I didn't see that I had a choice...did the installer mis-recognize mt system, or how can I fix this? I think I may just re-install.

---

### Post by bcbc on 2010-08-28
> **harlanwolfe said:**
> I appreciate the help! The only place that I can see is that AMD 64 it refers to as my computer, which is a 32 bit. I didn't see that I had a choice...did the installer mis-recognize mt system, or how can I fix this? I think I may just re-install.

If you reinstall make sure it's the 32 bit version - wubi automatically chooses amd64 if it detects a 64 bit processor. You can download the 32bit .iso and place it in the same folder as wubi.exe and it will use it instead.

---

### Post by harlanwolfe on 2010-08-29
Thanks! Great success in writing to disc & installing using 32 bit downloader, all features are installed or available.
I appreciate all the assistance. So far, the only reason I need to switch back to Windows is a USPS Shipping Assistant, but I can workaround that.

---

