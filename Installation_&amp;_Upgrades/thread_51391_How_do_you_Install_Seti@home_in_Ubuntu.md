---
title: "How do you: Install Seti@home in Ubuntu"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by AMCDeathKnight on 2005-07-23
ok; heres the background: I have just installed Ubuntu; after using windows xp. I have very little experiance and knowledge of the linux systems. I've been running the BONIC  manager on windows xp. But wish to have seti@home running on Ubuntu (perferably graphical like the BONIC manager) I have no idea how to do it; so a walkthrough would be good :-) and also how to enable it as a service so it automaticlly starts doing its thing every time i boot. Thanks

---

### Post by mike998 on 2005-07-23
From a terminal :
```
sudo apt-get install setiathome
```

---

### Post by AMCDeathKnight on 2005-07-24
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  setiathome
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6kB of archives.
After unpacking 73.7kB of additional disk space will be used.
Get:1 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/multiverse setiathome 3.08-4 [10.6kB]
Fetched 10.6kB in 12s (837B/s)

Preconfiguring packages ...
Selecting previously deselected package setiathome.
(Reading database ... 63050 files and directories currently installed.)
Unpacking setiathome (from .../setiathome_3.08-4_i386.deb) ...
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--17:58:57--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/fileUHtjYk'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu[128.32.18.176]:21... connected.
Logging in as anonymous ...
Login incorrect.
dpkg: error processing setiathome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 setiathome
E: Sub-process /usr/bin/dpkg returned an error code (1)





Something bad has happened (i think) what can I do?

---

### Post by AMCDeathKnight on 2005-07-25
plz help  :???:

---

### Post by Limulus on 2005-08-01
Hmm...  It looks like Seti finally switched over to the Boinc software, which explains the error message you're getting; the reason the setiathome package is failing is that it can't download the Seti-specific software they used to have available.

So, basically, you can't run "setiathome".  I will research this further to see if there is a Boinc debian package available for ubuntu and let you know what I find...

---

### Post by Limulus on 2005-08-01
Oh, wow, OK, I did it.  I got Boinc! to work.  [Edit: I finally got the 686 version of Linux to work after installing Boinc! too ^_-;]  It takes a little while (and Hoary gets a little more Breezy ;) but its all nicely working with Synaptic and everything...  Here's the walkthrough you wanted ^_^

