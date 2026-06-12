---
title: "Presario CQ57 install problems"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2011-08-05
This is a new machine(64bit 1ghz AMD processor) and I can't get either 10.04.3 or 11.04 to map out to RAM and boot from a cd.  (I will try it from a usb drive, but I seem to recall having a difficult time getting it to install in a VirtualBox from a usb drive.)

See the attached screenshot for what I get with 10.04.3 when I try to install it in a VB.  I have tried the first two alternative install options in the F6 menu (I think "noapic" and "apic=off"... not sure, but it's the top two. I'll try the rest.)

W/R/T booting from the cd at startup and selecting "Try without installing" they both "try" to paint all the graphics, but fail in such a way that nothing is discernible.

There's a gazillion of these machines in people's homes now.  I'm hoping that someone knows the secret trick for it in terms of getting Ubuntu to install in both a VirtualBox in Win7 and in a dedicated partition.

Thanks in advance,
Scott

---

### Post by sks24 on 2011-08-05
Update: I've got the machine booting successfully to 11.04 from a usb drive. Now the VirtualBox...

---

### Post by sks24 on 2011-08-09
Well, I can't get any Linux distro to install in the Virtual box on this machine.  openSUSE and the 64 bit Puppy Linux hang, and it looks like I get kernel panic with 11.04, 10.04, 10.04.3.

There are many settings in the VB, some of which I tried. So too on the Linux side with noapic options selected.

I'll probably post over at techguy.org and maybe the virtualbox forums about this.  

But any tips here would be appreciated.

I do have 10.04.3 in a dedicated partition, but no sound.  (see: [http://ubuntuforums.org/showthread.php?t=1821350](http://ubuntuforums.org/showthread.php?t=1821350))  

Thanks,
Scott

---

### Post by ipadm on 2011-12-01
Solved sound problem on Presario CQ57 by upgrading ALSA with this script (save it and run as sudo)
```


#!/bin/sh

# This script will recompile the ALSA drivers for Ubuntu
# This procedure was gotten from
# https://help.ubuntu.com/community/HdaIntelSoundHowto
#
# Authored by Bob Nelson  admin@stchman.com
#
# This script updated 9/6/2007


script_name="alsa_setup.sh"

# Script must run as root 
if [ $USER != "root" ]; then
    echo "You need to run this script as root."
    echo "Use 'sudo ./$script_name' then enter your password when prompted."
    exit 1
fi

# Install the required tools
sudo apt-get -y install build-essential ncurses-dev gettext

# Install your kernel headers
sudo apt-get -y install linux-headers-`uname -r`

# Change to users home folder
cd ~

# Get the files from www.stchman.com
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.24.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.24.1.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.24.2.tar.bz2

# make a new folder 
sudo mkdir -p /usr/src/alsa

# Change to that folder
cd /usr/src/alsa

# Copy the downloaded files to the newly made folder
sudo cp ~/alsa* .

# Unpack the tar archive files
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

#Compile and install alsa-driver
cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

# Compile and install alsa-lib
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

# Compile and install alsa-utils
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

# Remove the archives as they are no longer needed
rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

# Add the following line to the file, replacing '3stack' with your model
sudo echo -e '\n' >> /etc/modprobe.d/alsa-base
sudo echo "options snd-hda-intel model=3stack" >> /etc/modprobe.d/alsa-base

# Reboot the computer
sudo reboot


```

---

### Post by sks24 on 2011-12-02
Thank you very much ipadm.

---

