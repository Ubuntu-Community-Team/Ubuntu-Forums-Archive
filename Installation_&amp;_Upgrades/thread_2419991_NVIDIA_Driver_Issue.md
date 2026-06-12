---
title: "NVIDIA Driver Issue"
date: 2019-05-28
forum: Installation &amp; Upgrades
---

### Post by carmello6769 on 2019-05-28
Hi Everyone,

I'm installing ubuntu 19 and I'm running into an issue using the NVIDIA driver. I've tried installing two ways, by either checking off the proprietary software checkbox at the beginning of the install, or waiting until after the install has finished and done it through the software updater. Either way, once I try to boot the system after the drivers have been installed I never make it to the gui. It hangs at "Starting Authorization Manager".

If it helps I'm using an RTX 2070.

Thanks!

---

### Post by verlinanderson2 on 2019-05-28
I'm not much help. I'm typing this to hopefully follow the thread and gain the solution. I am likely to have the same problem using my Dell XPS15 when I shift it to using Ubuntu. Hopefully my addition will help someone else see the posted request too.

---

### Post by rbmorse on 2019-05-28
If this is a UEFI machine, make sure secure boot is disabled in the UEFI setup.

---

### Post by carmello6769 on 2019-05-28
I took it off of secure boot. I got slightly further to "rotate log files". 
[https://imgur.com/a/i4mO8Az](https://imgur.com/a/i4mO8Az)

---

### Post by rbmorse on 2019-05-29
I'm not sure you have a video driver problem, but whatever it is is beyond my ken. Perhaps someone more knowledgable will chime in.

---

### Post by carmello6769 on 2019-05-29
Ok well thank you for trying though

---

### Post by oldfred on 2019-05-29
That is a very new card, did you add the ppa to get the very latest nVidia drivers?
And if an older driver installed, you must purge that before installing newer one, or else you get conflicts.

#What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia
nvidia-smi

nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)

# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
This will show the defaults with the Ubuntu repository for Ubuntu version.
ubuntu-drivers devices

Info on ppa
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update

# If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa

Now list includes newer drivers from ppa:
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by Autodave on 2019-05-29
Do what oldfred told you and you should be good.  I am running the RTX 2070 here with no issues.  You will need to add that repository.

Not sure what version of 'buntu you are installing.  If it were my machine, I would be doing the LTS (long term service) 18.04.  That way, you will not have to upgrade every 6 months and possibly run into this issue again.

---

### Post by rbmorse on 2019-05-29
The 2070RTX is supported on 19.04 with the Nvidia 418 driver installed by "additional drivers."   According to the documents, anyway. I did a clean install with 19.04 and the installer picked it up automagically. 

Adding the .ppa shouldn't be necessary, but now that you've disabled secure boot, purging the driver and reinstalling as indicated should help.

---

### Post by carmello6769 on 2019-05-31
Unfortunately the directions didn't work for me. I've tried doing fresh installs, using nvidia-driver-418 and 430 with the updated repositories and still no dice. The system only wants to work with the noveau driver.. if it helps I'm just using straight ubuntu and not another distro based off it.

---

### Post by rbmorse on 2019-05-31
Don't go away.  I'm getting a 2080 this afternoon and I'll try to slap it into the box this evening.  It will be replacing a 970GTX that's working fine with the 418 driver, so I'll be real interested to see if the RTX card will just plug 'n play.

---

### Post by rbmorse on 2019-05-31
I'm finding this very curious. I just did the hardware swap (don't forget about the release tab at the rear of the PCI slot!) and 19.4 came up on the 2080RTX without problem, using the 418 driver that was working with the previously installed 970GTX. 

Purge the Nvidia drivers per above and bring the machine up on the nouveau driver. 

What happens when you select applications > software and updates > additional drivers?  Is the video card properly detected? Do you have the option to select one (or more) proprietary drivers?

---

### Post by carmello6769 on 2019-06-09
Hey just wanted to make an update to this. I tried the install on another drive(just by chance I wanted to use an SSD instead of the HDD I was using) and everything is running no problem today! Thanks to everyone on here for their input.

---

