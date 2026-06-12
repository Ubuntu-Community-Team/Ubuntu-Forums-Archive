---
title: "Ubuntu 8.04 on Alienware m5500 with x1400"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by dusted on 2008-11-07
Hey everyone, just posting my success story.  Just installed Ubuntu 8.04 to a 13GB partition with a 2GB swap area alongside my 105GB WinXP install.  I made this choice after a successful 4 month run with Ubuntu 8.04 through Wubi.  Here are my systems specs followed by the installation details.

Notebook
Alienware m5500-r3
T7400 Core 2 Duo 2.16GHz
4GB Ram
- Corsair 2GB PC6700 x2
128MB ATI X1400 Mobility Radeon
120GB 5,400 RPM Hardrive
- 105GB NTFS Windows
- 2GB Swap Area
- 13GB ext3 root
Extra buttons
- Media player
- Internet
- Mail
- Stealth mode
- Power button
- Lid close switch
- Function + volume/brightness/mute/sleep
Internal Wireless ABG
Wireless switch
Gigabit 10/100/1000mbps NIC
DVD-RW Drive
Speakers

All of the above work flawlessly including the media keys.  They can be set through System > Preferences > Keyboard Shortcuts.  The stealth mode button throttles CPU0 back to 1GHz regardless of what mode your power saving is set to.  The wireless switch on the front of the laptop works fine, even better than in Windows.  The Gigabit NIC works on a 100mbps network at my college, I have yet to try it on a 1000mbps network.

The volume adjustment jog dial on the side of the laptop does not function.

The built-in SD card reader works as expected but I have not tried other forms of media in it.  It supports MMC and a couple other cards in Windows, yet to be tested in Ubuntu.

Touchpad works out of the box as well as the wireless.  The touchpad supports vertical and horizontal scrolling as well we tap-to-click.  The touchpad power button also works for turning off the touchpad for when you plug in a USB mouse which has been tested to work fully.

The function buttons works alongside the volume up/down, brightness up/down, and mute buttons and these changes are shown up in on-screen-displays in Gnome.  Screen brightness is now also controllable from power management software.

I have successfully used all of my flash drives and SD card readers and Portable hard-drives with no problems.

Suspend-to-ram works as expected as well as locking screens.  I have not yet tried Suspend-to-disk or Hibernate yet in fear of something going wrong with my working set-up.  As I have not tried the following as I have no need for them:
- External display
- S-Video Out
- Headphone and Microphone jack
- Mini Firewire
- Express card

I have tried using a Rocketfish Bluetooth 2.0 USB dongle and a set of Logitech USB speakers, both of which are recognized by Ubuntu but do not function.


As for the actual installation itself, it was painless, I defragged Windows using jkdefrag and Disk-keeper 2008 then proceeded with the Ubuntu installation.

Put the CD in the drive, reboot, check for defects, Install Ubuntu option from the menu and followed the installation windows.  Choosed Manual partition set-up, resized Windows partition and made it smaller by 15GB, made a 2GB swap area and a 13GB ext3 for root.

After the installation upon logging in, let the update-manager run, updates were about 170MB, rebooted my computer, ran it again, updates this time were about 260MB, rebooted my computer.  I then enabled the fglrx driver in System > Administration > Hardware drivers.

I then went into System > Administration > Software Sources and enabled the Proposed updates on the  tab and ran System > Administration > Update Manager once more and did a final update.

I then went on to install the following packages:
- fusion-icon
- compizconfig-settings-manager
- emerald
- kpowersave
- virtualbox
- wine
- amarok
- ntfs-3g
- deskbar-applet
- freebasic(guide for this can be found at bottom of post)

I then proceeded to mount my windows drive by running the following commands:

sudo -s
mkdir /host
ntfs-3g /dev/sda1 /host -o force

Note: I have not yet figured out how to make the mount permanent to upon login you may have to run "sudo ntfs-3g /dev/sda1 /host -o force" and enter your password before accessing the windows drive by going through the /host directory.

