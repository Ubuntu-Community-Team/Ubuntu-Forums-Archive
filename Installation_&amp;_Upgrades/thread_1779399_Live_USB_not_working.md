---
title: "Live USB not working"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by gurgsnekr on 2011-06-10
Greetings,

I recently had a problem with the hdd on my netbook.  The hdd died and now I need a new one...it happens.  So, I decided to take a plunge into Ubuntu.  I was able to run the Live USB with Ubuntu 11.04, bypassing the hdd for about a day and this morning it stopped working.  I have tried to reboot using the Live USB and even re-installed the Live USB.  The process to load Ubuntu looks like it is stuck at a screen with the ubuntu logo and 5 dots.  At first, the 5 dots changed color as the program was loading, now the dots do not change.  

Right now, the program does not load up from the Live USB and I am at a loss as to why.  Also, if it is possible to save settings from USB session to USB session, how does one accomplish that?  I am still very new to Ubuntu so I am a little out of my element.  I am trying to install Ubuntu on a HP Mini 210 with 2 GB RAM and a 2 Gb Kingston Datatraveler USB.  Any advice would be greatly appreciated.

Thanks in advance,

gurgsnekr
Pacific
[email]gurgsnekr@gmail.com[/email]

---

### Post by Joe of loath on 2011-06-10
Has the USB stick worked previously? If not, re-download the image and try again. I'd recommend using a torrent or download manager that supports hashes.

If you create the USB stick using the tool on the Ubuntu home page, it should give you 'persistence'. The persistence feature will automatically save your session when you're finished.

---

### Post by gurgsnekr on 2011-06-10
Hi Joe,

Thanks for the reply back.  I am using the same USB stick that I used two days ago and ran off of all day yesterday.  My other USB stick is set up for a clean boot to DOS so I could run diagnostics on the hdd. I re-did the image from Ubuntu site, but still no luck.  Is there a difference between the torrant and what is offered on the Ubuntu home page?

  I am currently scanning the netbook for other potential problems.  So far everything is passing.  I did not see a 'persistence'option for saving settings between usb session to usb session.  After this diagnostic, I am going to attempt to re-run the live usb from a different usb port (4th attempt).  

I had no problems using the live usb yesterday.  In fact, I am 99% convinced that I should switch over to Ubuntu.  Even the live usb was faster than the Windows 7 that was installed on the hard drive.

Thanks
gurgsnekr
Pacific
[email]gurgsnekr@gmail.com[/email]

---

### Post by Joe of loath on 2011-06-10
First off, try a different USB. They're prone to losing their MBR and gods know what else, so the first step is to try another. I have a couple which refuse to boot, but work fine for transferring files etc.

The torrent is automatically checked as it downloads, meaning you're sure to get a good image.

Persistence is enabled automatically, if the tool used to burn the image to the stick supports it. If you save a file, it should be there when you reboot.

---

### Post by gurgsnekr on 2011-06-10
"They're prone to losing their MBR and gods know what else, so the first step is to try another."

I think that I will have to try another USB device. Although, it does seem to be working as a boot until it is part way through the loading process.   Do you know of anyone who has run exclusively from the Live USB or the problems they encountered? Just wondering.

As far as the settings, I used the Universal USB installer linked to from the Ubuntu site.  I guess I will have to look at it closer. :D

Re-downloading the torrant version of the image, and I will be trying again with both USB devices.

or

Would the Live CD work better in my situation?

Again, Thanks!

---

### Post by Joe of loath on 2011-06-10
My dad keeps a USB stick version in his laptop bag, to use with his work laptop (because Vista business is a POS). It works perfectly, although it's recommended not to do updates, since they break it occasionally.

I'd try a live CD too if you can.

---

### Post by gurgsnekr on 2011-06-10
I agree, Vista is a POS.  Windows 7 is much better and more stable, but I am really liking how fast and efficient Ubuntu is from the usb drive.  I can imagine it is faster and more efficient running from the hdd.

My brother uses Ubuntu exclusively from his netbook (run from hdd) and he loves it.  He swears he will never go back to Windows.

