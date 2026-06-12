---
title: "Dualbooting rock &amp; hardplace!"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by cinnamonbuntu on 2008-04-15
Well, heres my problems as of today:

I was setting up a dual boot with Vista pre-loaded and Ubuntu being fresh install (gutsy).
I'm new to Linux in general, but O M G I looooooove linux. I set everything up on the windows side, changed my partitions to Fat32s since I wasn't getting my NTFS recognized. Everything was smooth on the vista side (believe it or not), and on my linux side with LiveCD. SO! I went on about 5 different guides for dual boot installs, printed em out, read through, highlighted, checked reviews and reactions to each. Pick the best 2, and went with the most relevant steps from each. I checked my CD integrity, got 100%. Started installing Linux into a seperate partition from the Vista partition that I had set as read only. Heres where the trouble begins, and I can't even figure out why. I had an ext3 partition, and a 2 gig swap. I started the install, was told the information on each of the new partitions would be lost. "No Problem!" I thought, there wasn't anything in either of them anyway! Well, I got the full install done, there was quite a few errors that I'm still working out. Wireless being one of them (I have that RTL-8185 card that no one likes), and I went to the grub to boot in Vista. Much to my dismay. My Vista partition has somehow been corrupted. Its visible from Ubuntu (though obviously unexecutable), and when I finally forced a Vista boot I got a very succinct, and straight forward error "No Operating System Found". Basically, I'm going to wipe this laptop, and get Vista put back on while its still under warranty, then try again. So heres a few questions in hopes my next attempt goes more smoothly.

1. How do I format my entire hard drive right now so that its totally clean?

2. What did I do wrong if you can tell from the string of run-on sentences above?

3. Should I wait and go with a Hardy install instead? or will I have more luck learning on an established version such as Gutsy?

---

### Post by kutjara on 2008-04-15
Before you reinstall Vista, have you tried using your Vista CD (or the recovery disks that came with your PC) to repair your Vista installation? The repair facility works pretty well, and can fix a number of common problems. It's probably worth doing since it might save you having to go through a total Vista install.

---

### Post by ToySouljah on 2008-04-15
You can run your Windows Install DVD/CD and when it asks which drive you'd like to install in on you can delete all the partitions that you have on there and it will combine them to form one large drive.  Now you can create new partitions depending on how you want to set them up.  I personally make my OS partitions small (enough for OS, Installed programs, and a little for slight breathing room) and leave more room for storage.  My Windows partition is 50GB, My Ubuntu is 30GB (/), I have a shared storage partiton (for both OS's) of 320GB, 110GB (/home), and a 1GB swap.  

From there try this[ link]("https://help.ubuntu.com/community/WindowsDualBoot")

Hope that helps  :)

---

### Post by cinnamonbuntu on 2008-04-15
ah! my bad guys guess I should've mentioned this before. This is a store bought laptop. No recovery CD/DVD or Install CD/DVD come with em anymore. I have to either take it in to the shop, ship it into the manufacturer, or buy one. The excuse that Gateway used was that they put all the recovery tools needed on a seperate portion of my hard disk, which was partitioned as Recovery, and set to read only. Of course all this is true, however since I installed ubuntu that portion of my hard disk is for unknown reasons, totally wrecked.

And as far as buying anything for Vista, as far as I'm concerned its the just the world's prettiest turd, and no amount of diamonds, or platinum, or gold can cover the smell. So why would I pay money for a turd.

Thats right folks, Vista=Jewel encrusted turd.

---

### Post by cinnamonbuntu on 2008-04-16
BUMP

Ok so I procured a Vista home recovery CD from a friend, and when booted it told me theres no Windows OS on my HDD. SO! Esentially this computer is completely clean except for an attempted Ubuntu install last night that went bad, because of a bug. How would I remove this partial install to try again?
 
As far as the vista issue I'm just sending it to the manufacturer, but until the mailer gets here I might as well try to learn how to run Ubuntu! BTW gonna go with a heron install. Anyone know where to snag a good ISO for this? all the Gutsies I've grabbed have been bad at 62% of CD continuity check.

---

### Post by tommcd on 2008-04-16
> **cinnamonbuntu said:**
> BUMP
As far as the vista issue I'm just sending it to the manufacturer, but until the mailer gets here I might as well try to learn how to run Ubuntu! BTW gonna go with a heron install. Anyone know where to snag a good ISO for this? all the Gutsies I've grabbed have been bad at 62% of CD continuity check.

You can download Ubuntu Hardy Heron beta from here:
[http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)
I don't know why your Gutsy downloads are bad. You should be able to download a good Gutsy from any Ubuntu mirror:
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
For checking the integrity of your Ubuntu downloads on Windows:
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)

---

### Post by cinnamonbuntu on 2008-04-16
Snagged one of each, got a good Gutsy finally. Something was corrupting my ISOs on my end I think. Had a buddy burn me a copy of each. They worked! So now I have a fresh install of Gutsy, and I might try out Hardy later tonight after I mess with this for a bit. One thing I noticed though, is that the alternate install didn't give me Gparted or a wireless management utility like the Live CD did. Anyone know how I can get one while on windows and get it to Ubuntu?

---

### Post by tommcd on 2008-04-17
> **cinnamonbuntu said:**
>  One thing I noticed though, is that the alternate install didn't give me Gparted or a wireless management utility like the Live CD did. Anyone know how I can get one while on windows and get it to Ubuntu?

The alternate install CD should have given you the same packages as the live CD. Do you have the gnome networking utility
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
If not, use "ifconfig -a" to see all of your network interfaces. If you have a wlan0   you can set it up with iwconfig:
sudo iwconfig wlan0 essid your_essid (to associate with your router's essid).
sudo iwconfig wlan0 key your_encryption_key (for WEP encryption).
WPA is a bit more complicated, see this:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
If you don't see a wireless interface with "ifconfig -a", run lspci to see  what wireless chipset you use. It should be near the end of the output. Depending on what wireless chipset you have you may need to enable a restricted driver (atheros) or use ndiswrapper to use the Windows driver in Ubuntu.

---