I then ran the following commands to enable access to the wubi installation of Ubuntu.  I did this to access my old home folder and copy the directories: .themes .fonts .icons .emerald
This was so that I could keep my old settings and appearance settings along with any documents I saved on the Wubi install.\

sudo -s
mkdir /wubi
mount /host/ubuntu/install/disks/root.disk /wubi -o loop

Note: Same as above, you will have to remount this after logon and AFTER mounting the ntfs drive.  Run "sudo mount /host/ubuntu/install/disks/root.disk /wubi -o loop" after logon.

After that basic set-up came all the customizations to Ubuntu such as the 3D cube, wobbly windows, appearance effects, adding Aerofox, Greasemonkey, Stylish, and Fastdial to Firefox and changing a few themes in different programs.

One major note is that any program running OpenGL or WINE program using DirectX needs to be run without Beryl.  You can run the program but the graphics will be all glitched if you don't first select Metacity as the window manager and Reload the window manager.  This can be done from the fusion-icon which can be access from Applications > System Tools > Compiz Fusion Icon which loads it into the Notification area.

I hope this helps anyone who has installation problems on there laptop, more specifically an Alienware m5500.

I have include a link to screenshots of my set-up.

[[IMG]http://s1d3.turboimagehost.com/t/924097_firefox.png[/IMG]](http://www.turboimagehost.com/p/924097/firefox.png.html)
[[IMG]http://s1d3.turboimagehost.com/t/924096_amarok.png[/IMG]](http://www.turboimagehost.com/p/924096/amarok.png.html)
[[IMG]http://s1d3.turboimagehost.com/t/924099_wow.png[/IMG]](http://www.turboimagehost.com/p/924099/wow.png.html)
[[IMG]http://s1d3.turboimagehost.com/t/924098_scale.png[/IMG]](http://www.turboimagehost.com/p/924098/scale.png.html)
[[IMG]http://s1d3.turboimagehost.com/t/924095_3dcube.png[/IMG]](http://www.turboimagehost.com/p/924095/3dcube.png.html)

FreeBASIC installation
- Go to [http://www.freebasic.net/index.php/download]("http://www.freebasic.net/index.php/download")
- Download the latest package
- Extract the package and open a terminal with root
- cd to the extracted folder and run "./install.sh -i"
- This will install freebasic
- Go to [http://www.freebasic.net/forum/viewtopic.php?t=11217&highlight=packages+ubuntu]("http://www.freebasic.net/forum/viewtopic.php?t=11217&highlight=packages+ubuntu")
- Follow the steps on that page to install the extra packages needed to compile programs
- to compile a file just run "fbc <filename.bas>" and it will create an exectuable "<filename>" in the same directory as the "<filename.bas>"
- If you have any questions about FreeBASIC sign-up at [http://www.freebasic.net/forum/]("http://www.freebasic.net/forum/"), it's a very friendly community who will help answer your questions




If you have any questions regarding my set-up, post here or drop me an e-mail to [email]james_jones_5@hotmail.com[/email]

---

### Post by dusted on 2008-11-10
I received an e-mail asking about what theme and icon set I was using.

First check out this site:
[http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/]("http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/")

Specifically, the Dark-Ice section, I installed the packages it listed there.

Under System > Preferences > Apearance I chose 'Clear Looks' to start and pressed the 'Customize' button.  Here are the settings for each tab:

Controls: Dark-Ice
Colors: Default
Window Border: Dark-Ice
Icons: Gnome
Pointer: DMZ-Black

Those will be the settings used when you have Metacity set as your window manager, in my case, I switch to Metacity using the Fusion-Icon whenever I want to run an OpenGL application.  For the emerald theme I use the Black-Centered theme on the page above, but I slightly modified it moving the buttons around a bit.  You can use the emerald theme manager to customize the theme.  If the theme doesn't change for you, just open the terminal and run:

emerald --replace&

The same goes for metacity

metacity --replace&

Then after that you just need to customize to your likings.  Read through the guide in that link, it is a good read and has a lot of good resources and themes.

---

