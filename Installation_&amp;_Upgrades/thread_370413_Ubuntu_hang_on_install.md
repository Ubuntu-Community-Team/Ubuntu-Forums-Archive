---
title: "Ubuntu hang on install"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by godswill65 on 2007-02-25
First time user to ubuntu.  Tried to search through the forums but didn't bring up much.

My setup:

AMD64 3200
1 gig ram
1 80g wd hard drive
ati x800xl 

Tried ubuntu x386 and the am64 version.  When I boot from the CD, I hit "start and install ubuntu".  With default settings the screen goes black and i get no signal.  When I set the video to "VGA" or "640x480" or anything else I get the scrolling Ubuntu screen with the progress bar.  That will go for a minute or so and then either stop at that screen or give me a black screen.

Any ideas?

Thanks.

---

### Post by Kateikyoushi on 2007-02-25
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

If still a no go I would recommend the alternate install cd, which is text based so should work with your VGA, then you can install the driver after you finish the system installation.

---

### Post by godswill65 on 2007-02-25
sorry, yes, I've tried video safe mode as well

---

### Post by Kateikyoushi on 2007-02-25
Yes, I figured that out so I changed my post.

---

### Post by godswill65 on 2007-02-25
I'm not quite sure how to implement those boot lines you gave me.. when i hit F6 it pops up with one single line of white text .. i tried putting those in the same line as the other stuff with spaces seperating but still had the same problem .. black screen..

where can i get this alternate install?  and how hard is it to install graphics drivers when i do finally get into ubuntu?

---

### Post by Kateikyoushi on 2007-02-25
Just scroll down on any ubuntu download page and you will see after desktop and server the alternate install CD. For example, but choose your closest mirror.[LINK]("http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/")

I do not know how hard is the install because I do not own an ati card but installing nvidia was fairly easy. Check other people's experience here. [LINK]("http://ubuntuforums.org/showthread.php?t=361240")

---

### Post by Think first on 2007-02-26
It has to do with the driver for your graphics card "out of the box" that does not support your card. One solution can be found here:
[http://www.linuxmint.com/forum/viewtopic.php?t=1278](http://www.linuxmint.com/forum/viewtopic.php?t=1278)

Works for all Ubuntu and Mint is Ubuntu with a nice taste

Possibly you could install the drivers from the root prompt, but you might not have an internet connection thus "apt-get" would not be an option

---

### Post by godswill65 on 2007-03-05
If i have an internet connection how would I go about doing the apt-get?

I have done the following..

1. booted up 6.10 and hit f6
2. changed "quiet splash" to "break=bottom"
3. chroot /root nano /etc/x11/xorg.conf
4. looked for the line "driver" to scroll to
5. changed from ATI to "radeon" and to "vesa"

Radeon didnt' work at all.

Vesa brought me to a blue ANSI color'd screen which said it wasn't able to load the GUI.

My next install attempt will be with the alternate isntall cd i guess.

---

### Post by godswill65 on 2007-03-05
nevermind .. got it working!

thanks for the help!

---

