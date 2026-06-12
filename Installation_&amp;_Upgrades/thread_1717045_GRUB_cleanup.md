---
title: "GRUB cleanup"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by katobe62 on 2011-03-29
With the updates received with Ubuntu 10.10 my grub splash screen has become very busy.   Is there a proper way to clean off the older update options?  
 
My dual boot for Windows 7 has now been pushed off to a second sceen.
 
Thank you
Cameron

---

### Post by Enigmapond on 2011-03-29
I recommend an app called Ubuntu-Tweak. Among a whole slew of great features, there is a feature to remove all the old kernels and that will clean the Grub...just add this PPA [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa) , run sudo apt-get update and it will be available in the software centre. An easy way in the terminal..:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak
```

It will be available in System Tools after installation.

---

### Post by Frogs Hair on 2011-03-29
The package cleaner included with Ubuntu Tweak works very well for removing old kernel entries and it has some other features you may find useful  . [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Sean Moran on 2011-03-29
> **katobe62 said:**
> With the updates received with Ubuntu 10.10 my grub splash screen has become very busy.   Is there a proper way to clean off the older update options?  
 
My dual boot for Windows 7 has now been pushed off to a second sceen.
 
Thank you
Cameron
There are probably smoother ways to sort this out, but my way is my way, and I have Startup Manager to finalise things.

You can download Startup Manager with: 

sudo apt-get install startupmanager

That's the final part. Download the startupmanager package first, because that is what you will need last.

The first thing to do is to open the terminal and cd to the /boot directory with

cd /boot

Get a listing of the files therein with: 
ls


You will see a range of old and new kernel versions, listed as 'abi, config, and initrd' sorts of files.  Each of these various versions have numbers.  eg. In Karmic I get 14, 22, and now 23.

I've also been told not to recommend the **rm -rf** command, so I'll suggest the **rm -ri** command instead.

Find the oldest, (LOWEST) number out of the two.  Be careful that you're deleting the OLD kernel and not the newer updated one.  When you know for sure what the number of the OLD kernel is, enter:


sudo rm -ri *-??-* 

where ?? is ther number for the kernel you're removijng.  The OLD kernel. Now cd / and you will see a couple of files in your root directory with the .old suffix.  These are just links.  Type:

sudo rm -ri *.old

That takes out the links.

Now back to the GUI and open Startup Manager.  It takes a while to open.  Have a look and maybe change from 640x480 to 800x600 or something simple, and close again.

Reboot.  

The old Linux kernels should now be gone from your GRUB menu.

---

### Post by Enigmapond on 2011-03-29
> **Sean Moran said:**
> There are probably smoother ways to sort this out, but my way is my way, and I have Startup Manager to finalise things.

You can download Startup Manager with: 

sudo apt-get install startupmanager

That's the final part. Download the startupmanager package first, because that is what you will need last.

The first thing to do is to open the terminal and cd to the /boot directory with

cd /boot

Get a listing of the files therein with: 
ls


You will see a range of old and new kernel versions, listed as 'abi, config, and initrd' sorts of files.  Each of these various versions have numbers.  eg. In Karmic I get 14, 22, and now 23.

I've also been told not to recommend the **rm -rf** command, so I'll suggest the **rm -ri** command instead.

Find the oldest, (LOWEST) number out of the two.  Be careful that you're deleting the OLD kernel and not the newer updated one.  When you know for sure what the number of the OLD kernel is, enter:


sudo rm -ri *-??-* 

where ?? is ther number for the kernel you're removijng.  The OLD kernel. Now cd / and you will see a couple of files in your root directory with the .old suffix.  These are just links.  Type:

sudo rm -ri *.old

That takes out the links.

Now back to the GUI and open Startup Manager.  It takes a while to open.  Have a look and maybe change from 640x480 to 800x600 or something simple, and close again.

Reboot.  

The old Linux kernels should now be gone from your GRUB menu.

Well...that is a way however, if the OP is not that familiar, it leaves too large a margin for error. With Ubuntu-Tweak..it's very simple and there is no rebooting needed.

Cheers!

---

### Post by Sean Moran on 2011-03-29
> **Enigmapond said:**
> Well...that is a way however, if the OP is not that familiar, it leaves too large a margin for error. With Ubuntu-Tweak..it's very simple and there is no rebooting needed.

Cheers!
I reckon you're right mate.  I don't like to give advice to people about deleting things from their /boot directory, but that;s just the way I do it, and I try to do stuff like that in the mornings, with coffee, not beer.

Can I ask though, because I'm rather keen to find a smoother solution, what is the apt-get name for Ubuntu Tweak?  I've tried apt-get install ubuntutweak and apt-get install ubuntu-tweak and no response.  Where can I get it, please?

---

### Post by Enigmapond on 2011-03-29
Check my previous post. You must first add the PPA. The best thing is that with this app...you CAN do it in the morning with beer... LOL

---

### Post by Sean Moran on 2011-03-29
> **Enigmapond said:**
> Check my previous post. You must first add the PPA. The best thing is that with this app...you CAN do it in the morning with beer... LOL
Thaniks mate.  Sorry I overlooked that post before, as it wasn't directed at me, so it's just my habit to skip down the threads and look for OP or references to myself.  Now we've got the update going, and I'll edit from this post when the Tweaks are ready to test out.  If I can define the debs to make it happen without the need for PPA comands, I might be able to add this to my distro yet.

---o0o---

Cleanup Successful!

The Clean Kernels option did it neatly, as far as I guess.  I still haven't rebooted yet, but Bruce Springsteen is still singing on Rhythmbox so I guess the latest kernel is still there.

Next time I run up a new distro, (Friday) I'll make sure my var/cache/apt/archives dir is clean and see what packages this entails, because it looks like something to test out further, although I still like to try to direct people to cli solutions for serious things if I can.

I'll check this tweak thing out over the weekend.  It looks good, but but sometimes a few basic terminal commands can achieve the same result with more proficient recipients.

---

### Post by themoon49 on 2011-03-29
Hello dear mates 
I have a problem, i'm attempting  to install vmware server 2 on ubuntu 10.10. 
so that i think, i will need to uninstall vmware workstation 7 from my ubuntu 10.10. (Right i do?)
while uninstalling the following error is occur 
i used to uninstall [COLOR=Red](sudo vmware-installer -u vmware-workstation 7.1.2.301548 OR sudo sh /usr/bin/vmware-installer --uninstall-product=vmware-workstation)[/COLOR]
[IMG]http://i55.tinypic.com/dlj14h.jpg[/IMG]
 
how can i go on? Help me and explain ACE VMwares.

---

### Post by katobe62 on 2011-03-29
Thank you for all of your assistance.  
I am new with Ubuntu but I am becoming comfortable with the terminal.    I did opt to allow the Ubuntu-tweak app to do the work, it worked smoothly and I do enjoy the other apps that arrived in the package!  I did feel comfortable doing all of the instructions in terminal, I was just limited on time and didn't quite trust myself.  

this is the greatest forum I have found.   
Thank you everyone for your quick and precise input.

Cameron

---

### Post by Enigmapond on 2011-03-30
Hi Cameron,
No problem, We are glad to help. Please mark the thread as "solved" in the thread tools in upper right.

Cheers!

---

