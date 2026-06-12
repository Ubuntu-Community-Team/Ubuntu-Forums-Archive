---
title: "[SOLVED] Something is wrong w/ network-manager | Fresh install (2 times)"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by SloYerRoll on 2008-03-05
So I decided Ubuntu was too good an OS to share w/ my windows drive. So I shoved some files around and formatted my second internal HD (250GB) and installed 7.10 on it. 

The update manager told me I had 196 updated available. So I clicked OK to download/install. Everything downloaded fine, Then the install froze on a network manager error (of course at 98%). It locked out my keyboard and mouse. So I killed the machine. Started back up, ran updates and it froze on the same thing. it hung on CPA or CNA (whatever the network printer stuff is).

No sweat, I'll just install again and my problem will be fixed. So I install (telling Ubuntu to use the whole drive (if that matters). It tells me I have 196 updates to install. So I find the 5 updates that say CPA or CNA and de-select them. Then click OK. 

I let the machine run for over an hour (I have broadband and a fast machine so it's WAY longer than it needed). In the update details box, it said there was some kind of error on the network manager that it was hung up on. I tried to launch Firefox so I could ask for help, but nothing would come up. I couldn't even power the system down. I was able to force quit the updates though then restart. 

So I went to manually install repository updates by entering:
[FONT="Courier New"]sudo apt-got update[/FONT]

and it told me that "dpkg was interrupted must run [FONT="Courier New"]dpkg --configure -a[/FONT] to correct"

I run that command and it stalls out and locks my keyboard out so I can't copy/paste all the good stuff you guys need to help. 

I know I probably haven't given you enough relevant data. But if you tell me where any logs are that I can grab to help you figure out what's going on. I'll be happy to post them.

I know the install disk is good since I used the same one to install on a partition and it ran like a dream.

---

### Post by SloYerRoll on 2008-03-06
So I went in to install Compiz via terminal and the damn thing froze up on me again. I did write everything down so this may help a bit..

[FONT="Courier New"]Unpacking Compiz-settings-manager....

Setting up network manager 0.6.5-0ubuntu16.7.10.0
*Reloading system message bus configurations
*Restarting network connection manager NetworkManager

Sub process post instillation script
Error exit status 2[/FONT]

---

### Post by jimv on 2008-03-06
Try Wicd.  I installed it earlier and I LOVE IT compared to network-manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

To get it to run at startup, add an entry to your session (System, Preferences, Sessions) for "/opt/wicd/tray.py"

---

### Post by SloYerRoll on 2008-03-06
Thanks! But UGH....

I can't even open Synaptic. I normally don't since I'm trying to learn shell. Any ideasa on how to make this happen through shell?

Here's what I get when I try to run Synaptic:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I crossed my fingers and ran updated again. It froze up in the same spot. I had the presence of mind to have screen grab ready. (I only made the image so large so you can see the text)

[IMG]http://jbritt.smugmug.com/photos/262545579_Ntz9b-X3.png[/IMG]

---

### Post by jimv on 2008-03-06
Try this in a terminal:

cd /var/lib/dpkg/updates
sudo rm -r *

(make SURE that you are in hte /var/lib/dpkg/updates folder before running the second command)

---

### Post by SloYerRoll on 2008-03-06
Hey Jim, 

Thanks for showing me where to get rid of one of the problem files. I only found one file in there, so I didn't need to go to those -r extremes:)

So I was able to launch Synaptic and get wicd loaded in there easily enough. Now I went to install Wicd and it told me I had to remove NetworkManager.. SWEET!! Let's do it. 

Then the install starts and the same exact thing...
*Restarting network connection manager NetworkManager
And it just locks the keyboard up and I'm hosed. 

So I googled around and found an article on how to manually stop and isolate NetowrkManager [here]("https://help.ubuntu.com/community/WifiDocs/NetworkManager").(almost at the bottom of the page)

It tells me to enter the following commands in terminal:

```
Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
```

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
```

When I type in the second line of code:
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

It freezes up!@#Q@!\

If I can get past this line and make this happen.. What does the original coder mean by the following?
"Create two files with only the word 'exit' in them."

This is really frustrating. I don't want to move on until I figure this out. I don't want to set everything up just right and have to demolish it later to fix a bug!

---

### Post by jimv on 2008-03-06
try 

"sudo apt-get remove network-manager"

---

### Post by SloYerRoll on 2008-03-06
Hey Jim, it finally worked!

A few black eyes later. But all's well that ends well. 

I'm running updates now and crashing. I'm going to leave this thread open in case anything rears it's ugly head in the next day or so. 

Thanks for helping out!

All the best,

---

### Post by SloYerRoll on 2008-03-06
Thanks a ton Jim. 

Looks like everything is running ike a dream. Wcid is also allot easier to configure as well!

All the best,

---

### Post by jimv on 2008-03-06
YEah, I just switched to wicd the other day and I LOVE IT.

---

