---
title: "Upgrade from 12.10 to 13.10 via Command Line?"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by Digitalscribbler on 2013-10-18
I currently have Quantal Quetzal (12.10) and I'd like to upgrade to Saucy Salamander (13.10) via the command line. I know I can do this via the Software Center, but I'm interested in learning how to do this through the Command Line. After doing a little research, it looks like these are the commands that I need to enter. Is this correct? Thanks.


> 
sudo apt-get install synaptic
sudo apt-get update && sudo apt-get dist-upgrade
sudo update-manager -d  

---

### Post by MadmanRB on 2013-10-18
Yeah the command is correct.
However if you have a CD or USB you can upgrade Ubuntu via that too without a reinstall.

---

### Post by grahammechanical on 2013-10-18
Actually we cannot upgrade from 12.10 to 13.10. We have to upgrade to 13.04 first and then on to 13.10. and I do not think that we need to install Synaptic Package Manager either. Synaptic is a front end for the apt-get tool. It combines updating with software installing which are separate utilities in Ubuntu.

Regards.

---

### Post by newb85 on 2013-10-18
+1 grahammechanical

---

### Post by fantab on 2013-10-18
> **Digitalscribbler said:**
> I currently have Quantal Quetzal (12.10) and I'd like to upgrade to Saucy Salamander (13.10) via the command line. I know I can do this via the Software Center, but I'm interested in learning how to do this through the Command Line. After doing a little research, it looks like these are the commands that I need to enter. Is this correct? Thanks.

Those commands will only take you to 13.04 as grahammechanical points out. **IF**, and its a big 'if'**,** all goes well, then you will have to run those commands again to take you to 13.10. 
If I were you I would clean install 13.10 after removing 12.10, it would save me lots of time, trouble and the install will be cleaner without any issues.

---

### Post by Digitalscribbler on 2013-10-18
Thanks everyone for your help :)  

@fantab - to reinstall - can I do this from the Terminal - e.g., "sudo apt-get install ubuntu-desktop"? Thanks

---

### Post by sandyd on 2013-10-18
moved to installation and upgrades

---

### Post by fantab on 2013-10-18
No. Download and burn ubuntu 13.10 to a DVD/USB and install.
sudo apt-get install ubuntu-desktop will only install ubuntu-desktop for the same version ie, 12.10.

---

### Post by Digitalscribbler on 2013-10-18
@fantab Thanks

Got it installed. For anybody else who might be in the same situation ....
1. I created a bootable USB (I've got an Aspire One netbook) via the Linuxpendriver
2. Then rebooted and selected F2>Boot and put the USB as the top-level boot drive
3. Then saved the settings and exited F2
4. Then rebooted and followed the installation prompts.
5. Enjoy 13.10!

---

### Post by newb85 on 2013-10-19
A clean reinstall cannot be done from within the system.  You would need to boot from a live DVD/USB for that.

Edit: Oops, should have refreshed the page before responding.  It looks like you've got it!

---

