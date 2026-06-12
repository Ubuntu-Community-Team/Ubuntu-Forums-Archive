---
title: "monitor cuts off. mouse and keyboard lock up from live CDs"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by markMDW on 2010-05-19
this is a bit long, thanks for reading and replying! my machine: a custum built with Intel core 2 quad processor, two harddrives each with atleast 200GB. 4GB of RAM. The motherboard has an AMI Bios. Two DVD RW drives, and I've got a brand new 24" Viewsonic 1080p monitor. Ubuntu monitor cuts off on boot from wubi.exe installed versions. mouse and keyboard lock up from live CDs.
------
[[side note: My secondary machine with an AthlonXP processor is running Xubuntu well now after installing patches to 10.04. 9.10 had ran perfectly but I decided to upgraded to the newest version. I regretted that initially. I had to try twice at the 10.04 Xubuntu installation on the AthlonXP but was successful at a really stable setup only after a complete and total reinstall of Xubuntu and without attempting to save the XP installation, and after installing the now available patches. My first attempt at upgrade went terribly after I selected the xubuntu 10.04 upgrade package from the program manager to install, from Xubuntu 9.10. It seemed far less stable than 9.10 with frequent crashes back to the login screen, maybe every 10 minutes or so. I also lost my ability to run XP from the ubuntu installedOS selection menu.. selecting Windows XP from the selection menu would cause a pause, as-if attempting to load XP, but then my Athlon-XP system would jump back to ubuntu's OS selection menu again where Windows XP and Ubuntu both appeared available for initializing. But now after reinstalling Xubuntu without an OS selector menu (without saving the Windows XP partition which no longer ran), and reinstalling the now available patches, it is very stable]] 
-------------------------
 
Back to my main concern, the Intel Core-i5 machine with specs listed above: I'm experiencing system lockup with every linux distribution ive attempted to run (live cds of Ubuntu 10.04 and 9.10, Xubuntu 10.04, Fedora12, Knoppix under XWindow session option.) And using the wubi.exe installed Ubuntu under Windows 7 failed due to Monitor shutting down from no signal being received. several attempts with 64bit and 32bit versions-- installing, uninstalling and reinstalling, were made. Each time after selecting Ubuntu from the OS menu selector the systems reports back "loading 5, 4, 3. " [counting down] then monitor reports no input received, then it cuts off entirely. The activity lights on the computer will remain on and the hard drive indicator appears to be active for a split second about every 5 seconds or so. This goes on indefinitely. And Windows 7 runs well on this machine. 64bit and 32bit versions of Ubuntu 10.04 have been tried using the wubi.exe Windows installer.
 
With the Live CDs of Ubuntu and Xubuntu or Fedora12 on this machine (Intel Core 2 Quad) I would get lock ups and the mouse and keyboard would quit working. I could move the cursor with the mouse but clicking would not activiate anything. The keyboard was useless also. With ubuntu It locked up on the select language menu selection once, other attempts would lock up just a couple of minutes after running Firefox, the first application selected after bootup. Xubuntu would always boot from live cd though but lock up later in Firefox. I also tried 9.10 versions and experienced the same problems with lock up just minutes after running Firefox, the first application run for testing after bootup from live cd. Additionally, I tried Fedora12 (same problem). Finally I tried Knoppix Adriane live cd. Everything was stable as long as I stayed out of the XWindows option. I was even able to run Firefox just fine as long as I was not inside XWindows, the last option on the menu. As soon as I ran the XWindows session and opened Firefox, shortly afterward the system lockup occured yet the mouse cursor would freely move about, the Keyboard was inactive and mouse clicks at links and buttons did nothing.
 
Since I haven't yet found a stable version of linux for my Intel Core-2-Quad system I'm thinking it might be the XWindows interface common to almost all distributions. I've got two harddrives on this machine and now I am thinking about leaving Windows7 alone and installing a Ubuntu version solely on my secondary hard drive (avoiding wubi.exe windows installer) and using the Bios boot selector instead of having a menu program pop up prompting for the OS I want to boot up. I'm hoping that after I load the updates that the system will become stable and that Windows and Linux will not interfer with each other if I keep them nice and seperated. 
 
I'm trying to pick up this Linux and Ubuntu. My first experience with Xubuntu 9.10 on my Athlon-XP was fantastic. please offer suggestions? Thanks again for reading!
 
----Edit to now solved tread [microprocessor is Intel Core i5 rather than Core2-Quad listed throughout thread; probably would not make any difference at all, I guess]

---

### Post by davidmohammed on 2010-05-19
Hi there,
  you didn't mention what type of graphics card you have.

When using the live CD, press F6 when the language selection screen is displayed. Try selecting one or more of the options such as nomodeset, noapic, nolapic etc.

---

### Post by markMDW on 2010-05-19
Hi, The video card in the Intel Core-2-Quad machine, the one with the monitor shutting off or keyboard / mouse-clicks not working, is a "NVIDIA GeForce 8400 GS".  The monitor is plugged in via the DVI-D cable.  

Do you think it would be worth while connecting it up with the available VGA port instead of the DVI-D port?  Maybe the Linux driver has a glitch with DVI-D output..  Thanks!

---

### Post by davidmohammed on 2010-05-20
I doubt it, but it wouldnt do any harm to test running vga only for a while.  How did you get on trying to install with one or more of those switches in my post?

---

### Post by oldfred on 2010-05-20
I have a Nvidia 9600Gt and had to do this:

boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

On my portable from the liveCd it changes from low graphice booting to high graphics booting just about the same point as my monitor went to sleep on my desktop. nomodeset must prevent that change.

---

### Post by markMDW on 2010-05-21
The nomodeset option works on the live cds.  I installed ubuntu 10.04 from cd and at the GRUB menu used the 'e' to edit out "quiet splash" with "nomodeset".  BUT.. the bootup took me only to a command line Ubuntu welcome and text login prompt.  I could log in but the entire screen was command line without any graphics and I'm clueless as to what Linux commands to type next.   

When I try to boot the installation without the 'nomodeset' option [standard settings] the monitor goes to sleep.  The nomodeset from live cd brings me to the low-res but working version of Ubuntu.  The nomodeset from my harddrive install takes me to command line only.  

Can you tell me how to load the xwindows with Gnome for Ubuntu from the command line I get after booting from my new installation?

Thanks for all the replies..  I'm making progress now! :)

---

### Post by oldfred on 2010-05-21
This starts graphics if it works. But you can run all the update commands from the command line which may also help.
startx

Commands to run to update.
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Catharsis on 2010-05-21
Also try:

1) Leave "quiet splash" but just add "nomodeset" to the end, and also removing "quiet splash" but not replacing it with anything.

2) Booting into Recovery Mode (in grub, select the recovery mode kernel). Boot normally and in failsafeX.

