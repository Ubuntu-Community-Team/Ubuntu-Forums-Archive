---
title: "Need help with modem dialing and upgrade to 7.04"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by mbsnr on 2007-06-02
as I've *really* had enough of Ubuntu.

Ok - I have a brand new install of 6.1. The battery meter works in this version but not in 7.04 on my laptop. I decided to try and upgrade my copy to 7.04 using the CD to see if the battery meter continues to work - long shot but you never know. Check my other posts for my lack of faith.

So how do I do this from the 7.04 CD? I'm on dial up (28K)  so the internet is NOT an option. Have I missed something obvious....? I don't think so.

I tried
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade

it ignored the CD and decided the update would be via my 28K modem....

In addition I had to use a Windows PC to figure out how to get Ubuntu to dial a modem connection. Why is this not built in...? I can configure the modem but couldn't dial it? Surely *this* is important that it should be there as a big button?!? Not everyone in the world has fast internet access you know.

So eventually I got dialup working using pon/poff after running sudo pppconfig. The cmd sudo apt-get install gnome-ppp fails even though I'm on the web. Again why?

This is the last post and Ubuntu's last chance otherwise Bill Gates gets me back....

Thanks

---

### Post by aysiu on 2007-06-02
I retitled your thread. Threats to leave may give you a lot of attention, but a lot of that attention will be negative. If you want help, ask for it.

By the way, what kind of CD are using to upgrade to 7.04? Is it a Desktop CD (not going to work) or an Alternate CD (will work)?

---

### Post by mbsnr on 2007-06-03
Thanks!  - Yes the original title wasn't very thought out at the time, but I have been so frustrated with the fact that the simplest things turn out to be so convoluted with Linux. I want to learn and use Linux but it's not making it easy. I *know* half the issue is the old hardware I have, but it does appear to me that the Linux way of doing certain things just doesn't use a common sense approach in some respects.  

Take PPP dial up as a prime example. Is there a built in utility that enables me to dial an ISP and see my connection time & data download status? I am absolutely amazed that this is seemingly not in Ubuntu (or some other distos of Linux I have used) by default.  Again how do you install the utility it if you can't connect to the internet in the 1st place.....? I can add the modem monitor to the top panel but both the activate/deactivate are greyed out even though my modem has been detected and is correctly configured.

With regards to the upgrade -  I have the install 7.04 CD not the Alternate CD. What is the alternate CD and how do I go about obtaining it? I have access to the internet at work. Can I download an ISO image?

Thanks in advance.

---

### Post by Bartender on 2007-06-03
"Ubuntu - Linux for human beings who aren't on dial-up"

Those of us stuck with dial-up have been squawking about the problems but I think it's only going to get worse instead of better.
Modem Monitor hasn't worked since Dapper.  They haven't fixed it.  If it's not going to be fixed they oughta remove it.  The present situation is lame.

GnomePPP is supposed to work fairly well, but you've gotta have internet to get the program so you can go on the internet!

Even if you get everything configured correctly at your location, is your ISP going to cooperate when you're online for hours with no "activity"?  Most dial-up ISP's will cut you off after a coupla hours.

---

### Post by jhenager on 2007-06-03
> **Bartender said:**
> "Ubuntu - Linux for human beings who aren't on dial-up"


Sadly, this is not inaccurate.
I have been in technical support since 1993, am Cisco and Microsoft certified, yet cannot get a winmodem to work.
Tried martian.
Tried wvdial.
Tried everything I can think of.

I wouldn't really care but I am hoping to get this box to where it can see the modem and dial out, so I can give it to my mom. She has no plans to go to broadband ever.
I have an Agere modem, and the 
[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)
is no help.
BTW, being on 2.6.20 kernel will not help either.
Brand new install of 7.04 and all updates have run.

---

### Post by mbsnr on 2007-06-04
Nice to see it's just not me having these dial-up issues (As I write this on a XP PC...)!!

Interestingly dial-up isn't an issue with Windows updates. I use MBSA in cmd line mode to generate a security report and then manually download the updates at work.

Does anyone know if this process can be done with Ubuntu? Is it possible to generate a listing of the updates and then manually download them? If so, how would they be applied?

---

### Post by karenslfs on 2007-06-06
Sorry I have to agree dialup connection people seem to be all but banned from "upgrading".???

I've got ppp working with sudo pppconfig then use pon & poff but of course this effectively means I can't upgrade from 6.10 to 7.04??

I have had you kindly mail me the desktop 7.04 cd but it's not the "alternate" which seems to mean I can't use it to upgrade. Is it even possible to ask for the "alternate" CD or is it only available via the net?? if so dialups can't access it.

Given that the basic install needs lots of work after install to make good system, mp3,mplayer, codecs etc etc (all very slow via dialup remember) no complaint as such, but to have to go through it all again for no good reason?? I'm hesitant to just reinstall 7.04.

A shame really debian based & all; then drops the ball at the line.

Karen

---

### Post by mbsnr on 2007-06-07
Karen - I got hold of the "alternate" CD - waste of time. I managed to get package manager to see it and inform me that there was a disto upgrade available from the CD. It informed me that 926 files needed to be copied (I was using 6.1 base install from CD) and it started to copy them. At 899 files it reset to zero and repeated. It did this again..... and I gave up.

I took it to a friends house with BB access.The 6.1 install informed me there were updates. I let it install them. It asked for a restart but instead of getting 7.04 as I expected - I got 6.1 (with all the updates...) - wasted 2 hrs there. Then package manager said there's a disto upgrade - I let it start. It's still running 4 hrs later. 

However I note that my power icon now thinks it's on permanent AC (again) which is why I decided to go the *upgrade* route in the 1st place, as the fresh install of 7.04 does this as well. So much for that idea. Looks to be a bug in 7.04 but I can't wait until it (is maybe) fixed and I notice there's 100's of bug posts about batteries on laptops anyhows. Not sure my 7 yr old laptop will jump the queue....

TBH with this old hardware, the lack of PPP/modem utilities, the fact that the sound doesn't work, I'm sad to say I'm giving up and I will be putting W2K back on it.  I feel like I've wasted a *lot* of time and effort. I haven't enjoyed Linux - in fact it's been a chore and frankly I've no intention of going back to it in the near future.  

Shame but there you go. I've tried Suse, PCLinuxOS and Ubuntu distos on a number of different laptops and none really work right.  I don't think I'm alone on being let down by the "Linux experience".

>>>>
Edit: 
Not that anyone really wants to know on a Ubuntu forum but I just got XP installed and *All* hardware detected ok on the laptop!

So erm what more can I say? Let's face it. Until Linux offers the ease of setup.exe on *every* program, instead of chmod 755 or some other convoluted install process, which involves consulting the internet and forums at every error you get, Windows is really going to win.

---