These updates you mentioned.  Is this like installing apps for Chromium (couldn't get firefox to work on the live usb) and adobe player, or update to a newer version of Ubuntu?  I ask because I had installed those so I could get back online and get my school work done.  I let it run over night suspended and this morning the whole thing froze up about an hour after waking the netbook up.  Total reboots is less than 10 starting two days ago.  

Of course the USB drive may have had it and I need to switch to another USB drive.  I think I did find the persistence option in the installer.  Didn't pay attention to it the first time through...oops :D  If this still does not work, then I will try the Live CD.

Thanks again!

---

### Post by Joe of loath on 2011-06-10
I mean updates as in security updates/bugfixes. it won't pop up a box like it does when running from hdd, but if you were to run sudo apt-get upgrade from the terminal, you could mess it up. Installing regular programs is fine.

---

### Post by gurgsnekr on 2011-06-10
Ah, thanks!
Re-did the usb stick (same one) with the new installer, and it would not let me run from usb stick (downloaded with the torrent.  Re-did the usb drive with the file from the website and still having the same issue (not loading past Ubuntu screen).  Going to try the other usb stick and if that does not work then I'll try the live cd.

thanks again for your help.

---

### Post by gurgsnekr on 2011-06-10
Ok, 

Second usb stick did not work for both Ubuntu images (from site and from torrent). Both USBs formatted using HP USB Storage Format Tool prior to using the installer.  A second format was performed by the installer to ensure proper FAT. 
Created and attempted to use Live CD (original image from site) without success.  Noted a different start up screen, attempt to load then blank screen 15+ minutes, no activity.  Unknown if video issue was cause.
Out of CDs, unable to attempt with image from torrent.  

I noted a newer usb installer version.  I do not remember the version I originally used to create the Live USB, but I downloaded and created it on the 7th so I assume 1.8.5.2?  The newer version came out on the 8th (noted on the website for the installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")) downloaded and used this today.

I noticed that there is a usb installer in the image from the site that the torrent version does not have.  I could not find any information about the installer on the image.

I know this is an unusual use of the program with my hdd not working but I think this should be able to work.  Especially since I had it working yesterday.  

Thinking:
[LIST=1]
[*]Remove physical hdd (it is not working anyways) and retry Live USB.  HDD might be throwing errors causing problems with Live USB or CD.
[*]Installer/image issue.  Locate previous installer version and retry Live USB.  Delete all images currently used and re-download Ubuntu images
[*]"I got lucky" and it is not supposed to work.  Although I find this option hard to believe.
[/LIST]
After that, I am out of ideas.  

Thoughts anyone?

Thanks in advance,
gurgsnekr
Pacific
[email]gurgsnekr@gmail.com[/email]

---

### Post by Joe of loath on 2011-06-10
Your two options sound plausible, however I have had computers do some very strange things before, without warning. Changing the weirdest thing can sometimes help.

It might be useful to see what kind of errors are coming up; as soon as you see the dots on the screen changing colour, hit the 'up' arrow. You should start to see some of the boot messages appearing. Post anything that looks interesting.

---

### Post by gurgsnekr on 2011-06-10
I did not know about that....Thanks!!  :D

---

### Post by gurgsnekr on 2011-06-10
Just removed hdd and tried the Live CD.  Started loading much faster, then stopped loading.  "UP" arrow revealed log as follows from 9 "*" u:
* Starting save kernal messages
* stopping eCryptfs
* Starting deferred execution scheduler
* Starting configure network device security
* Starting configure network device
* Starting bluetooth
* Starting CPU interrupts balancing daemon
[orange astrick] * PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
* Stopping save kernel messages

On the right hand of the screen from top to bottom is [ OK ]

No activity in 5+ minutes (time it took to type this message plus 3 minutes)

Still waiting on the image for Live USB.  This will be my next attempt

---

### Post by gurgsnekr on 2011-06-10
Finished Live USB with persistence set to 302 MB with following results:
Same message as above only the last two astricks are reversed.  The Stopping save kernel messages and the orange astrick are switched and no [ OK ] after the PulseAudio.  
No further activity 

Ok, I'm out of ideas.
anyone else?

---

### Post by gurgsnekr on 2011-06-10
Ok,

Tried a couple of different ways to run from USB, unfortunately nothing is working for me.  Tried with and without persistence with and without the hdd installed.  At a loss...bummer

gurgsnekr

---

### Post by gurgsnekr on 2011-06-10
Got something happening.

Re-installed the physical hdd. While I was there I cleared the CMOS trying to get to the HP instant Internet program to see if I could bypass everything and go straight to online.  As it was booting, I missed the "press esc to enter SETUP and the thing booted to Ubuntu just fine like it never had a problem.  Not too sure what happened, but I am redoing the Live USB (another stick) and trying with the persistence.  

gurgsnekr

---

### Post by Joe of loath on 2011-06-10
Ah yes, I have had BIOS resets do something, usually a buggy implementation somewhere that causes everything to crash on boot.

---

### Post by gurgsnekr on 2011-06-10
I was thinking something along those lines.  Although I am not sure what is there that would do that.  I know, no software is perfect.

Just finished with the Live USB with persistence set at 303 MB...plugged it in and now it is working.  Maybe clearing the CMOS can help others with similar issues.

Thanks for the assistance and letting me bounce things off of ya.  I can't wait to get my new hdd so I can do a dual boot with windows 7 (still need it for school).

Thanks again,
gurgsnekr

---

### Post by Joe of loath on 2011-06-10
I used to dual boot Windows. Heh. I realised after a couple of months of not using it that, hey, I didn't use it :p Now I dual boot Arch Linux and Ubuntu instead :D

---

### Post by gurgsnekr on 2011-06-26
Just thought I would throw a quick update out there.  Since my hard drive died I have been running my netbook strictly off of a Live USB and an SD card to store files.  This is not a permanent solution, just a limp-along until I get a replacement hard drive.

Running the Live USB does have problems (duh).  After a while it no longer is able to boot or it freezes up while loading the OS.  On several occasions the Live USB will throw errors then freezes as it is loading.  I assume these are the problems everyone talks about when running a Live USB all the time.

I have found some ways of dealing with this and how to keep it somewhat stable, if anyone is interested.

First, when the Live USB does not run properly during boot and OS start up for two or three times in a row, I found recreating the Live USB to be effective.

Second, sometimes clearing the BIOS has proven effective. I had created a Live USB then tried to run with a failed attempt.  I recreated the Live USB with a second failed attempt.  Before the third attempt, I cleared the BIOS then was successful.  This appeared to be helpful on further attempts.  Why this works I am not sure.

Third, after a successful boot and Ubuntu is running Shutting down or restarting seems to have problems.  Suspend does not seem to have too many problems.  

Fourth, keep added programs to a minimum.  I only load what I need.  Chromium, Adobe Flash plugin and plugins to play mp3s in Banshee.  

I am looking into configuring grub to boot to an SD card, but with time constraints that project is on a back burner.  

Hope this helps someone else :D.

---

