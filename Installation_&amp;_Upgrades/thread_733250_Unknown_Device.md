---
title: "Unknown Device"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by qaissi on 2008-03-23
Ok I am relatively new to this so hopefully I will not seem too silly.

I am trying to install Ubuntu 7.10 on a Toshiba Satellite A70.

Mobile Intel Pentium 4 2.80 Ghz with ½ gig of shared memory and an ATI Radeon 9600 viedo card.

I am very used to using Windows and so of course I checked the Device Manager to ensure that everything is working properly.  That is where the problems begin.

I am sort of used to dealing with “Unknown Devices” but of course as I found out from this forum the Device Manager in Ubuntu is more a matter of displayed information then it is actually a Device Manager.  So now that it opens with a number of things displayed as being Unknown Devices I am not sure what to do next.

The only real symptom that I have noticed so far is the irratic behaviour of the audio card which shows as an IPX150 and as a constant source of problems with Ubuntu.  I can get sound when I boot into Ubuntu but nothing after that.  If I go to System – Preferences – Sound – everything is set to auto but when I try to test anything I get no sound and I can not close the test window or the sound window and have to reboot – no force close appears.

I have tried searching for “Unknown Devices” all over this forum and of course come up with all sorts of issues that do not relate to the general question of how do you detect and resolve an “Unknown Device” issue in general.

So some assistance would of course be greatly appreciated.

---

### Post by Pumalite on 2008-03-23
Post:
lshw -C sound

---

### Post by qaissi on 2008-03-23
Thanks for the assist

  *-multimedia            
       description: Multimedia audio controller
       product: IXP150 AC'97 Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.5
       bus info: pci@0000:00:14.5
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master
       configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp

---

### Post by Pumalite on 2008-03-23
Good news. Your kernel recognizes the card and loads the module. At the Terminal:
alsamixer
If you get a picture with settings; set them all at 100%
If not; post the output here.

---

### Post by qaissi on 2008-03-23
Everything set to 100% for all I can get to.  Tried the Sound Preferences and when I hit the Test button it locks up again.

I am not convinced that this is solely a sound card issue.  As I said there are a number of things showing in the device manager as unknown devices any of which might be the problem.  

Of course I am will to try anything at this point.

---

### Post by Pumalite on 2008-03-23
You might have to compile the latest alsa-driver. 16 I think it is.

---

### Post by qaissi on 2008-03-23
Fine - and how does one go about doing that?

---

### Post by Pumalite on 2008-03-23
Your alsamixer looks fine
As for the driver, I have something written down. Just replace the 15 for 16 and where corresponds, intel for ati:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=auto

Save the file, close it, reboot, and CROSS YOUR FINGERS!

---

### Post by qaissi on 2008-03-24
Well that was fun - not!  Anyway this is the code as I converted it and it seemed to run without any problems:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)
sudo tar xjf alsa-driver-1.0.16.tar.bz2
sudo tar xjf alsa-lib-1.0.16.tar.bz2
sudo tar xjf alsa-utils-1.0.16.tar.bz2
cd alsa-driver-1.0.16
sudo ./configure --with-cards=hda-ati
sudo make
sudo make install
cd ../alsa-lib-1.0.16
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.16
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-ati model=auto

My symptons now are this:

The Volume Control at the top of the screen is now muted out and when clicked reads: No volume control GStreamer plugins and/or devices found.

When booting I now get a line that reads: GREP :/Proc/Asound/Cards: No such file or directory

lshw -C sound now gives me

  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: IXP150 AC'97 Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.5
       bus info: pci@0000:00:14.5
       version: 00
       width: 32 bits

       clock: 66MHz
       capabilities: bus_master
       configuration: latency=64 mingnt=2

And of course the alsamixer command gives me alsamixer: function snd_ctl_open failed for default: No such file or directory.

So where can I go from here besides the obviouse to H--L :)

---

