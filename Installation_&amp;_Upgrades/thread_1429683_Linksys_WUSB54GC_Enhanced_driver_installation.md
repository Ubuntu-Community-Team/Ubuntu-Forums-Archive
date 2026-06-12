---
title: "Linksys WUSB54GC Enhanced driver installation"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by SimonTemplarmagician on 2010-03-14
I've searched google and read quite a few threads on the the topic of installing the new enhanced rt73-k2wrlz.3.03 driver and modprobe my rt73usb driver but I'm running into a road block here when I get these messages after I run sudo make install. I have attached a screenshot. 

I have already run sudo aptitude. Sudo aptitude safe-upgrade. Sudo aptitude install linux headers.

***Update /etc/modprobe.d/ralink alias for wlan*
***Install firmware in /lib/firmware...
***Check old config

Is it having problems locating the firmware; How do I update the alias. As you can tell I'm somewhat new and hopefully I can get online to learn. Something to not is I've tried blacklisting the drivers before installation and also after. This time I still havent modprobed rt73 from following this thread: [http://ubuntuforums.org/showthread.php?t=1178790](http://ubuntuforums.org/showthread.php?t=1178790) nor have I plugged in my Wireless adapter during the installation phase yet.

Thanks for any help in advance.

---

### Post by Old_Grey_Wolf on 2010-03-14
You can try the GUI application for installing wireless drivers if you have the CD for the WUSB54GC.

In the Ubuntu repositories, there is an application called "Windows Wireless Drivers" in add/remove or ndisgtk in Synaptic. Down load it and run it. Select install new driver. Locate the drivers directory on the CD and select one of the .inf files. If there are more than one .inf file try each one. Install one and see if it works.

---

### Post by SimonTemplarmagician on 2010-03-14
Unfortunately I do not have the cd for WUB54GC :(

---

### Post by SimonTemplarmagician on 2010-03-14
Also WUSB54GC isn't included in the USB network cards that work with ndiswrapper according to [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)

---

### Post by Old_Grey_Wolf on 2010-03-14
<strike>It worked for me. I checked to make sure I'm using the WUSB54GC, and I have the CD in front of me as I type this.</strike>

Edit: I just looked at the CD and there is no .inf files on it. The WUSB54GC just worked out of box on 9.04 and 9.10. I am using the WUSB54GC Version 1.

---

### Post by SimonTemplarmagician on 2010-03-14
the WUSB54GC adapter works already I'm able to get online and browse and I'm able to crack WEP. However, I was trying to install the enhanced drivers from [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/) so that I'd be able to crack WPA. Also. Ettercap and Wireshark arent working. Arp poisoning is not working. So I think there must be a trouble with driver for injection.

---

### Post by SimonTemplarmagician on 2010-03-14
Also WICD client doesnt work with the current rt73usb driver

---

### Post by Old_Grey_Wolf on 2010-03-14
OK, I didn't realize that you wanted the enhanced driver for cracking WPA. I didn't know the WUSB54GC supported injection. That is why I have a WUSB300N.

---

### Post by SimonTemplarmagician on 2010-03-14
why isnt the regular driver working with WICD any ideas. this is what I got from the reuglar driver.

---

### Post by Old_Grey_Wolf on 2010-03-14
You may want to wait for a while to see if you get a response in the thread you posted to in the "Networking & Wireless" forum. I don't know how much help you will get on the Ubuntu forums when you are using the "Back|Track" OS distro that is meant for penetration testing.

---

### Post by SimonTemplarmagician on 2010-03-14
yeah I've been holding off on trying over there at the backtrack forum. They are so high on themselves and hate noobs lol

---

### Post by Old_Grey_Wolf on 2010-03-14
The people one the Back|Track forum don't want to be associated with script kiddies or crackers. They think of themselves a "Cyber Athletes". There is a difference. For example, the US government is advertising for "Cyber Athletes" who can help protect its networks and infrastructure from intrusion and exploitation. 

It took us 3 hours of dancing around the subject before you said what you were trying to accomplish. Just a suggestion...Try telling people what you want to do, and not try to hide it. Hiding your intentions suggests you may be up to something nefarious. ;)

I don't think the Ubuntu forum is the place for this type of discussion. I think it is probably not acceptable according to policy. The Ubuntu forum is not meant for "Cyber Athletes". There are other forums for that type of discussion.

---

### Post by SimonTemplarmagician on 2010-03-14
Thanks for your help gray wolf. But with all due respect the subject of this thread is not backtrack or ettercap it is the successful installation of the enhanced driver. Observe The title of this Thread is in fact :  **Linksys WUSB54GC Enhanced driver installation**. That confuses me that you did not know that I was talking about the enhanced driver when I mention that during my first post and it is indeed the title of the thread. As far as the success of keeping my network safe from hackers that is not the topic. The question is I'm running into problems installing a driver. What are your thoughts if any.

---

### Post by Old_Grey_Wolf on 2010-03-14
> **SimonTemplarmagician said:**
> What are your thoughts if any.

I think you may have proven my point. And, I find the use of "Gray **Dog**" as a deliberate insult. I have been trying to be helpful; however, it seems to be falling on def ears. 

Anyway, good luck with your inquiry. 

I give up. Let's see if someone else can help you.

---

### Post by SimonTemplarmagician on 2010-03-14
I wasnt trying to insult you dude. I cant see your name when I write I reply and I had it in my mind that was your name. But thanks for your help so far. I dont know how that proves your point when I have pointed out to you that the topic of the thread is enhanced driver installation. So it is confusing if you dont understand that.

---

