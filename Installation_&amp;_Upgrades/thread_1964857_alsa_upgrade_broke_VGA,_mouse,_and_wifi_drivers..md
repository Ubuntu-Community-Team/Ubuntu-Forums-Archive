---
title: "alsa upgrade? broke VGA, mouse, and wifi drivers."
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by HalfNote5 on 2012-04-24
Hi everyone!

I have in my hands my awesome little AAO zg5 laptop that has been cozily running Hardy Heron for a few years now. 

Last thing I REMEMBER doing that may have caused my problem was 'sudo apt-get install alsa' (to see if I couldn't grab any newer alsa drivers, and maybe get the "mix" input option. All of which, other than as a "what I was doing last," is beside the point.)

Anyhoo, now I can boot to it fine with an Ubuntu Live usb, (or, for that matter, a Mint Live, and Debian live usb,) so it's not an actual hardware problem.

During bootup, my splash screen disappears and it shows a failure on button.wifiled.0 or something to that effect, and then proceeds to load Gnome into low graphics mode with no wifi, vga, mouse our touchpad drivers. I'm assuming other stuff might be hosed, too, as plugging in a USB mouse will show under lsusb, but it won't actually be usable. :cry:

Aaaaanyhoo, I'm wondering if this is something that an upgrade (if possible) would fix, or if I should bite the bullet and just reinstall Ubuntu.  I've dumped the entire hard drive (using a live-boot to enable the wifi) to my server, so I can get everything back if I have to, but it'd be nice if something like an 'apt dist-upgrade' would fix it.

Anyone have any advice on how to proceed?  (I have no problem getting the system back to how it was from scratch, but I love knowing a simpler solution for future reference, if one is available.)

Thanks!

---

### Post by HalfNote5 on 2012-04-24
P.S.

Wired network will work, but DHCP will not - have to set IP manually. Seems like there's something pervasively and badly wrong with the system.

---

### Post by Dngrsone on 2012-04-24
Here is my script for updating ALSA drivers (in 10.04 I have to run it every time my kernel updates):

```

#!/bin/bash

# Update ALSA drivers

# Stop ALSA-Utils

sudo /sbin/alsa-utils stop

# Install necessary compiling tools

sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

# Download new ALSA driver, libraries, and utilities

cd ~
rm -rf ~/alsa* ~/.pulse*
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2

# Create folder to compile in and install from

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

# Unpack files

sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

# Compile and install Driver

cd alsa-driver*
sudo ./configure
sudo make
sudo make install

# Compile and install Libraries

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

# Compile and install Utilities

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

# Cleanup

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

echo You many now restart your computer to complete ALSA update.  Do not forget that the sound is muted by default.

```

With that said, though, an ALSA update shouldn't affect your networking at all.

It sounds to me like you need to either reinstall some networking drivers or perhaps you have a bad wifi module.

---

### Post by HalfNote5 on 2012-05-24
Yah. I had to back up my little machine's HD using a live disc, and reinstall.
Luckily, I keep system backups ; )

Thanks everyone!

---

