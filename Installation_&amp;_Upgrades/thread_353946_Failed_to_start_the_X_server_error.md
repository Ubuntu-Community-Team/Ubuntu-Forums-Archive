---
title: "Failed to start the X server error"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by darkcyber on 2007-02-05
I'm trying (unsuccessfully) to just run the Ubuntu 6.10 Live CD on two older pc's...one is a PIII 450 mhz and the other is a PIII 850 mhz pc.  Each time I put the ubuntu cd in and boot up I get to the splash screen that has the menu and I select number 1, which is 'Install or start Ubuntu'.  From there is runs for a while and then I get this error screen that says:

'Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem'

I select OK and then the second page shows the following information.

It list the build versions and number of ubuntu and then toward the bottom it says this:

(EE) Screen(s) found, but none have a usable configuration

Fatal server Error:
No screen found.

Does anyone have a clue what's going on here?  My goal is to install ubuntu on these, but I can't even load the live cd to do that.

Thanks!

---

### Post by taurus on 2007-02-05
Do you get to a prompt when you press <Ctrl><Alt>F2?  How much RAM do those old machines have anyway?

---

### Post by darkcyber on 2007-02-05
> **taurus said:**
> Do you get to a prompt when you press <Ctrl><Alt>F2?  How much RAM do those old machines have anyway?


Other than the main menu that comes up...i.e. where you select 'install or start' and then other options below that, there is no other prompt I get.  The next thing I get is that error screen and the only thing on it is to select OK to see the error. 

Where are you talking about pressing <Ctrl><Alt>F2 at?

One system has 512 megs and the other has 384 megs.

---

### Post by darkcyber on 2007-02-05
Bump...no one else has run into this problem?

---

### Post by gradedcheese on 2007-02-06
it likely means that the X11 configuration tool wasn't able to detect/support your video card automatically and this an /etc/X11/xorg.conf file was generated that does not have a valid 'screen' section for your video card.  When the installer tried to start X (ie: the GUI) it of course failed.  If you don't use menu option 1, are there alternate installation methods?  Perhaps an old-style text-based (ncurses) install?  If so, use that, and then set up X manually after things get installed.  Otherwise, I am not sure... borrow a different video card for the installation?

Incidentally, do you know the name/model of the video card in this PC?  If not, after X fails and you get a shell (press Control+Alt+F1 as previously suggested if you need to), type:

lspci

to see a list of devices, including the video card...

---

### Post by aberry5555 on 2007-02-06
This might be to do with the CD being a dodgy copy, as it's doing the same on both PCs. on the first menu scroll down to "Check CD". If this is OK then try the following:

I think it could be having difficulty loading the graphics drivers, try reverting to the "vesa" bog-standard drivers by doing the following:

at the startup screen press F6, which will bring up the boot line. delete the "quite - splash" part and enter in "break=bottom". Save this and carry on booting. 

Instead of the fancy looking Ubuntu splash screen you'll get a few messages (if they are errors don't worry too much right now) and then, after a while, you will get a command prompt. 

Type in "chroot /root nano /etc/X11/xorg.conf". This will bring up the "xorg.conf" file which is the configuration file for the graphics. Scroll down to the heading "Device" under which will be a sub-heading called "Driver".

