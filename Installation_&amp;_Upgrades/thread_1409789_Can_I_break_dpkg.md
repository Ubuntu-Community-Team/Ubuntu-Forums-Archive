---
title: "Can I break dpkg?"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by kazinnud on 2010-02-18
I can't get flashplugin-nonfree to work; sudo apt-get install flashplugin-nonfree outputs the following:

2010-02-17 21:57:46 (527 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753]

Download done.
cp: cannot stat `WeiDU': No such file or directory
cp: cannot stat `WeiGUI': No such file or directory
cp: cannot stat `WeInstall': No such file or directory
cp: cannot stat `tisunpack': No such file or directory
cp: cannot stat `tolower': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weidu': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weigui': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weinstall': No such file or directory
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

the cp's and ln's are from an install.sh from weidu-linux.  apparently, i have compiled things in a terrible way.  (i'm pretty sure i tried "make install.sh" and then "sudo checkinstall" and the package never went through, but now...)  

now, i'm not so worried about the flash because any time i use apt-get this script of cp's and ln's runs (on the other hand, flash is the only package not working, so maybe this is just a cosmetic issue...).  for example, ace of penguins outputs the same stuff (but at least it runs).

I don't want help with the flash issue--i just want my apt-get / dpkg to be clean again!  i'll never try to run baldur's gate with weidu mod's again, i promise!

Karmic Koala, please let me watch hulu again...

izak

p.s. baldur's gate runs great.

---

### Post by kazinnud on 2010-02-18
i have tried to uninstall the offending flash, reinstall, and nothing brings it back.  always the same error.

have tried
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get clean
sudo dpkg audit
sudo dpkg --config flashplugin-installer
sudo apt-get install -f

have tried deleting what others have called "offending files" in var/lib/dpkg/info (some prerms and such) and var/cache/apt (the packages themselves).

have not tried getting the binary from flash website, but getting their tarball and following the instructions on adobe's website does nothing (unpack tarball to desktop, navigate terminal to desktop, type "./flashplugin-installer" and nothing happens).

thanks for your help :)

---

### Post by kazinnud on 2010-02-18
frankie@frankie-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [871B]                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Fetched 3,600B in 1s (2,314B/s)
Reading package lists... Done
frankie@frankie-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up flashplugin-installer (10.0.45.2ubuntu0.9.10.1) ...
Downloading...
--2010-02-17 22:51:47--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz)
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4028753 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.45.2.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 69.3K 56s
    50K .......... .......... .......... .......... ..........  2%  258K 35s
   100K .......... .......... .......... .......... ..........  3%  311K 27s
   150K .......... .......... .......... .......... ..........  5%  741K 21s
   200K .......... .......... .......... .......... ..........  6%  443K 19s
   250K .......... .......... .......... .......... ..........  7%  236K 18s
   300K .......... .......... .......... .......... ..........  8%  224M 15s
   350K .......... .......... .......... .......... .......... 10%  240M 13s
   400K .......... .......... .......... .......... .......... 11% 54.5K 18s
   450K .......... .......... .......... .......... .......... 12%  314K 17s
   500K .......... .......... .......... .......... .......... 13%  131K 18s
   550K .......... .......... .......... .......... .......... 15% 71.3K 20s
   600K .......... .......... .......... .......... .......... 16% 90.8K 21s
   650K .......... .......... .......... .......... .......... 17%  121K 21s
   700K .......... .......... .......... .......... .......... 19%  101K 22s
   750K .......... .......... .......... .......... .......... 20%  125K 21s
   800K .......... .......... .......... .......... .......... 21%  124K 21s
   850K .......... .......... .......... .......... .......... 22%  138K 21s
   900K .......... .......... .......... .......... .......... 24%  139K 21s
   950K .......... .......... .......... .......... .......... 25%  157K 20s
  1000K .......... .......... .......... .......... .......... 26%  150K 20s
  1050K .......... .......... .......... .......... .......... 27%  145K 20s
  1100K .......... .......... .......... .......... .......... 29%  194K 19s
  1150K .......... .......... .......... .......... .......... 30%  170K 19s
  1200K .......... .......... .......... .......... .......... 31%  200K 18s
  1250K .......... .......... .......... .......... .......... 33%  171K 18s
  1300K .......... .......... .......... .......... .......... 34%  199K 17s
  1350K .......... .......... .......... .......... .......... 35%  180K 17s
  1400K .......... .......... .......... .......... .......... 36%  241K 16s
  1450K .......... .......... .......... .......... .......... 38%  190K 16s
  1500K .......... .......... .......... .......... .......... 39%  198K 15s
  1550K .......... .......... .......... .......... .......... 40%  247K 15s
  1600K .......... .......... .......... .......... .......... 41%  207K 14s
  1650K .......... .......... .......... .......... .......... 43%  233K 14s
  1700K .......... .......... .......... .......... .......... 44%  211K 14s
  1750K .......... .......... .......... .......... .......... 45%  254K 13s
  1800K .......... .......... .......... .......... .......... 47%  229K 13s
  1850K .......... .......... .......... .......... .......... 48%  255K 12s
  1900K .......... .......... .......... .......... .......... 49%  240K 12s
  1950K .......... .......... .......... .......... .......... 50%  260K 11s
  2000K .......... .......... .......... .......... .......... 52%  263K 11s
  2050K .......... .......... .......... .......... .......... 53%  139K 11s
  2100K .......... .......... .......... .......... .......... 54%  182K 11s
  2150K .......... .......... .......... .......... .......... 55%  133K 10s
  2200K .......... .......... .......... .......... .......... 57% 92.0K 10s
  2250K .......... .......... .......... .......... .......... 58% 93.7K 10s
  2300K .......... .......... .......... .......... .......... 59%  111K 10s
  2350K .......... .......... .......... .......... .......... 61%  112K 10s
  2400K .......... .......... .......... .......... .......... 62%  135K 9s
  2450K .......... .......... .......... .......... .......... 63%  137K 9s
  2500K .......... .......... .......... .......... .......... 64%  139K 9s
  2550K .......... .......... .......... .......... .......... 66%  142K 8s
  2600K .......... .......... .......... .......... .......... 67%  142K 8s
  2650K .......... .......... .......... .......... .......... 68%  167K 8s
  2700K .......... .......... .......... .......... .......... 69%  180K 7s
  2750K .......... .......... .......... .......... .......... 71%  167K 7s
  2800K .......... .......... .......... .......... .......... 72%  172K 7s
  2850K .......... .......... .......... .......... .......... 73%  183K 7s
  2900K .......... .......... .......... .......... .......... 74%  139K 6s
  2950K .......... .......... .......... .......... .......... 76%  104K 6s
  3000K .......... .......... .......... .......... .......... 77% 85.0K 6s
  3050K .......... .......... .......... .......... .......... 78% 89.4K 5s
  3100K .......... .......... .......... .......... .......... 80% 84.3K 5s
  3150K .......... .......... .......... .......... .......... 81%  104K 5s
  3200K .......... .......... .......... .......... .......... 82% 97.5K 5s
  3250K .......... .......... .......... .......... .......... 83%  131K 4s
  3300K .......... .......... .......... .......... .......... 85%  133K 4s
  3350K .......... .......... .......... .......... .......... 86%  137K 4s
  3400K .......... .......... .......... .......... .......... 87%  139K 3s
  3450K .......... .......... .......... .......... .......... 88%  142K 3s
  3500K .......... .......... .......... .......... .......... 90%  137K 3s
  3550K .......... .......... .......... .......... .......... 91% 92.0K 2s
  3600K .......... .......... .......... .......... .......... 92% 98.8K 2s
  3650K .......... .......... .......... .......... .......... 94%  116K 2s
  3700K .......... .......... .......... .......... .......... 95%  106K 1s
  3750K .......... .......... .......... .......... .......... 96%  126K 1s
  3800K .......... .......... .......... .......... .......... 97%  132K 1s
  3850K .......... .......... .......... .......... .......... 99%  138K 0s
  3900K .......... .......... .......... ....                 100%  151K=27s

2010-02-17 22:52:15 (144 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753]

Download done.
cp: cannot stat `WeiDU': No such file or directory
cp: cannot stat `WeiGUI': No such file or directory
cp: cannot stat `WeInstall': No such file or directory
cp: cannot stat `tisunpack': No such file or directory
cp: cannot stat `tolower': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weidu': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weigui': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weinstall': No such file or directory
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankie@frankie-desktop:~$ 

