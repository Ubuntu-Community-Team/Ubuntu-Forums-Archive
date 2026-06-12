---
title: "No Internet After Feisty Upgrade"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by clucas on 2007-04-22
Had been using Ubuntu 6.10 without any problems. Upgraded to Feisty 7.04. Upgrade went smoothly except now I can't connect to the internet. What's that all about?

---

### Post by Immolatus on 2007-04-22
> **clucas said:**
> Had been using Ubuntu 6.10 without any problems. Upgraded to Feisty 7.04. Upgrade went smoothly except now I can't connect to the internet. What's that all about?

whats the hardware?

---

### Post by clucas on 2007-04-22
Dell Dimension 8200.

From the "Hardware" the network card is "21X4XDEC-Tulip Compatible 10/100 Ethernet".

I seem to remember a while ago I had to do some manual changes when I installed 6.10. Perhaps it's the same now. But I can't recall how I changed it.

Just checked....that was when I was using SUSE 10.0.

---

### Post by Immolatus on 2007-04-22
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0603.0/1210.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0603.0/1210.html)

If you look in this link, the guy reported a bug and if you read through he states his belief that it is the fault of the tulip's driver.  Is this a wireless card or mobo card?
I found a whole lot of bug listings for this particular card under Linux. It's odd but I gather it has something to do with the kernel not liking the firmware module very much.
I couldn't find this firmware on Sourceforge either but I'll keep digging. 

Now I'm intrigued.

---

### Post by clucas on 2007-04-22
I found a solution. this was a help: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2508381](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2508381)

It had the loopback listed but not eth0 so I did a little messing around and then when I clicked on the monitor icon (which I had to manually add to the bar) etho was listed so clicked on that. Now all is well.

All is not well. When I reboot I have to go to a terminal and put in: sudo ifdown eth0 and then sudo ifup eth0. Don't know why. Didn't have to in 6.10.

---

### Post by Immolatus on 2007-04-22
I had a similar problem with my ipw2200, sometimes the kernel picks it up and sometimes doesn't.
Is there anything in /lib/firmware?
I just looked in mine and found a folder "2.6.20-15-generic". Maybe if you add the firmware for you're specific card here it'll pick it up from the bunch.

---

### Post by clucas on 2007-04-22
Just checked and I also have the same folder in /lib/firmware. But I don't know how to add the firmware for my specific card.

---

### Post by Immolatus on 2007-04-23
> **clucas said:**
> Just checked and I also have the same folder in /lib/firmware. But I don't know how to add the firmware for my specific card.

ummmm...I didn't find it right away when I looked so, go to the vendor (who ever made the card) or the OEM (who ever made the machine) site and look for the Linux firmware there. And also look on Sourceforge.
You aren't the only one to have this issue with this card so I'm sure you can find it, just make sure you get the newest one.
When you get it the download will be a .gz or a .tgz file. Just download it to you're desktop (save to disk) and extract it into you're home folder.

in a terminal do;

sudo cp /home/you're login name/the full name of the extracted folder*  /lib/firmware

The asterisk in unix represents the operand for cp (copy) the reason I say do it this way is because  this will work regardless of the distro as it is a depricated unix technique and therefore compliant to linux/unix/bsd, K?
Also, if it ends up in the wrong place and you wont to remove it and copy it somewhere else, you still have the copy in you're home folder where you don't have to search for it and can plainly see the file path to it 
So, I'll try to find this thing myself. Let me know.

---

### Post by Immolatus on 2007-04-23
[http://sourceforge.net/projects/tulip/](http://sourceforge.net/projects/tulip/)

I found this and a bunch of other crap just by Googling "tulip driver" (minus the quotes).
this should at least take you in the right direction. I also discovered that the card was produced by a company called Allied Telesyn if that helps.
Now, I didn't trace all the way to the driver download itself as I got side tracked but I'm sure you'll find it from there.

---

### Post by clucas on 2007-04-23
Than ks for all the research! I'll look into all of this.

What I don't really understand is why it worked without any problem in Ubuntu 6.1 but not Feisty.

---

### Post by Immolatus on 2007-04-23
> **clucas said:**
> Than ks for all the research! I'll look into all of this.

What I don't really understand is why it worked without any problem in Ubuntu 6.1 but not Feisty.

probably because the firmware or a version of firmware that just happened to work for you're card was built in to the distro for 6.1 but not for 7.04. some times they just take things out to keep the clutter down if they think no one is using them. For example  Realtek is is the most common etho card in oem machines along with intel chip sets. So you'll always find these drivers in a Linux distro.:biggrin:

---