---

### Post by markMDW on 2010-05-21
Hi, I've tried the recommendations above but experienced setbacks of one sort or another each time.  

when I use the apt-get command in the text mode it boots to I get two messages back, 1> file is locked 13) permission denied 2> cannot access locked ... directory  [something to that affect]

I've now tried editing the GRUB bootup by including "quiet splash nomodeset" or just "nomodeset" or just the default "quite splash".  various things happen, if don't use the nomodeset it seems the monitor always goes to sleep.  And, if I use nomodeset by itself the bootup after using the "startx" commands frequently locks up upon "checking battery state"  then I have to hit the reset button.   But when using the "startx" command at the command line prompt after I've edited the GRUB boot sequence with both the quite splash nomodeset options then I can get into the GNOME desktop.   However, the internet connection will not work and I cannot download any updates.  I don't see the popup prompting to download a new video driver.

The internet should be working I figure.  Its a direct line into the same router I'm using now.  The green light is on for the connection of that line, and the eithernet card shows an orange light that its plugged in.  And the internet is working on this secondary computer I'm typing on now.  Yesterday using the live CDs the internet was working fine with the nomodeset option selected on liveCD bootup.

And so next I need help figuring out why internet access is failing.  And I need help figuring out how to the get the apt-get commands to work in text mode after I bootup using the nomodeset GRUB option from the hard drive installation of Ubuntu 10.04.    The boot into the commandline did welcome me to Ubuntu and it did report back that 82 updates plus 1 security update were available, and so I'm not sure where it was getting that information if the internet was failing.  [firefox didn't work and I couldn't update the programs]

Thanks for everyones help and patience!

---

### Post by markMDW on 2010-05-21
oh, also I wanted to add that I did try the Recovery Mode option from Grub.  The monitor goes to sleep with that option.  Thanks again for everyones support!

---

### Post by oldfred on 2010-05-21
If INTERNET is not working the text mode commands to update will not work. Everything nowadays needs internet. Under System, Administration, hardware drivers does it offer to download a new driver?

Or system preferences, network connections, do you get an auto eth0? If not try adding. If you have it edit and check settings.

---

