---
title: "Install on new Dell r320 which has no OS"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by James_Looney on 2013-09-27
Hello all,
New to Ubuntu and Dell servers - have been running apple servers for the last 8 years. So i'm comfortable with unix commands and headless administration. We just got a new Dell PE r320 which has no OS on it. I am trying to install Ubuntu and can't quite figure out the correct process.

I've downloaded and ripped Ubuntu .iso to DVD. The Dell is set to boot off the optical drive - as it boots it's own DVD just fine. However when trying to boot my ripped ubuntu, it does recognize anything on disk.

Has anyone done a similar type of install that can offer advice to a seasoned unix user who is lost on this new Dell?

thanks in advance for anyone who can assist.

---

### Post by oldfred on 2013-09-27
When you say ripped, did you just extract it which will not be bootable or install it with tools that both extract and install boot loader?
I prefer flash drives now as they are reusable and install is quicker than from DVD. And if reinstalling I use hard drive.

       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


New versions are too large for CD, but instructions are the same.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Is this system UEFI or BIOS?
Do you want gpt partitioning. Ubuntu will boot from a gpt partitioned drive with either UEFI or BIOS boot modes. Windows only boots from gpt with UEFI.
      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I use gparted to create partitions in advance from either live installer or separate download of parted magic or gparted which has slightly newer versions of gparted.        
 If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by James_Looney on 2013-09-30
Hi Fred, thank you for replying. I used the instructions for mac osx on this page: [https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Mac_OS_X](https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Mac_OS_X)

However maybe i'll try the flash drive method


Right now i believe it is just BIOS. only limited system start up when i start the machine, there are some kind of Dell management utilities available too, but no OS is installed on this thing.

I do want to partition before going live but I'm assuming I can use Ubuntu to do that after its up and running? Because all I need is to partition off 100Gb for Ubuntu and 500Gb for all the Users data that we'll have (websites and web applications).

I wont be back to this until tmorrow but i'll let you know how the flash drive goes. thanks again for your time.

---

### Post by oldfred on 2013-09-30
The Ubuntu desktop verison liveCD have gparted or other partition tools, but the server version is not a liveCD. If a server especially if RAID you need the server version. And then you may want to download partitioning tools separately. I might have Ubuntu liveCD of current version just to be able to make repairs.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by James_Looney on 2013-10-01
Ah, ok thank you again for that information. I was putting the desktop version on it so my boss would have  GUI to use when he needs to access the machine. However, I did some more reading it looks like I can install the Server version of ubuntu and then add any number of desktop environments to it - so that should work out fine. I'm trying the usb drive trick now, will post back here with my findings.

---

### Post by oldfred on 2013-10-01
The server version auto runs this, which you can install to desktop verions as an alternative.
 [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

You may not need or want full desktop enviroment, but may just want gui or Windows manager.
      
 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)

      
 Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)


 If you do not like Unity, use K/L/X ubuntu or the DE/ WM of your choice. 
Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)
What is the difference between Debian, Fluxbox, XFCE,
window managers like Icewm, Openbox, Fluxbox, and Xfwm
desktop environments are KDE, Gnome, Xfce, Enlightenment, and LXDE
Try Xubuntu (xfce), Lubuntu (lxde), Kubuntu (kde), Elementarty OS, Mint, Cinnamon, Mate, openbox, Awesome, dwm, wmii, i3, xmonad, fluxbox etc etc etc
One users comparison of versions.
[http://mylinuxexplore.blogspot.in/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.in/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html)

---

### Post by James_Looney on 2013-10-03
Thanks again for all of your help. I got a bootable DVD working finally. I got the server version installed and included the XFCE desktop for my boss. It's taking a while for me to understand the partitioning schemes but I think I finally have that all worked out with swap partition set up and an LV set up with separate partitions for the OS and for the Users data.  This has definitely been a learning experience.

Thanks again OldFred, I really do appreciate your time.
Kindest regards

---

### Post by oldfred on 2013-10-03
Glad you got it working. :)

 If you install your own system you are the system admin

        Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

