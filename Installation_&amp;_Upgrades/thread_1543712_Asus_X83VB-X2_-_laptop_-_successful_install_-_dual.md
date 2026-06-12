---
title: "Asus X83VB-X2 - laptop - successful install - dual boot w/ vista"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by texla on 2010-08-01
This is just a good installation post - let me know if this should be moved

The asus X83VB-X2 came with 64bit vista installed in a dual-core intel system w/4gb ram and firewire (4pin).  Here's how I installed a dual boot of lucid on it - btw - it was easy:

1.I used Remastersys to make a backup of my Lucid install (32bit) on my desktop.  
2. I turned on my new laptop and checked the Vista install and it was fine.  It had two partitions to the 250GB hard drive.
3. I figured I could install lucid to the second partition just fine - and it did, no problem but vista disappeared from the Grub menu
4. Using a USB flash drive, I installed my remastersys backup to the d partition on my system, using the manual install method.  I chose to use three partitions - one root (18gb) one for home (89gb) and one for swap (5gb)
5. Booted into Linux and THEN WENT TO THE TERMINAL TO RUN SUDO UPDATE-GRUB (very important if you want your dual boot to work!)

6. Then I installed a realtime kernel to record with firewire to Ardour and it went great!

notes:  I have had no problem with any hardware on this so far with lucid  - wireless, firewire, touchpad, one-touch system settings (asus has a lot of one key + fn key for changing volume, brightness whatever), nvidia video card, ethernet, and battery all working great out of the box.  Also, this is by far the easiest install experience I've had so far.  Looks like a newer system w/ a newer distro are a great mix.  Plus I saw a previous post on the forum about this laptop being a great install and that was a big influence on me so I thought I'd share some, too. 

And, Ubuntu rocks and that's that!  More later as this thing gets used in the field....

:popcorn:

---

### Post by texla on 2010-08-06
part 2

Realtime kernel notes to this install:

added this ppa here: 
[https://launchpad.net/~falk-t-j/+archive/lucid/]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/")

then added a realtime kernel:
2.6.33 (the .29 pae version)  image and headers

then added all the nvidia stuff in the ppa

(the 98 failed to install but the 173 did just fine)

then restarted and ran nvidia program in:

system - administration - nvidia x server settings

it told me to run a command in the terminal (i did not write it down but i ran it in the terminal like it suggested)
then restarted. - now all is good

---