### Post by Catharsis on 2010-05-21
Try unplugging your ethernet cord and then plugging it back in once you get your graphics working with "startx".

If that doesn't work, boot the recovery kernel and select "root with networking" (second from the bottom) in the menu. This *should* get you a terminal with networking (since there's no X Server or modules to mess things up). From there, try oldfred's update commands again. You can exit the root shell by typing "reboot".

---

### Post by markMDW on 2010-05-22
Hi, I've tried everything except booting the recovery kernel selecting "root with networking". I will attempt that tomorrow afternoon CDT when I get to that computer again. 
 
I spent a good bit of the time plugging and unplugging the eithernet cable and even power cycling the cable modem and router. Eventually I double checked and verified that the lan card was working running Windows. The hardware isn't malfunctinging atleast.
 
The odd thing is that after running Windows I could no longer get into graphics using the "nomodeset" options and then "startx" at the command line. I rebooted and also turned the machine off to let it rest for several minutes and made several attempts. Before this those options were working half the time to get into the Ubuntu graphics. I suppose if I tried many more times it would eventually boot into graphics but I ran out of time to play with it.
 
I'm thinking that if I can't get into the graphical Ubuntu 10.04 with networking and internet then I will attempt to download a driver for linux and place it on CD then attempt to load it from the command line. The big problem with that is my lack of experience at the command line. I will use oldfred's commands and then try to find a site with a list of additional commands that might load the driver from CD and then apply that to the OS where it needs to be. 
 
And then.. if everything goes perfectly the driver will push Ubuntu into operating with stability for me. 
 
advice and links are greatly appreciated. Thanks very much! Time for a movie :popcorn:

---

### Post by markMDW on 2010-05-23
update,  I still haven't been successful again at using the "startx" command to load the "nomodeset" graphical Ubuntu again.  Not sure why.  

From the nvidia website I downloaded Linux drivers for my 8400GS video card.  This is a .run file package that I am supposed to do as follows according to NVidia 
" change to the directory containing the driver package and install the driver by running, as root, sh ./NVIDIA-Linux-x86-195.36.24-pkg1.run "

I can copy that over to a USB thumbdrive or CDROM but am not sure what commands to use to run the file from external media or how to do this 'as root'.  I feel like I getting close to solving the problem but there are a few more barriers still in the way.  all advice is greatly appreciated.  thanks for your help

---

### Post by davidmohammed on 2010-05-23
may be this "[how to]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")" will give you a pointer in the right direction...

---

### Post by markMDW on 2010-05-23
Thanks, for the link.  I've been reading that very thread just now.  Still no luck

I was able to get into a 'nomodeset' from 'startx' low-res graphics session with Ubuntu after many many attempts.  I also was able to find an asnwer for one of oldfred's earlier questions about my driver:

oldfred, when I go to system>administration>hardware drivers I get a message that says "cannot connect to D-BUS ... no such file or directory"  Also, for your second queston regarding lack of internet, could you give me more advice on how to manually add the eth0 option.

Last thing, I tried copying the run files to both CD and USB thumbdrive.  For some reason the file manager shows CDROM as empty and for the thumbdrive it doesn't show anything either under the MEDIA folder.  

I think I may try Xubuntu 10.04 install and wipe this install out.  

One last unique thing about my system worth mentioning, the install is on my second harddrive, not the one indicated in CMOS/BIOS for intial bootup.  I understand that wouldn't make a bit of difference since the GRUB loader is on the boot disc and directs it to Ubuntu (my second hard drive) or Windows7 (my first harddrive indicated for bootup from CMOS/BIOS  ..but just in case I figure I should mention that.  

Thanks!!

---

### Post by oldfred on 2010-05-24
If you are not getting ethernet connection automatically, you may need a driver for that also. Are you using a wired connection. You should be able to system, preferences, network connection. It should show auto eth0. If not try adding, if there try editing and make sure DHCP is set unde ipv4 settings.

---

### Post by markMDW on 2010-05-24
Hi there, thanks for checking back.  I'm using a wired connecton.  I tried selecting the auto eth0 from network connections but it didn't have any noticable affect.  Also the CDROM and USB thumbdrive aren't accessable by the file manager when I pop in a CD or plug in a thumbdrive with the video driver.  I verified that its on both on my other working machine with Xubuntu, and it sees the files just fine.  My keyboard and mouse on the problem machine are USB and I can run LiveCDs, however, so those failures must not be hardware related.  It's seems as if the problem machine (intel core2quad with nvidia 8400gs card and a windows installation that works) is booting from harddrive with the nomodeset option but can't read anything except the harddrive it booted from.  
 