Update Aug. 3: Please note that Breezy's linux-686 (2.6.12-x) currently [has audio issues](http://ubuntuforums.org/showthread.php?t=34814)... as in no audio at all ^_-; I tested this with versions x=4,5 and 6 and all won't play sound files (well, they play, but there's no sound from my speakers , though switching back to Hoary's linux-386 is fine (and Boinc! works in it with the rest of the mods in place) so use that until Breezy is released in its finished form ^_-;

Step 0: Some notes.

The Debian version of Boinc! only seems to be available for i386.  I have written this guide using a P4 (that is, i686), so if you don't use a Pentium Pro/Celeron/2/3/4 then you shouldn't use this guide.

Putting Breezy stuff on a Hoary computer shouldn't cause it to burst into flames or anything, but might cause problems in other apps or, in the worst-case scenario, ubuntu might not boot.  My experience was that, booting with "linux-386" installed, the solution I devised worked without incident.  However, when I tested "linux-686", it failed to boot with a "Kernel panic" error message similar to the one in [this thread](http://ubuntuforums.org/showthread.php?t=41562); thus the most likely cause was installing the Breezy libc6 (which is necessary to get Boinc! to work).  The solution to THIS problem is to just go ahead and install the Breezy linux-686 (2.6.12-6).  This works well, because you still retain the Hoary linux-386 (2.6.10-5) to fall back on (be sure its installed (check in Synaptic) before proceeding).

That said, let's get started...


Step 1: Download the appropriate Breezy files.

(Edit: if installed, remove linux-686 and linux-image-686)

Get the (i386-specific if given a choice) deb files from:

(installation of a Breezy 686 linux variant is optional; currently the most recent version is on [http://packages.ubuntu.com/breezy/base/linux-image-2.6.12-6-686](http://packages.ubuntu.com/breezy/base/linux-image-2.6.12-6-686) I would install it because the Hoary 686 won't boot with the following changes and its always good to have a spare kernel to boot into But again, I'd say just use the Hoary 386 linux version as it plays sounds AND runs Boinc! -_^;

[http://packages.ubuntu.com/breezy/utils/initrd-tools](http://packages.ubuntu.com/breezy/utils/initrd-tools)
[http://packages.ubuntu.com/breezy/base/libc6](http://packages.ubuntu.com/breezy/base/libc6)
[http://packages.ubuntu.com/breezy/base/locales](http://packages.ubuntu.com/breezy/base/locales)
[http://packages.ubuntu.com/breezy/libdevel/libc6-dev](http://packages.ubuntu.com/breezy/libdevel/libc6-dev)
[http://packages.ubuntu.com/breezy/devel/linux-kernel-headers](http://packages.ubuntu.com/breezy/devel/linux-kernel-headers)
[http://packages.ubuntu.com/breezy/libs/libc6-i686](http://packages.ubuntu.com/breezy/libs/libc6-i686)
[http://packages.ubuntu.com/breezy/base/libstdc++6](http://packages.ubuntu.com/breezy/base/libstdc++6)
[http://packages.ubuntu.com/breezy/devel/gcc-4.0-base](http://packages.ubuntu.com/breezy/devel/gcc-4.0-base)
[http://packages.ubuntu.com/breezy/libs/libgcc1](http://packages.ubuntu.com/breezy/libs/libgcc1)

Note: As Breezy Badger is not yet finalized, these packages are subject to change...


Step 2: Download the Debian Boinc! files.

Two choices here; either (a) download them directly or (b) get them later from Synaptic.


(a) If you want to get them directly, bypassing Synaptic, download them from:

[http://pkg-boinc.alioth.debian.org/binary/](http://pkg-boinc.alioth.debian.org/binary/)

You'll need:

boinc-client_4.71-1_i386.deb
boinc-manager_4.27-1_i386.deb


(b Part i) Otherwise, from Terminal, run:
sudo gedit /etc/apt/sources.list
and add this entry at the end:
deb [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) ./
Then save and exit.


Step 3: Install all downloaded deb files.

From Terminal navigate to the directory where all your files are sitting and run:
sudo dpkg -i *.deb


Step 2b Part ii:

If you decided to go the repository route, start Synaptic:
press reload, then install:

boinc-client
boinc-manager


Step 4: Cleanup and Reboot

If you haven't already, run Synaptic and make sure that you don't get the 'broken packages' error message.  This will indicate that the dpkg installation proceeded smoothly.  Then use Synaptic to get rid of the old Hoary linux-686 stuff; find:

linux-image-2.6.10-5-686
linux-restricted-modules-686
linux-restricted-modules-2.6.10-5-686

and mark them for removal.  When that's all done, reboot and make sure grub only shows a single 686 version of linux (2.6.12-6).


Step 5: Run Boinc! by running the command "boincmgr" (no quotes).

---

### Post by Lord Illidan on 2005-08-01
What a lot of trouble to search for aliens!!!

---

### Post by coolclassic on 2005-08-01
I have just used kynaptic to install setiathome it installed with no problems. The same should apply to synaptic.
Use find and type in seti the following files should be shown:
setathome
tkseti

select them and install

this will give a graphical interface for seti.

---

### Post by Limulus on 2005-08-01
[QUOTE=coolclassic]I have just used kynaptic to install setiathome it installed with no problems. The same should apply to synaptic.[/QUOTE]Indeed it should, but I was getting the exact same "Login incorrect" error with the setiathome package as AMCDeathKnight was...  (In fact I had been trying it for a couple days before I decided to come to UF to see if the answer was posted ;)

Note that the Seti@home website ([http://setiathome.ssl.berkeley.edu/](http://setiathome.ssl.berkeley.edu/)) now only offers links to download Boinc! instead of the classic seti app, so even if you can get the old one working (kudos to you :)), its not a bad thing if we can run the latest version of the software ;-)

---

### Post by Limulus on 2005-08-01
[QUOTE=Lord Illidan]What a lot of trouble to search for aliens!!![/QUOTE]LOL!  Yes indeed; if they'd just land their ships on the White House lawn or something that would be easy, but nooooooo... aliens like their comfy space apartments and the several thousand channels of cable they get ;)  Don't be surprised if the first Seti signal we pick up on is the grey equivalent of "Captain Ron" ^_-

---

### Post by coolclassic on 2005-08-01
Have you got the correct repositorys. As I am not at my own computer (using some crappey thing called windows ;)) I can't remember the correct ones

---

### Post by AMCDeathKnight on 2005-08-02
[QUOTE=][/QUOTE]
 Thanks for your help guys; been having trouble with linux but problem s hould be fixed now; so as soon as I get home I will try this out. Thanks alot :-)

---

### Post by Limulus on 2005-08-02
> **coolclassic]Have you got the correct repositorys. As I am not at my own computer (using some crappey thing called windows  said:**
> My sources.list file currently reads:
[quote]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main universe multiverse restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-updates main universe multiverse restricted 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

deb [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) ./
Should I add (or subtract; are archive.ubuntu.com and security.ubuntu.com redundant?)  anything from that in your opinion?

---

### Post by Gamabunta on 2005-08-03
I would use security.ubuntu for hoary-security and use archive.ubuntu for the rest. As for backports mirrormax.net is reputed to be the most reliable.

Anyway there is a non-deb way to install boinc, which is the way I did it:

1. Download [http://boinc.berkeley.edu/dl/boinc_4.43_i686-pc-linux-gnu.sh](http://boinc.berkeley.edu/dl/boinc_4.43_i686-pc-linux-gnu.sh) to your home folder
2. In a terminal type **sh boinc_4.43_i686-pc-linux-gnu.sh**
3. It will create a folder called "BOINC" in your home directory containing *boinc*, the core client, *boincmgr*, the GUI interface, and *run_client*, a script that runs the core client.
4. Delete the file you downloaded
5. Run *run_client*
6. To get *run_client* to run each time you start up, use System>Preferences>Sessions>Startup Programs and add */home/*/BOINC/run_client* where * is your username. Leave the order at 50.
7. Use [Smeg](http://ubuntuguide.org/#menu-editor) to add a menu item for *boincmgr*
8. Click on that menu item to setup BOINC, check your status, etc.
9. NOTES: May have problems found [here](http://ubuntuforums.org/showthread.php?t=45673).

Limulus, please check out [this thread](http://ubuntuforums.org/showthread.php?t=53457). If you can please help me get BOINC into Universe! Thx.

---

### Post by AMCDeathKnight on 2005-08-06
Ok i was lost at the install debian files...

Please im new to Ubuntu. Could you make a more simpler yet detailed walkthrough so all i really have to do is copy and paste?

---

### Post by coolclassic on 2005-08-07
[QUOTE=Limulus]My sources.list file currently reads:
Should I add (or subtract; are archive.ubuntu.com and security.ubuntu.com redundant?)  anything from that in your opinion?[/QUOTE]

Here is my source list:





deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  






deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 
## skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
##Kde
deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main
deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main
deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main

deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.2/kubuntu) hoary-updates main

deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./

---

### Post by Limulus on 2005-08-13
[QUOTE=AMCDeathKnight]Ok i was lost at the install debian files... Please im new to Ubuntu. Could you make a more simpler yet detailed walkthrough so all i really have to do is copy and paste?[/QUOTE] Um... not really ^_^;  Besides, if you're that new, you probably shouldn't be doing this in the first place since it can cause some rather annoying issues on your system ^_-;  Your best bet is just to wait until Breezy is released in October; then you won't need to do anything except download Boinc (and they might include it in the regular repositories, which would make it even easier).  Ask again then, ok? ^_^

---

### Post by garnertr on 2005-10-07
[QUOTE=Gamabunta]I would use security.ubuntu for hoary-security and use archive.ubuntu for the rest. As for backports mirrormax.net is reputed to be the most reliable.

[snip]

Anyway there is a non-deb way to install boinc, which is the way I did it:

4. Delete the file you downloaded
5. Run *run_client*
6. To get *run_client* to run each time you start up, use System>Preferences>Sessions>Startup Programs and add */home/*/BOINC/run_client* where * is your username. Leave the order at 50.
7. Use [Smeg](http://ubuntuguide.org/#menu-editor) to add a menu item for *boincmgr*
8. Click on that menu item to setup BOINC, check your status, etc.
9. NOTES: May have problems found 
[/QUOTE]

is there a step after run_client?  How is that command generated, do you just type run_client and it will work????

---

### Post by garnertr on 2005-10-10
I'm a dweeb, forgot the ./ command, anyway, got it running, now setting it up on the wifes computer...

---

