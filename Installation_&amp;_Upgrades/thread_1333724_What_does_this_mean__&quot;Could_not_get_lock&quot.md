---
title: "What does this mean?  &quot;Could not get lock&quot;"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2009-11-21
I'm trying to install Ndiswrapper and I don't understand what this "lock" stuff is all about and how to fix it.


owner@ubuntu:~$ sudo apt-get install ndiswrapper-common
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by lisati on 2009-11-21
In computers, a "[lock]("http://en.wikipedia.org/wiki/Lock_(computer_science)")" is commonly used to make sure that two different programs **don't** try to update important information at the same time.

Things to check when you receive such a message include making sure that you don't have two installers running at the same time.

---

### Post by PDA1 on 2009-11-21
How do I solve the problem?  Can you tell me what to do?

---

### Post by sgosnell on 2009-11-21
Close Synaptic, Update Manager, and anything else that can add programs.  They're all GUI frontends for apt-get, and you can only have one run at a time.

---

### Post by PDA1 on 2009-11-21
Call me stupid.....but how do I close them?

---

### Post by sgosnell on 2009-11-21
The same way you close any program - with the X at the top right corner, or with Alt-F4.

If they're minimized, you can right-click on the icon in the panel and select Close.

---

### Post by PDA1 on 2009-11-21
I was afraid you'd say that.

The problem is those programs do not appear anywhere on my screens.  They are neither at the bottom nor top of the screen....or anywhere else.  They have to be running somewhere.....so Ubuntu says.

This is a mess.

I'm just trying to figure out how to get Ubuntu to connect to the web wireslessly and I just can't figure it out.

WHAT A PAIN!!!!

I wish there was a simple program that I could run that would solve the wireless problem.

---

### Post by drs305 on 2009-11-21
Have you rebooted since you had the lock problem? That is probably the best way to ensure the APT-related apps are not running. 

Check System, Admin, System Monitor for any running install apps.

If you have already done that, *copy* these commands into a terminal and run them. 
```

sudo killall apt-get synaptic aptitude update-manager
sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock-bad
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by PDA1 on 2009-11-21
Am I supposed to enter the code you mentioned "sudo killall etc?

---

### Post by drs305 on 2009-11-21
> **PDA1 said:**
> Am I supposed to enter the code you mentioned "sudo killall etc?
Yes, just copy each line into a terminal and press ENTER. You will be asked for your password and won't see it as you type it.

The commands will stop/kill any of the listed apps, ensuring that no APT processes are really running.

You also may not see any messages when you run one or more of the commands, which is ok. You will probably get "no process found" messages on the first one, and nothing on the second.

---

### Post by lisati on 2009-11-21
EDIT: DRS305 beat me to it.....

---

### Post by PDA1 on 2009-11-21
By the way- can you tell me simply how to connect Ubuntu to the web with my notebook?

I can use the cabled ethernet connection but the wireless stuff won't work.  It works perfectly on Windows XP.

Thank you

---

### Post by PDA1 on 2009-11-21
More headaches- what's the matter with this thing?


Please insert the disk labeled:
Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)
in drive /cdrom/


W: Failed to fetch cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb

---

### Post by lisati on 2009-11-21
> **PDA1 said:**
> More headaches- what's the matter with this thing?


Please insert the disk labeled:
Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)
in drive /cdrom/


W: Failed to fetch cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb

What were you trying when this came up? (It means that it wants your Ubuntu CD in the disk drive)

---

### Post by dhavalbbhatt on 2009-11-21
> **PDA1 said:**
> More headaches- what's the matter with this thing?


Please insert the disk labeled:
Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)
in drive /cdrom/


W: Failed to fetch cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb

I am guessing that under System -Administration - Software Sources, in Ubuntu Software tab there is a section for "Installable from CD ROM / DVD" - uncheck any options there and hit save. That will take care of your above problem.

---

### Post by sgosnell on 2009-11-22
"Wireless won't work" is a rather nebulous statement.  You need to be much more specific about what you've done and what the problem is.  Wireless works out of the box on my netbook, but I don't have yours, so I can't speculate about the cause without more information.  Is the problem with all access points, or just your home network?  What security?  Is the SSID broadcast?  Does the network manager see the wireless network, or any networks?

---

### Post by PDA1 on 2009-11-23
> **sgosnell said:**
> "Wireless won't work" is a rather nebulous statement.  You need to be much more specific about what you've done and what the problem is.  Wireless works out of the box on my netbook, but I don't have yours, so I can't speculate about the cause without more information.  


Is the problem with all access points, or just your home network?  

I can only access the internet with the ethernet cable hooked onto the computer.


What security?

I use ESET when I'm in Windows.  I suppose ESET has no effect when I'm Ubuntu.
I have no virus program on Ubuntu that I know of.


 Is the SSID broadcast?  

I don't know what SSID is.  My notebook doesn't recognize, see or show any wireless networks.

Does the network manager see the wireless network, or any networks?

No.

---

### Post by sgosnell on 2009-11-23
The SSID is the name of the network.  If it's not broadcast, it's a 'hidden' nework.  By security, I meant WEP, WPA, WPA2, or none.  What are the settings on the router?  If you don't know how to do that, it's going to be a long process, but I think we can eventually get you going.

Have you tried other networks, other access points, or just your own network?

---

