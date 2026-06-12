---
title: "Problems on sources.list, network manager, and software center after upgrade to 13.10"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by scprotz on 2013-10-20
I have slowly been migrating my desktop from 10.04 to 13.10.  I made it all the way to 13.04 and everything was running smoothly. I figured one more upgrade wouldn't hurt.

After the upgrade I saw my Cairo dock was missing.  I went to check it and the app wasn't appearing in unity.  I then tried to install it.  I found all sources were still pointing to raring instead of saucy. Software center would NOT let me select multiverse (like I didn't have permission).  It'd check the box but immediately uncheck it.

I manually swapped raring to saucy (I checked numerous spots and my computer says it is 13.10 and the upgrade appeared to work correctly) in the sources.list file.

I also noticed I didn't have a network connection. I am not allowed to use the network manager applet in unity or gnome.  In unity it says: 

Failed to add/activate connection
(32) Not authorized to control networking.

I logged in as root and used the nm-applet to tell my wireless to automatically connect and work for anyone (not ideal, but it got me some wifi for a bit).  I still can't manage any network connections.

I went back to install Cairo since it appears not to be installed.  Now software center says:

Software can't be installed ore removed because the authentication service is not available.  (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':':1.82'}): org.debian.apt.install-or-remove-packages.


Thinks I have tried:

reboot
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall policykit-1

I have checked my startup.  If I ps my running processes is shows that /usr/lib/policykit-1/polkitd --no-debug is running.

Please any help.  It looks like I'm having a policy authentication failure but I am not sure how to fix it.

Thanks,
scprotz

---

### Post by scprotz on 2013-10-20
As a follow-up and to add insult to injury:  I also cannot reboot/shutdown from the buttons.  I have to use a terminal and 'sudo reboot now!' to get the system to go down.

I did finally find my installed cairo-dock.  I tried to launch it.  Now when the system comes up, Cairo tries to start by blinking on, goes to its configuration page, I close it, It blinks again, and then disappears.

I really think something broke with one of the authentication modules during upgrade as nothing will run correctly.  Any ideas would be appreciated.

Thanks

---

### Post by jjaison-daniel on 2013-10-26
I also having this issue. But I just upgraded from 13.04 to 13.10.

---

### Post by djdill on 2013-10-30
I am also having the same problem with lubuntu - lxde 
13.04 -> 13.10
Was working fine with Network Manager and shutdown buttons etc (13.04).. But now can only connect to the internet via [I]wpa_supplement 
[/I]Network manager will not auto connect as well.. So I have no internets :(
I have run the below command each time it starts to get my wifi up and working:
sudo service networking stop
then kill any other wpa_supplement ps
Then start the process as above:
Network manager gives me :
(32) Not authorized to control networking.

Little more info:
I am running on a ARM based core - TF101

---

### Post by Interruptor on 2013-11-11
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1249844](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1249844)

---

### Post by syntaxerror74 on 2013-11-13
Looks this is exactly the problem I had when doing a full upgrade:

[http://ubuntuforums.org/showthread.php?t=2185833](http://ubuntuforums.org/showthread.php?t=2185833)

**Network manager** applet (somewhere between the clock and the loudspeaker by default) was **gone for good**, never to reappear again. But gladly I remembered I could use pon/poff, copied the /etc/ppp... stuff preserved from my old Debian from my USB stick, and VOILA it worked! It's almost magical, but despite lacking a working network applet, even auto-dialin (!) will work after I power-cycle the machine. The only thing that is missing now is the pop-up window I have to 'OK' every time.
AND I have to 'poff/pon' the connection should I ever want to reconnect with new dynamic IP.
But otherwise...I am surprised I can even live with that bug. ;)
Nevertheless, whoever broke that should be walking one week with a brown paper bag---even in a lively city---just as a long-lasting lesson to be more careful next time. Since once one starts messing with PAM and authentication, he should *really* know what he's doing, and if not, keep his dirty mitts off there and leave it to the experts that can! Gazillions of users will be thankful for that.

---

