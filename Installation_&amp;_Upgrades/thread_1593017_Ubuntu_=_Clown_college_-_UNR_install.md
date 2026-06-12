---
title: "Ubuntu = Clown college - UNR install"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by gcday on 2010-10-11
Let's say you are a new user and you heard about Ubuntu and you decide to download UNR 10.10 to install - you download it and then click on the install instructions and it tells you to download the universal installer and what happens when you head over to get the univerisal installer?

> Updated to include Ubuntu 10.10, Xubuntu 10.10, and Kubuntu 10.10 final with Persistence.** Corresponding 64 bit and Netbook versions will be added** (as time permits) within the next few days.

This is clown college - isn't there anyone checking any of this stuff? 

I wonder how many potential users just don't bother coming back?

Is it actually possible to install UNR via USB at the moment and is it something that a none-technical person can do?

---

### Post by kerry_s on 2010-10-11
[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

---

### Post by gcday on 2010-10-11
> **kerry_s said:**
> [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Hi Kerry, I already have a copy of the iso, I simply have no way of installing it on UBS following the instruction provided by Ubuntu.

Best

GCday.

---

### Post by mikewhatever on 2010-10-11
I suppose you could wait a few days, could you not?

---

### Post by gcday on 2010-10-11
> **mikewhatever said:**
> I suppose you could wait a few days, could you not?


I could but that's not really the point is it? If you are saying to the world at large "Today is release day" people expect to be able to install the actual OS - it's amateur hour.

---

### Post by mikewhatever on 2010-10-11
Do you have to be so fussy? Look through the new forum posts. People are installing the actual OS. Universal USB installer is a program for Windows I've never heard of. Suppose the world could use the USB Image Creator included by default in Ubuntu.

---

### Post by gcday on 2010-10-11
> **mikewhatever said:**
> Do you have to be so fussy? Look through the new forum posts.

t's not a matter of being fussy - my point is that Ubunutu is suppose to be at the stage where it's for everyone and this is amateur own-goal stuff, a sizable number of people will simply conclude this stuff doesn't work and will not come back. 

> Universal USB installer is a program for Windows I've never heard of.

It's the one that you are directed to use  - [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)


> Suppose the world could use the USB Image Creator included by default in Ubuntu.

I have no idea what this is? How would someone get to it on a windows box?

---

### Post by mikewhatever on 2010-10-11
I beg to disagree. Those genuinely interested and wanting to try Ubuntu will come back. I really hope you won't get stuck in the lofty criticizing attitude of yours. Loosen up and try to enjoy it.

---

### Post by gcday on 2010-10-11
> **mikewhatever said:**
> I beg to disagree. Those genuinely interested and wanting to try Ubuntu will come back. I really hope you won't get stuck in the lofty criticizing attitude of yours. Loosen up and try to enjoy it.

What's lofty about expecting basic things to be right? It's not lofty for the end-user to expect things to actually work when they follow the instructions provided by the vendor. This is really low-level stuff to make sure works at launch. Lofty would be providing some crit of some minor aspect of the GUI, not that the OS as provided can't be loaded by a novice user.

---

### Post by Cobracommand0 on 2010-10-11
A few minutes of searching Google about a Ubuntu USB install would eventually bring up the Ubuntu Install guide which recommends Unetbootin:



[LIST]
[*]Instead of usb-creator.exe you can use Unetbootin to create a bootable USB drive. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[*]You  won't be able to select the USB drive if it wasn't formatted in a way  that Windows can see it.  You may have to format it using Windows  Explorer in order for it to show up in a creator tool.
[/LIST]

I would expect a new user to Ubuntu would still be able to Google for a answer to the USB issue, which would bring up the forums/official documentation.  Unetbootin is more reliable than the Windows Universal Installer IMO.

---

### Post by mikewhatever on 2010-10-11
I don't know, perhaps it just seems lofty to me. Don't you think you are somewhat overreacting? 
From the look of pendrivelinux.com, it's obviously a third party project Ubuntu devs have no influence over. Now, my own reaction to the quote you posted from their site was, "thank you for providing an application for Windows users, even though I am not one of them". New users that want to try Ubuntu from USB can use a 32bit desktop version, or use another computer with Ubuntu installed.

---

### Post by aidanandrach on 2010-10-11
Interesting thread.

I quite strongly agree with the OP.  Ubuntu is being pushed more and more 'for the masses' and as a genuine alternative to Windows.  But how can this be true if someone from the masses can't easily install it?

For me at least I'm somewhat stuck with my Windows environment for my desktop PC due to my heavy investment in audio software.  But my netbook is another story.  Here, UNR offers me a genuine alternative with a system that is (on paper) tailored to the hardware (at least vs. XP!).  So I was awaiting the arrival of 10.10 with some eagerness, having been disappointed with 10.04...

Now I'm a pretty tech-savvy person, but so far I've tried three of  different methods to get a live USB up and running for 10.10 UNR with no success.  In desperation I ended up using the desktop version and loading Unity on top of it just to see if it was what I'm after - looks great, but the performance out of the box is poor.  That would make four attempts now.

I suspect the masses would have given up at two.  And the 'wait a few days' argument just doesn't fly too well I'm afraid - first impressions and all that...

I'm aware that Pendrivelinux is a third party project and that Ubuntu can't control their releases, but if the "show me how" instructions on Ubuntu.com are going to point to it, then Canonical need to make sure it works.

Clown college indeed.

---

### Post by Old_Grey_Wolf on 2010-10-11
I have to agree with the OP on this. The link in the Ubuntu download page points to the Universal Installer if you select Windows as the OS.

There is also a related comment in the Ubuntu Wiki Release Notes about using the Startup Disk Creator in Ubuntu 10.10.

> It is not possible to create Ubuntu 10.04 USB disks from the Startup Disk Creator in Ubuntu 10.10 due to a backwards incompatibility in the syslinux program.

When the Startup Disk Creator doesn't work I use Unetbootin; however, I have a few years of experience behind me. The same goes for the Windows installers.

Edit: <humor> ducks head </humor>

---

### Post by gcday on 2010-10-12
> **mikewhatever said:**
> I don't know, perhaps it just seems lofty to me. Don't you think you are somewhat overreacting? 
From the look of pendrivelinux.com, it's obviously a third party project Ubuntu devs have no influence over. Now, my own reaction to the quote you posted from their site was, "thank you for providing an application for Windows users, even though I am not one of them". New users that want to try Ubuntu from USB can use a 32bit desktop version, or use another computer with Ubuntu installed.

Just to be clear about this, I am not blaming Pendrivelinux.com, they can upgrade or change their products at a time that suits them, that's not the actual issue.

---

