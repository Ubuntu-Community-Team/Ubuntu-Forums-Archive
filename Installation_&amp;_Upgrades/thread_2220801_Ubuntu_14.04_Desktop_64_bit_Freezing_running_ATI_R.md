---
title: "Ubuntu 14.04 Desktop 64 bit Freezing running ATI Radeon 8350 series card"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by hitekwaiter-j on 2014-04-29
*note I posted this yesterday in another section, but I guess I used the wrong area*
      About 2 weeks before the 14.04 official release, I downloaded (and, yes donated a little) to get 13.10 desktop 64, which I installed on a
     fresh hard drive from scratch.
     I had a lot of problems with the display and screen frezzing up (no response, no errors, just frozen)
     I found that my graphics card responds better with the open sourced drivers (not amd/catalyst)
     Since 14.04 (note, the proprietary drivers work better in my dual installation of 12.04)
     I have updated my 13.10 Ubuntu desktop 64 bit to 14.04.
 

     I have also run an
     apt-get install gnome
 

     ***I NEED to know the command to switch display managers from the root promt in recovery mode***
     I was promted and decided to change to GDM (gnome display manager) welcome screen, but I find Gnome is Worse for the screen frezze problem, so I select Unbuntu/unite
 

     Note: I'm not running the proprietary ATI/AMDFGLRX GRAPHICS DRIVER for my amd graphics card
     that makes the problem worse.
     ****NOTE******
     over 12 hours later. Had to go to work. Got back...left out some stuff****
     ************************************************** ******************
     Hardware info.
     the command
     sudo lshw -C video
     yields:
     description: VGA compatible controller
     product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
     vendor: Hynix Semiconductor (Hyundai Electronics)
 

     NOTE: this is from the XORG i have running on the same PC, from a different Harddrive (yes, i have a lot of hard drives)
 

     I know its a ATI Radeon 8350 series card
     I'm only running the open source driver on my 14.01 side.
 

     Changing to Gnome (classic) desktop help, but I just got another crash/frezze
 

     The card IS listed amongst the fullly supported video cards.

---