my next troubleshooting measure late tonight will be to boot from live cd with Ubuntu 9.10 and copy the video drivers into the mounted harddrive in the download folder, then attempting a manual install.  If I'm lucky I will be able to get into graphics and get it done.   Thanks again

---

### Post by oldfred on 2010-05-24
You may want to check BIOS settings. Hard drives need to be in IDE compatiblity mode. Mouse & keyboard need USB setttings.

I could not get grub to see my mouse & keyboard when I put a new mother board in a year ago. It was BIOS settings.

---

### Post by markMDW on 2010-05-25
thanks for the tip, I will give those a check.  The mouse and keyboard to work initially when I boot from LiveCD.  Last evening I managed to run LiveCD Ubuntu 9.10 and everthing runs normally from 30 seconds to 5 minutes, and then the lockup occurs.  In that lapse of time I was able to use the file manager to view the drivers on USB thumbdrive.  I also viewed the Ubuntu 10.04 harddrive and tried to copy the drivers into my download directory.  I could COPY from but not PASTE into.  Anyhow, the internet works fine from 9.10 live cd and I run Linux for up to 5 minutes before lockup.  In that time I managed to download the Ubuntu recommended display driver for NVIDIA, which I did for the heck of it.  But I suppose that did no good at all since I was running from a liveCD session and not the 10.04 hard drive installation.
 
I need to figure out why I cannot copy the .run file into the download directory so that I can then boot 10.04 from a nomodeset option and load it manually since I don't have internet access from 10.04 and the nomodeset option.  Any ideas?
 
I'm starting to think that the problems are more widespread than could be solved by a new display driver, but if I can manage to get it installed I can atleast rule that out.  I think I did make a bit of progress at least by being able to view the contents of the thumbdrive from 9.10 liveCD.     I don't have any hopes of getting this computer to run LINUX anytime soon but I plan to keep on troubleshooting every evening.  I appreciate all the advice everyone's given and will post the progress and lack thereof.

---

### Post by markMDW on 2010-05-26
update, last evening I installed Xubuntu 9.10 on the computer and erased the problematic Ubuntu 10.04 lucid lynx installation.   After installation I was able to install all updates.  
 