Change whatever is to the right of the driver (e.g. ATI if it's an ATI card or otherwise) to "vesa". Now press ctrl+O and ctrl+X to save and exit the text file. 

This will bring you back to the Command line, type exit in to this and, hopefully, Ubuntu should boot properly.

---

### Post by ruan on 2007-02-06
I did all these commands and stil doent work


Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

---

### Post by aberry5555 on 2007-02-06
What hardware are you running ruan?

---

### Post by darkcyber on 2007-02-06
Does ubuntu work with PCI graphic cards?  Because that is what I have in both pc's that I'm having problems with.  I've installed it on pc's running AGP and PCI-E with no problems.

The cards I have is a Number9 and an older ATI with tv tuner built onboard.  Would have to go pull them from the pc's to get the exact model numbers.

Also, when is gives me those error statements, if I select NO (for not viewing the error) then it says this:

The X server is now disabled. Restart GDM when it is configured correctly <OK>

---

### Post by gradedcheese on 2007-02-06
> **darkcyber said:**
> The cards I have is a Number9 and an older ATI with tv tuner built onboard.  Would have to go pull them from the pc's to get the exact model numbers.

Like I said earlier, the 'lspci' command will tell you quiet a bit about the cards and their chipsets, and that information will be helpful.  PCI cards are supported just fine, though there might be a few chipsets that don't have much support.

---

### Post by aberry5555 on 2007-02-07
dark cyber try what I said, I can almost guarantee you it's because of ubuntu's automatic allocation of dodgy drivers.

---

### Post by Rogandali on 2007-02-09
I have the same problem as Darkcyber, but with a Dell 5150 dual core computer with 1024mb memory and a Radeon X600 hypermemory graphics card.  I have only just downloaded the CD and am very new to this and fairly limited in knowledge.  The CD integrity is OK and I also ran the Md5SUM program. I have followed the suggested fix above, but I keep getting responses like " no file found" and "Root nano not found". I have tried lots of combinations of upper and lower case, with and without spaces and still no do not get to the xorg.conf file.  Can anyone tell me what I am doing wrong?

---

### Post by Mencius on 2007-02-09
Same problem as Darkcyber, and when I type in the chroot command i get a file/ directory not found message.

I have also tried the manual set up of the X server and when i get to the option to select the colour depth in bits the command line comes back up and I cant select anything.

I have an Nvidia 7950 GT, Does anyone have anymore ideas on what to try?

---

### Post by Rogandali on 2007-02-13
I have found a post in another thread that gets me to the xorg.conf file.  Instead of the entry "chroot root nano etc", type "sudo nano /etc/X11/xorg.conf".  That gets me to the xorg.conf file where I can change "ATI" to "Radeon" or "vesa". However, when I have saved this, "Exit" does not continue the boot and I have to use ctrl+alt+delete to get any result.  This seems to restart the boot process from the beginning, and as I am using the live CD, the xorg.conf setting reverts to "ATI". So it seems that this work-around only works if you have installed Ubuntu on your hard disk. Having said all that, I find that I get good results if I ask for a "safe mode" start.  I have read that someone tried this and it only worked in Spanish, but mine works in english.  Hope this helps.

---

### Post by darkcyber on 2007-02-14
> **aberry5555 said:**
> dark cyber try what I said, I can almost guarantee you it's because of ubuntu's automatic allocation of dodgy drivers.

aberry5555,

The cd is good.  I've checked one of them and it checked ok.  I've tried 2 more cd's burned from different burners and get the exact same error...so it's nothing to do with a bad cd...it's something with ubuntu and my video cards I guess.  They are two different cards and two different motherboards, but get the same error.

---

### Post by greenxeyezz on 2007-02-14
I too am getting this error and i have an ati x700 i havent tried any of these methods at all, but i will when i get home.

it definitely has something to do with the graphics card from everything i have been reading, and i havent found a CLEAR work around yet.

as it is booting from the LIVE cd none of the changes being made a "saved" once restarted

---

### Post by d-train24 on 2007-02-15
i am getting the same error it if you are saying its the graphics card are you saying ATI is the one xorg is running, because i have an ati and still get the error i have reinstalled, updated and opend and investagated the xorg file but its true that once you configure how are you supposed to test it, other than reboot  :confused: by the way this cd is a requested free cd sent by mail????

---

### Post by darkcyber on 2007-02-15
Well, I tried booting up with the Xubuntu live cd as some had suggested it might do better on older pc's.  But it errored out as well.  Although I got different errors with it...didn't really take time to read what they were.  I had to get that pc rebooted and up for some work I had to do.

---

### Post by Levant on 2007-02-17
I'm having pretty much the same problem as the OP. I tried the various solutions in this thread, but none seem to work.

My graphics card is NVIDIA GeForce 8800 GTS, can anyone lend a hand?

---

### Post by hove99 on 2007-02-22
Bump. Same issues as the user above.

---

### Post by hvymtlsteve on 2007-02-22
This is my first linux install-- here's what I found, very quickly:

If X does not load with your graphics chipset right away, you can use the "alternate" version of this CD. 
There, you'll have the option to do "text install" or "oem install" which was what I did. 
 
This at least installs the OS for you. 
How to get X to work after that? Well, that's what I came to find out...

---

### Post by hvymtlsteve on 2007-02-22
> **aberry5555 said:**
> This might be to do with the CD being a dodgy copy, as it's doing the same on both PCs. on the first menu scroll down to "Check CD". If this is OK then try the following:

I think it could be having difficulty loading the graphics drivers, try reverting to the "vesa" bog-standard drivers by doing the following:

at the startup screen press F6, which will bring up the boot line. delete the "quite - splash" part and enter in "break=bottom". Save this and carry on booting. 

Instead of the fancy looking Ubuntu splash screen you'll get a few messages (if they are errors don't worry too much right now) and then, after a while, you will get a command prompt. 

Type in "chroot /root nano /etc/X11/xorg.conf". This will bring up the "xorg.conf" file which is the configuration file for the graphics. Scroll down to the heading "Device" under which will be a sub-heading called "Driver".

Change whatever is to the right of the driver (e.g. ATI if it's an ATI card or otherwise) to "vesa". Now press ctrl+O and ctrl+X to save and exit the text file. 

This will bring you back to the Command line, type exit in to this and, hopefully, Ubuntu should boot properly.

This worked for me, after already having installed the OS by using the alternate version of the CD as I described above. 
Minus the "chroot root" part of the command. 

Excellent work!
:guitar:

---

### Post by darkcyber on 2007-02-27
> **hvymtlsteve said:**
> This is my first linux install-- here's what I found, very quickly:

If X does not load with your graphics chipset right away, you can use the "alternate" version of this CD. 
There, you'll have the option to do "text install" or "oem install" which was what I did. 
 
This at least installs the OS for you. 
How to get X to work after that? Well, that's what I came to find out...


Thanks for the tip...downloading it now and going to try it.  Nothing else has worked, maybe this will.

---

