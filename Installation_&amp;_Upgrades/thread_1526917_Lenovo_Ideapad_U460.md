---
title: "Lenovo Ideapad U460"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by gopa on 2010-07-08
Hi all,

   I am planning to buy this recent model: Lenovo Ideapad U460.
I find that it comes with windows 7 pre-installed. I would like to install
Ubuntu Lucid lynx with dual boot option. I was wondering whether anybody
here faced any problems during Ubuntu installation on Lenovo laptops.
Main concern is about the Hardware configuration that I can choose:

======
**Graphics**:Intel Graphics Media Accelerator HM55HD  /  NVIDIA GeForce 305M

**Processor**: Intel Core i350M  (2.26GHz 1066MHz 3MB )   /   Intel Core i5-450M Processor ( 2.40GHz 1066MHz 3MB )

**Network card**: Intel Wireless Wi-Fi Link 1000

**Bluetooth**:  Bluetooth Version 2.1 + EDR

[B]Fingerprint Reader
[/B]=======
I just want to make sure that I am going for the right hardware so that I am
not stuck at some point with the installation;). Recently I found that[URL="http://ubuntuforums.org/showthread.php?t=1525765"] Intel 855 and 
Ubuntu 10.04[/URL] has some issues.

Thanks in advance for all suggestions, help and comments.;)

---

### Post by davidmohammed on 2010-07-08
no experience with this laptop model myself - however, try booting the live CD, and use the option "try without installing" - have a play with wireless, graphics etc and see if all of this works or if you have to use workarounds.

---

### Post by Ibidem on 2010-07-08
The graphics are the only trouble I can see; [http://ubuntuforums.org/showthread.php?t=1393413](http://ubuntuforums.org/showthread.php?t=1393413) and [https://bugs.launchpad.net/ubuntu/+bug/518938](https://bugs.launchpad.net/ubuntu/+bug/518938) indicate it may not work;  switching graphics (what Intel + NVIDIA means) is a WIP.  The NVIDIA should work, if recognized.
Wireless  should work.  Bluetooth is too vague.
Is it in-store, or online?  If in-store, ask about a "live" test run.  Otherwise, make sure you can get a FULL refund, or look elsewhere.  Thinkpads look more promising to me, though.

---

### Post by gopa on 2010-07-12
Hi thanks for the comments.. It is not available in the store, but it is an online shop.
It seems that I have to wait for some time to get this item. I think I will go for NVIDIA GeForce305M 
graphics card. I will update this thread with my experience later. thanks for all comments...

---

### Post by dgokhale on 2010-08-24
> **gopa said:**
> Hi all,

Main concern is about the Hardware configuration that I can choose:

======
**Graphics**:Intel Graphics Media Accelerator HM55HD  /  NVIDIA GeForce 305M

**Processor**: Intel Core i350M  (2.26GHz 1066MHz 3MB )   /   Intel Core i5-450M Processor ( 2.40GHz 1066MHz 3MB )

**Network card**: Intel Wireless Wi-Fi Link 1000

**Bluetooth**:  Bluetooth Version 2.1 + EDR

[B]Fingerprint Reader
[/B]=======
I just want to make sure that I am going for the right hardware so that I am
not stuck at some point with the installation;). Recently I found that[URL="http://ubuntuforums.org/showthread.php?t=1525765"] Intel 855 and 
Ubuntu 10.04[/URL] has some issues.

Thanks in advance for all suggestions, help and comments.;)

Hi ... got my u460 a month ago and just got around to installing Lucid 64-bit on it. Am running a dual boot machine right now. Breezed through the install. Still fiddling around and checking things. Have an i3 processor, integrated graphics, 4GB RAM etc.

Works out of the box - graphics, sound, wifi, bluetooth. 
Note - The brightness control does not work with the Fn+Up/Down keys. You can change it though with the Gnome Brightness Applet. I have submitted a bug report ([Bug # 623065]("https://bugs.launchpad.net/bugs/623065")). I dont have Nvidia graphics on my machine. Just the integrated intel one.

Some other keys also do not work with the Fn key and I am trying to figure it out.But they are not that serious.

Also in the process of getting the Synaptics Touchpad to support multi-touch smoothly. Seems I may need to fiddle a bit with the values as right now the multi-touch movement seems jerky.

Have downloaded a package for the Upek fingerprint reader from the OEM website (Upek) but have not got around to installing it. Will update.

On the whole quite happy with the way its running ... other than the brightness control part ..

---