Everything went well except for one small glitch.  I checked for Ubuntu recommended drivers and it promted two restricted options for my NVideo 8400GS card, one was listed as "recommended" the other was optional for install.  I forgot the numbering, but the higher number was the one recommended and the lower number was just optional.  I tried the recommended restricted driver first and it failed to install and then I tried the earlier version and it installed without a hitch.  [seems my computer balks at new stuff even though it's my "new" computer]
 
After that I test drove Xubuntu for 10 minutes and it worked without any problems whatsoever.  My goal is to eventually install Ubuntu 10.04 on this machine but I may wait for a "second spin" of the iso, hoping that whatever causes the monitor going to sleep and/or lockouts of keyboard, mouse clicks, CDROM and USB Thumbdrive will get resolved.
 
The good news for now is that Xubuntu 9.10 seems to work!  I will keep this thread updated as I make additional attempts at installing Ubuntu 10.04.  Thanks to everyone who has posted suggestions.

---

### Post by markMDW on 2010-05-28
update, I installed the Ubuntu 9.10 and overwrote the Xubuntu 9.10 installation, then installed updates (over 200). Before I installed the recommended restricted NVIDIA driver I test drove the installation with firefox and it locked up after about 5 seconds (mouseclicks and keyboard), just like with the live CDs.  I could still move the cursor around with the mouse but that's about it. 
 
To resolve that problem successfully I went to the administration menu and selected the hardware drivers and it notified me of the two versions available. [Where as with the prior Xubuntu installation I was only able to install the 173 version, on this try I was able to install the '185' version, which the updater had recommended.] 
 
Everything is working just fine with Ubuntu 9.10. I also installed the 'ubuntu restricted extras' and can watch DVD movies and You Tube videos.. everthing just as advertised.    During the installation, after prompting me first, Ubuntu 9.10 even copied over My Documents from Windows7 including the fantastic wallpaper of what looks like a California rocky coastline.  Nice Setup feature!
 
What this excersise in installing and re-installing has found out: 
#1 The new restricted video driver, once installed, solves all the problems I've had. 
#2 Lucid Lynx 10.04 (Ubuntu and Xubuntu) are both so allergic to the NVIDIA default drivers that my system cannot connect to the internet, view CDROM or USB thumbdrive, or even copy over the NVIDIA driver into the Download folder, so that 10.04 can load the recommended driver to become stable, which I think would happen if it could be installed.
 
PS- I had written that the processor in this machine was an 'Intel-Core2-Quad' but turns out it is an 'Intel-Core-i5' [with four processors-- slightly different and newer]. That was the only mistake regarding hardware. Also, the exact motherboard model is ASUS P7P55D and the video card is an NVIDIA model 8400GS. Two hard drives and two DVD RW drives and a ViewSonic 24" VX2433wm monitor supporting 1080p.
 
My goal is still to get a working Lucid Lynx installation.   I may chose the Xubuntu edition since the XFCE seems to be arranged more logically with settings and such, probably because I'm more familiar with it.

---

### Post by markMDW on 2010-06-03
new Question:  ubuntu 9.10 is working just fine on my new computer but I'm thinking about experimenting again and attempting to 'upgrade' to 10.04.  Will the upgrade overwrite the proprietary driver for my NVIDIA video card?  Or, will it keep the current driver configuration?  If it overwrites the proprietary driver then I think that would lock my system up like before [read thread].
 
Thanks for your answer!

---

### Post by markMDW on 2010-06-07
[SIZE=2]Problem solved. I now have Ubuntu 10.04 installed and operating perfectly on my new machine. The "upgrade" solution worked. [The restricted proprietary video driver I had installed for 9.10 did not get erased during the process and as a result the system doesn't lock up and the monitor works.]
 
Here's a consise synopis for the benefit of others. 
 
HARDWARE:
Intel core i5 [not Core-2-Quad as previously mentioned];
ASUS P7P55D motherboard
NVIDIA GeForce 8400 GS video card
Viewsonic 24" 1080p type monitor
4GB RAM, 2 Hard drives, 2 DVD RW Drives
USB Mouse, USB Keyboard
 
PROBLEM: could not install Lucid Lynx succesfully. 
A-- WUBI install method caused monitor to go to sleep with no input signal being received everytime I tried to run 10.04.
B-- Live CD: 
1> from 'nomodeset' bootup, within a few minutes the keyboard would lock up and although I could manuver the mouse cursor across the screen, clicking was useless.
2> without 'nomodeset' system would lockup before full bootup or monitor would go to sleep with no input signal received.
C-- Installing from Live CD with the nomodeset set option also caused the same problems listed above.
 
WHAT WAS LEARNED: 
A-- with Lucid Lynx 10.04 the default installed video driver caused the system to become instable and lock up within minutes, even using 'nomodeset' which boots into lower resolution graphics. Wired Internet connections did not work at any point, even before the lockup. From CDROM and USB FLASHDRIVE (or THUMBDRIVE) I also could not copy an already downloaded proprietary linux video driver recommended by the manufacturor to the download directory, or anywhere in my directory structure, apparently because the entire system was not stable. And with no successful internet connection that meant that every attempt at installing ubuntu's recommended but restricted and proprietary video drivers failed. 
B-- with Karmic Koala 9.10 I discovered that the system would work a little better in the 'nomodeset' low resolution graphics than with lucid lynx 10.04. As a result I overwrote the inoperable version of 10.04 with 9.10. With 9.10 installed my CDROM and USB Flashdrive was navigatable with the File Manager. Most importantly my wired internet connection worked. Still, I had but a few minutes each boot session to work until the keyboard would lock up and mouse clicks became useless. In that time period I installed the restricted video driver recommended by Ubuntu and from that point on the system worked perfectly (with 9.10).
C-- With a perfect working version of 9.10 I figured there should still be a way to aquire a full working version of 10.04, and getting that version installed and operating was still my ultimate goal. But I kept 9.10 installed for a little while since it worked so well and I was afraid that using the upgrade option would overwrite and erase the solution, that being the restricted proprietary video driver.
D-- The upgrade from 9.10 WORKED WITHOUT ANY PROBLEMS, and apparently did not overwrite the proprietary video driver.
 
THE SOLUTION FOR ME (to get 10.04 installed)
A> Install 9.10 from Live CD iso.
B> Boot using 'nomodeset' into lower resolution graphics which buys a few minutes of operational time before the system locks up.
C> Immediatly upon bootup go into SYSTEM and DRIVERS and download the recommended restricted video driver for my NVIDIA video card. (The system works perfectly from this point on)
D> UPGRADE to 10.04 (the proprietary video driver does not get overwritten/erased).

[/SIZE]

---

