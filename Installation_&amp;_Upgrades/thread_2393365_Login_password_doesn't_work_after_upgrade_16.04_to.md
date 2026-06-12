---
title: "Login password doesn't work after upgrade 16.04 to 17.??"
date: 2018-06-02
forum: Installation &amp; Upgrades
---

### Post by johnfrith1 on 2018-06-02
Grateful for any help.

I upgraded my laptop online from 16.04 to 17.?? (can't remember which). Download went smoothly until the reboot. The first problem was that I had left the laptop connected to a screen on my desk, along with a USB keyboard, and neither keyboard would work, and I need to enter the login password. Fortunately I could move the cursor so I managed to load the on-screen keyboard. But the second problem is that it does not recognise the password and gives message "Sorry that didn't work. Please try again". The pre-upgraded system was a dual boot, so I wonder if the default boot login has changed, and try the alternate password, but that doesn't work either. I have tried re-entering both passwords several times and am confident I'm entering correctly.

I haven't rebooted in case it screws up the upgrade. Can anyone advise?

---

### Post by TheFu on 2018-06-02
Sorry, I can't help with the password issue. I've never seen that.  A few questions that might help someone else are:
* is there any encryption involved?  If so, which type?
* the output from **sudo fdisk -l** would probably be helpful.
* which language and keyboard are being used?  Different international keyboards might send different keycodes, I'm guessing. Did the keyboard selected during the install change?

Ubuntu Support stuff
I wouldn't spend any time on 17.xx.  Support for 17.04 ended 5 months ago and support for 17.10 ends next month.  16.04 is an LTS and has either 5 yrs or 3 yrs of support depending on the flavor.   18.04 is LTS too and has 5 or 3 yrs of support, similarly.  A basic understanding about Ubuntu Release support can prevent wasted effort.
But maybe there is a very good reason you needed 17.xx? Please explain.

Heck, I just moved to 16.04 from 14.04 last Feb.  I'm an LTS-only guy.  Running a supported distro is important.

Another option is to make a backup of all your data and the installed programs (a list is fine), then perform a fresh install.  Most people have things about their installs that need to be addressed, be it partitioning or using a more resilient file system or something else.  Plus, having a backup before doing any of these things is computing 101. Required.

---

### Post by johnfrith1 on 2018-06-02
The plot thickens. I gambled and rebooted the system with no usb connections, and this time I was able to log in! I wrote it off to a glitch, and upgraded to 18.04, but then a similar thing happened - upgrade went ok, and this time keyboard worked, but it still wouldn't recognise password. So I rebooted and this time it did recognise the password. However when the session opened up, the keyboard stopped working. 

I've rebooted several times now and it recognises the log in password sometimes, sometimes it doesn't. It's not that I'm mis-typing, honest.

A search has suggested that I do sudo apt-get install xserver-xorg-i in Terminal. The problem there is that I'm unable to type.

I can't see how to get the screen input using mouse only, as the graphic menu system seems to have gone in 18.04.

I'm stuck.

---

### Post by Autodave on 2018-06-02
How bad would it be if you were to wipe the existing Ubuntu installation and do a fresh install of 18.04?  Of course, you need to copy anything from your Ubuntu install first.

I rarely have any luck upgrading to the next version.  I wait for the LTSs to came out and then do a clean install.

---

### Post by johnfrith1 on 2018-06-02
Thanks for posting.
No encryption.
Can't do sudo fdisk as keyboard doesn't work. 
The keyboard didn't change during upgrade. It's en (english). The keyboard is the built in one for an HP Envy.
I believe you can't upgrade from 16.04 to 18.04 directly, you have to go through  17.04.
I have done fresh LTS installs the last two times (three if you count the first one) and had a horrendous time each time, so I was looking for an easy ride this time.

---

### Post by johnfrith1 on 2018-06-02
> **Autodave said:**
> How bad would it be if you were to wipe the existing Ubuntu installation and do a fresh install of 18.04?
It takes me the best part of two days to do a fresh install,  and what if I arrived at the same place?

---

### Post by TheFu on 2018-06-02
> **johnfrith1 said:**
> Thanks for posting.
No encryption.
Can't do sudo fdisk as keyboard doesn't work. 
The keyboard didn't change during upgrade. It's en (english). The keyboard is the built in one for an HP Envy.
I believe you can't upgrade from 16.04 to 18.04 directly, you have to go through  17.04.
I have done fresh LTS installs the last two times (three if you count the first one) and had a horrendous time each time, so I was looking for an easy ride this time.

When a USB device isn't working, time to check the BIOS settings for USB stuff.

LTS-to-LTS upgrades **are** supported and have been since the beginning.  However, the GUI  has changed between the default in 16.04(unity) and the default in 18.04 (gnome), so no matter what you do, only the application settings will likely move forward.  The total "DE" settings are different, since the DE is different.

We can do better than 2 days. On a Unix system, with proper backups, it should be less than 1 hour, if the GUI didn't change and the backup storage isn't terribly slow.  Please check out **aptik**. If you backup those things, regardless of the backup tool, then getting all your settings back really shouldn't take more than 15min.

[LIST]
[*] 15 min to install the OS
[*] 15 min to put back most personal data and application settings
[*] 15 min to load the list of applications (that you make as part of the backup process)
[/LIST]
If there is 500GB of media, that will take longer, but the core system would be back and working in under an hour.   It took me 3-5 attempts to figure out the minimal needed to backup, but since then I've moved about 30 systems (mostly servers) following the same basic ideas.  Had an SSD failure on this system a few months ago. Thanks to minimal backups, it was a minor inconvenience, zero data loss.  After installing a replacement SSD, which was 50% smaller than the original, I installed the OS, restored my HOME and selected settings from /etc/ and /usr/local/, then took a list of packages previously installed and re-reinstalled those onto the machine.   Less than 1 hr and the system was back with all my settings. This includes my personalized keyboard accel setup which is controlled by the window manager.

---

### Post by johnfrith1 on 2018-06-02
> **TheFu said:**
> When a USB device isn't working, time to check the BIOS settings for USB stuff.

I think I'd been used to going to Settings via the icons in the top right of the screen - but that's not there in 18.04. So I went down a whole bunch of blind alleys until I eventually realised their was a GUI "Settings" option on the left screen menu. Dooh! Once I found that, I could get the on-screen keyboard, and from there I did ```
sudo apt install xserver-xorg-input-all
```. This got the keyboard and the USB's working.

> **TheFu said:**
> LTS-to-LTS upgrades **are** supported and have been since the beginning.
I didn't get the option to upgrade from 16.04 to 18.04 - I don't know why.

  > **TheFu said:**
> However, the GUI  has changed between the default in 16.04(unity) and the default in 18.04 (gnome), so no matter what you do, only the application settings will likely move forward.  The total "DE" settings are different, since the DE is different.

We can do better than 2 days. On a Unix system, with proper backups, it should be less than 1 hour, if the GUI didn't change and the backup storage isn't terribly slow.  

I'm sure if I knew what I was doing I could do it in a lot less time. But I have triple boot options with 2 disks, I didn't have a boot usb, it's 2 years since I last got my head around doing an install, and I have to plan down to the last detail to avoid a massive screw up!

> **TheFu said:**
> Please check out **aptik**. 

Thanks. I'll check it out. At the moment I only back up data, because I don't understand my PPAs from my Applications from my Packages.

> **TheFu said:**
> If you backup those things, regardless of the backup tool, then getting all your settings back really shouldn't take more than 15min.

[LIST]
[*] 15 min to install the OS 
[*] 15 min to put back most personal data and application settings 
[*] 15 min to load the list of applications (that you make as part of the backup process) 
[/LIST]
If there is 500GB of media, that will take longer, but the core system would be back and working in under an hour.   It took me 3-5 attempts to figure out the minimal needed to backup, but since then I've moved about 30 systems (mostly servers) following the same basic ideas.  Had an SSD failure on this system a few months ago. Thanks to minimal backups, it was a minor inconvenience, zero data loss.  After installing a replacement SSD, which was 50% smaller than the original, I installed the OS, restored my HOME and selected settings from /etc/ and /usr/local/, then took a list of packages previously installed and re-reinstalled those onto the machine.   Less than 1 hr and the system was back with all my settings. This includes my personalized keyboard accel setup which is controlled by the window manager.

You get good at what you practice, but once every 2 years won't do it for me!

Anyway thanks TheFu and Autodave for your advice and your time.

---

