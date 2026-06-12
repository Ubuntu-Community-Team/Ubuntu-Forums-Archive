---
title: "how to upgrade"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by edwin15 on 2015-01-15
Hello
I have the old ubuntu on one of my older desktop computers. I downloaded the new number 14 version to my USB stick from my laptop. I plug the USB into the old computer and it keeps on flashing forever....will not finish booting...when I turn on the computer.
Can someone help me how to upgrade to the new ubuntu ?:p

Can I wipe out the old ubuntu somehow and load in the new ubuntu?
Also when I try to run the USB file with number 14 on it it tells me it is not executable....not safe.  ??
:guitar:

---

### Post by TheFu on 2015-01-15
What was the old Ubuntu version?  LTS to LTS to LTS is well supported, provided the existing install is fully up-to-date, i.e. patched. Skipping is not supported.
Wubi installs are not supported anymore either.

Also - there are two Ubuntu "14" releases - you should stay with 14.04, which is an LTS release with 5 yrs of support. The newer 14.10 release gets 6-9 months of support only and really isn't meant for casual users.

So ... if you have either 13.10 or 12.04 already on the machine, then boot into that and run 
**sudo do-release-upgrade**  [https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Good luck.

---

### Post by edwin15 on 2015-01-18
Well at this point frustration is kicking in and I might just buy a new HP with Win 8.1 and give up on Ubuntu on my older computer. I upgraded it to 4 gig ram too using ram from another machine. There is simply too many hurdles on this old Ubuntu 10.10 version...I would upgrade but its not user friendly like modern Win 7 and Win 8. New upgrades should load AUTOMATIC. And it says new updates or plug in downloads are not from authentic sourse. or unknown sourses...so Im dead in the water at the moment. I would like to use it and make use of my old computer but just too many obsticles...
People are gradually forgetting old skills of booting and running installs and upgrading. As I am.
If one has to be a computer wiz ...almost ...to get all these things working....then people will give up. new cell phones and new Windows and Apple etc etc are all so user freindly....you do not need to know anything practically. I might keep trying but it is frustrating.:confused::-({|=

---

### Post by ian-weisser on 2015-01-18
> **edwin15 said:**
> I plug the USB into the old computer and it keeps on flashing forever....will not finish booting...when I turn on the computer.
I cannot tell which noun 'it' is referring to. The USB stick? The keyboard? The monitor?
Is there a pattern to the flashing? 
What happens on the screen? Nothing? Black screen? Words? Purple screen? Blinking dots? Kittens?

> **edwin15 said:**
> New upgrades should load AUTOMATIC
You had an entire year to upgrade easily: April 2011 to April 2012. The system probably automatically nagged you about it several times back then.

You can automaically upgrade to the next release of Ubuntu. It is inadvisable to do so - you risk data loss. But it's YOUR system, and easy to set up if you want it.

---

### Post by edwin15 on 2015-01-18
OK I didnt upgrade because I havent used this computer in about 3 years. It now has 4 gig ram versus 2 gig a few days back.I have Win XP on it and would be using it but for some reason XP wont connect to my wireless home network. I even called my Internet service help on the phone and they couldnt help me get it going. But the old Ubuntu system does connect to internet for me to do some stuff...news,,,ebay ,,,etc etc.
The version is 10.10 ...you say automatic upgrade to next relaese...but it is not automatic. When I said flashing I meant the 4 gig USB stick...a few days back when it seemed it would load the 14.04.1-desktop-amd64.iso version ....
If inadvisable to upgrade ??...what other options ? What is best version....14 ? 11 ?
Also I dont understand why it seems nothing will run...I double click the 14.04 folder and it says the file is not marked as executable...??then I press OK and thats it...??
Maybe best if I uninstall the 10.10 version entirely ??...but I dont know how to do that exactly and then I would have no internet on the computer at all...

---

### Post by grahammechanical on 2015-01-18
> [COLOR=#000000]The version is 10.10 ...you say automatic upgrade to next relaese...but it is not automatic. [/COLOR]

That is because Ubuntu 10.10 reached end of life by April 12.04. Upgrading from 10:10 to 11.04 and then to 11.10 and on to 12.04 would have been a one click affair each time.

There is a way to do the upgrade but you need to edit a system file. But the next version (11.04) is also end of life and you would have to repeated the process a second time (to get to 11.10) and a third time to get to the first release of Ubuntu that still has support (12.04).

There is something else to consider: There was a big jump from Ubuntu 10.10 to Ubuntu 11.04 and not just in the look of the user interface. With Ubuntu 11.04 we stopped using the Gnome 2 desktop environment and its Gnome 2 panel and switched to the Gnome 3 desktop environment with Ubuntu's own Unity user interface. As an experiment I recently tried the End of Life Upgrade method to go from 10.10 to 11.04 so that I could give a clear explanation on how to do it and I ended up with a really messed up user interface that I could not log in to.

Here is the really big question: Is your graphic adapter capable of doing hardware accelerated 3D rendering? How much of its own memory does the graphic adapter have? In other words can it run the latest Ubuntu?

Look at this wiki page and go to the section called Changing the CD's Default Options and see section 6 -F6. You could try to add the nomodeset option when running the Ubuntu installer.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

### Post by TheFu on 2015-01-18
Most people are not capable of installing an OS. It has been this way since Windows 2.0 and I don't see that changing anytime, especially when Microsoft forces hardware vendors to implement changes that have to be reverse engineered by every other OS in order to even boot. Certainly, some of these changes are technologically superior to the previous solution, but when the only way to load an OS onto some hardware involves paying Microsoft a certificate fee, that just seems wrong to me, a F/LOSS loving user.

How many customers did Apple abandon by dropping support for PPC Macs?
How many 16-bit programs did Microsoft stop working with Vista?  
Don't forget all the printers that didn't get updated drivers for any 64-bit Windows or Vista.  I have 2 printers like that here. They work perfectly under Linux, but not at all under current Windows.

The point is, that dropping support happens all the time across all vendors. This situation isn't unique, though it may feel that way to you, this time.

None of this provides you with satisfaction, but in the terms of Microsoft, you currently have Windows 95 and want to load Windows7 directly. You are 4+ versions behind the currently supported release. It isn't like support periods are not published - here: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) and a few other places. That link has a nice graphic to help you better understand the 10.10 release limited support period.

People like you and I need to stay on LTS releases only. I hope you will heed this advice going forward.

If your GPU is not 3D accel capable, please consider loading a non-Unity Ubuntu desktop - perhaps Xubuntu or Lubuntu?  The support periods for the LTS versions of these I don't recall, but think they are 3 yrs, which is enough to migrate from one LTS to the next with a year overlap.  Always, always, always stay on a supported release or take responsibility if you elect not to.

I wish you the best of luck in finding a solution that meets your needs and isn't too hard to implement.

---

