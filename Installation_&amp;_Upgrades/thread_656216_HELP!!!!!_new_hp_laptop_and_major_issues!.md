---
title: "HELP!!!!! new hp laptop and major issues!"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by ginnie6 on 2008-01-02
I've read the stickies and I still can't get this thing running. HP dv9610us with nvidia geforce go 7150m graphics card. I finally got the computer to boot by adding the noapic at the start....now I get a message that says  bcm43xx: Error: Microcode "bcm43xx_micircode5.fw"  not available or failed. 

I've tried using the regular cd, the alternate and feisty. Had I realized there were such issues with HP laptops I would not have bought one but I can't return it so I'm stuck.

---

### Post by gfd_2 on 2008-01-02
Not sure if the dv9610us  is an Intel based 64 bit system like my dv6633us with an internal card that uses the bc43xx driver but if it is you are in trouble.... the install went smoothly (about a dozen reinstalls as I wanted to make sure I was working with a clean version of 7.10 while trying to get wireless running and I never had a problem with the install). 

However, I've spent the better part of a month trying to get sound and wireless to work.  I was able to get sound working after running two scripts... if you search you can find the scripts that worked fine for me.  

As far as wireless - forget it - using the restricted driver would activate my wireless card but I could not connect to my network.    Using ndiswrapper (versions 1.49 through 1.51) would remove wireless as an option in Network  Manger just leaving Wired and Modem.     

I'm back to Vista - thankfully the HP came with 2 Gig of RAM and with the dual core processors it runs fast enough for me. I was able to connect after the folks at Verizon upgraded the firmware on my modem.   

I tried two more installs- one with ndiswrapper-1.51 and a second with using the restricted driver and ran into the same problem.  

Hopefully some distro will come up with a way to support wifi cards in the  upcoming months... if so I'll jump on board. 

Good luck!

---

### Post by ginnie6 on 2008-01-02
its amd based......I do not want to run vista. Tried it and hate it so this is not encouraging. I wonder if xp will run on it? If I've got to do winodws I'd prefer that.

---

### Post by ginnie6 on 2008-01-02
?

---

### Post by firecat53 on 2008-01-02
Don't give up! I have an HP and have had good luck booting with 'noapic irqfixup'.

For wireless....
First
1. sudo modprobe -r bcm43xx
2. sudo gedit /etc/modprobe.d/blacklist -- add to the end
    # bcm43xx -- ndiswrapper instead
    blacklist bcm43xx

3. Download the 32 bit wireless drivers for your machine from the hp website, and extract them to your home folder.

4. Install ndiswrapper-common and ndiswrapper-utils-1.9

5. cd into the directory with the extracted windows wireless drivers.

6. sudo ndiswrapper -i bcmwl5.inf

7. sudo modprobe ndiswrapper (you should see your wireless light go on - change from orange to blue if it's like our HP's -- make sure the switch is ON!!!!!)

8. Now network manager after a minute should give you the list of wireless networks.

Sound worked on both our HP laptops out of the box -- just make sure the volume is unmuted (double click on the volume control to open the complete volume control)

Good luck!

Scott

---

### Post by wolfen69 on 2008-01-02
if all else fails, you could always try another distro.

---

### Post by ginnie6 on 2008-01-02
> **wolfen69 said:**
> if all else fails, you could always try another distro.

LOL! today I've spent ALL day working on this computer....so far I've tried mepis, fedora, pclinuxos and all versions of ubuntu. I also downloaded, suse, debian, and knoppix but haven't tried them yet. As of right now I have ubuntu running .....no restricted drivers or wireless yet though. I'm almost scared to try them in case I loose what I've got. I can live with this for awhile i think.

---

### Post by firecat53 on 2008-01-03
Give ndiswrapper a try!! If you follow my instructions, or one of the several wiki articles about it, it should work! The hardest parts are finding the right drivers to download from the hp site and making sure the bcm43xx drivers are NOT loaded when you use ndiswrapper. 
To check that:
  lsmod | grep bcm43xx
 and to remove them, as I said above:  sudo modprobe -r bcm43xx.  And make sure it's blacklisted so it won't reload them on the next reboot. If you mess up with ndiswrapper, it's very easy to uninstall, remove the /etc/ndiswrapper directory and start over.

Try it! A ltitle command line work is good for you :)  It's well worth it!

Scott

---

