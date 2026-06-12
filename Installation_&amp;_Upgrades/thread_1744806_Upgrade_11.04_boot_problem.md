---
title: "Upgrade 11.04 boot problem"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by beachbuggy on 2011-04-30
Afternoon all. 

I have just finished the upgrade of the latest version and I'm at the point of my system restating. 
As I'm such a noob I didn't make a live CD and test it first :(

My system automatically tried to restart but on the restart I got the 'terminal' view. It stopped when asking for my username (it never normally asks for this before the grub menu) and then password. I didn't get any further than that. 

I now have on my screen (still in the terminal view before the grub menu)

"name@name-desktop:...$ "

I'm on my phone now so I don't actually have the symbol for before the dollar sign but your know what it is. The raised S on a 90 degree angle. 

Any help on what I am to type in now would be much appreciated. 

Collin

---

### Post by Hedgehog1 on 2011-04-30
You will need a LiveCD/LiveUSB before this is all over.

Please try typing **startx** to get the UI going.  If you can get it going, download the Natty ISO and make a LiveCD/LiveUSB.

If you cannot get Natty running, please use your previous LiveCD/LiveUSB to boot the PC and access the forums.  You can also use the previous LiveCD/LiveUSB to download the Natty ISO and create a Natty LiveCD/LiveUSB.

Using the LiveCD/LiveUSB, please backup your documents to an external hard drive or USB stick.

You will need do a clean install of Natty.

If you have a separate '/home' partition, this is much easier as you can do a manual install (called 'Something Else') and format the '/' (root) partition, and DO NOT FORMAT the '/home' partition for a reasonably painless clean install.


***The Hedge***

:KS

---

### Post by khoacao on 2011-04-30
> **beachbuggy said:**
> Afternoon all. 

I have just finished the upgrade of the latest version and I'm at the point of my system restating. 
As I'm such a noob I didn't make a live CD and test it first :(

My system automatically tried to restart but on the restart I got the 'terminal' view. It stopped when asking for my username (it never normally asks for this before the grub menu) and then password. I didn't get any further than that. 

I now have on my screen (still in the terminal view before the grub menu)

"name@name-desktop:...$ "

I'm on my phone now so I don't actually have the symbol for before the dollar sign but your know what it is. The raised S on a 90 degree angle. 

Any help on what I am to type in now would be much appreciated. 

Collin



Hi there, please refer to my reply here:

[http://ubuntuforums.org/showthread.php?p=10748345&posted=1#post10748345](http://ubuntuforums.org/showthread.php?p=10748345&posted=1#post10748345)

---

### Post by jz32300 on 2011-05-01
Hi,

I've just completed the online upgrade from 10.10 to 11.04 and I also have boot problems.

When I boot the PC (a Toshiba Satellite laptop) I get the new grub menu. I select the new Ubuntu version; the screen goes black and the light on my Caps Lock key flashes on and off. At this point the PC is blocked and the only solution is to turn it off and reboot into 10.10 or Windows XP.

How can I fix this problem?

Thanks in advance
Clive

---

### Post by TheHimself on 2011-05-01
This means that the kernel can not be started. You'll probably have to reinstall Ubuntu.

---

### Post by beachbuggy on 2011-05-01
Thanks 'The Hedge' I have the 10.10 live CD I forgot that would work. I will backup my files get the new ISO and start again.

 Cheers again

 Collin

---

### Post by HammerHed on 2011-05-03
> **jz32300 said:**
> Hi,

I've just completed the online upgrade from 10.10 to 11.04 and I also have boot problems.

When I boot the PC (a Toshiba Satellite laptop) I get the new grub menu. I select the new Ubuntu version; the screen goes black and the light on my Caps Lock key flashes on and off. At this point the PC is blocked and the only solution is to turn it off and reboot into 10.10 or Windows XP.

How can I fix this problem?

Thanks in advance
Clive

I had a similar problem and on reboot press the "ESC" key this will  give you some startup options. I chose boot in "Rescue Mode" and this gave me  a command prompt/terminal.

I then ran the following:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

This installed/upgraded all the bits and pieces that did not get updated to the latest version during the install.

I was then able to boot into the desktop after a restart.

---

