---
title: "Ubuntu Installation Freezes Early On"
date: 2017-01-19
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2017-01-19
I'm trying to install 16.10 via a thumb drive I configured using Rufus. I'm using the following hardware:

Asus X99-A USB 3.1 motherboard
Intel i7 6850K cpu
Asus Geforce GTX 1080 Strix video card
64 GB Kingston HyperX RAM
1 1 TB Samsung SSD
1 500 GB Samsung SSD
1 4 TB WD HDD

One of two things happens. One:  The system boots to the GRUB screen and I select "Install". I get a graphical screen with "Ubuntu" displayed in the middle and animated dots indicating there's activity. Then, the animated dots stop and the install goes no further. I see the thumb drive light flash a few times beyond that but nothing happens after.

Two:  The system boots to the GRUB screen and I select "Install". The screen flickers a few times and I get lines of text in the upper, left-hand corner of the screen. Several lines appear and then installation stops, just like it does when I get the graphical screen. I see the thumb drive flash a few times but it stops and nothing happens after that.

Also, if I "try" Ubuntu before installing, I get a very bad display and no ability to use the mouse. The desktop is duplicated side-by-side on a single screen (squished together and kind of garbled looking) and I appear to be able to tab through icons but hitting the "enter" key does nothing.

---

### Post by #&amp;thj^% on 2017-01-19
I have not had good luck with Rufus installs...
You could try to burn again with another tool.
And you should always check the source with md5sum.
This tool works just great with all Debian based installs: [https://ubuntuforums.org/showthread.php?t=1958073](https://ubuntuforums.org/showthread.php?t=1958073)

---

### Post by Kerry Lange on 2017-01-19
Hey, thanks for your response. Rufus has worked for me before a number of times. However, I'll try with another tool to see if that works.

---

### Post by oldfred on 2017-01-19
Some find it easier to install using just Intel Video.
Then install the nVidia drivers & switch to nVidia output.

It may work with nomodeset
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

And you will need to install the ppa to get the very newest nVidia driver. Do not install directly from nVidia.

This was a Gigabyte board, so different settings.

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648) 

      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   [http://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413](http://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413)
# Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 

 Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by Kerry Lange on 2017-01-19
Hi,

Thanks! I'll give this a try when I get home this evening.

---

### Post by Kerry Lange on 2017-01-20
> **oldfred said:**
> 
It may work with nomodeset
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.


oldFred, nomodeset was key for completing the installation. I ran into a boatload of other issues after that but I was able to install and now I'm up and running. Thank you for your help!

---