why on earth does apt-get's calling dpkg do that freaking weidu stuff?  i am beginning to care less about flash and more about this error...  which is sad because i really just want to watch hulu...

---

### Post by kazinnud on 2010-02-18
finally, i must appeal to the humanity of the ubuntu forums: my girlfriend is going to kill me if she figures out that i broke the tv with baldur's gate...  kill me...

---

### Post by Soul-Sing on 2010-02-18
: [http://ubuntuforums.org/showthread.php?p=8844222#post8844222](http://ubuntuforums.org/showthread.php?p=8844222#post8844222)
postcount 7

---

### Post by Soul-Sing on 2010-02-18
ps did you doublepost this? : [http://ubuntuforums.org/showthread.php?p=8844222#post8844222](http://ubuntuforums.org/showthread.php?p=8844222#post8844222)

---

### Post by kazinnud on 2010-02-18
i don't think i double posted; the concern in the other thread is how to fix flash.  the concern in this thread is "what is up with my dpkg?"

i should not have used my broken flash installs as an example; even installing ace of penguins brings up that strange weidu stuff when apt calls dpkg.  

the only difference is that ace of penguins works while flash does not.

but here i am concerned about my dpkg--how can i clean out that weidu stuff?

izak

---

### Post by kazinnud on 2010-02-18
Attempting to reinstall dpkg through Synaptic tries to reinstall the flashplugin components, returns the following error:

E: flashplugin-installer: subprocess installed post-installation script returned error exit status 1
E: flashplugin-nonfree: dependency problems - leaving unconfigured

Also, still coughing up weird baldur's gate crap.

izak

edit: after sudo dpkg --purge flashcrapola, reinstalling dpkg through synaptic seems to go fine, but the details tab ends with "setting up dpkg" and nothing further...

edit: further info--now ace of penguins installs through synaptic without the strange weidu/baldur's gate stuff, but it doesn't show up in the menus (have to go to /usr/games).  HOWEVER, flashplugin and such still produce the strange baldur's gate scripts and still don't work.  

What exactly is going on when apt-get calls dpkg such that it always runs these scripts?  If someone could guide me through a strace, it would be greatly appreciated...

---

### Post by kazinnud on 2010-02-18
solved

the problem was a stray file named "install" from the weidu for linux pack which had made its way into /usr/local/sbin

when installing the flashplugin-installer, dpkg would call this broken install file and screw everything up.

so, flashplugin was never really the problem.  i had screwed up dpkg.  i didn't know it would look in /usr/local/sbin so i never thought that putting that install file in there (and, and!--adding it to $PATH) would be a problem.

i really suck at linux.

---

