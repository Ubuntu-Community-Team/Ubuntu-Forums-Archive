---
title: "Seriously, still with the b43-phy0 loop error??"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by ctsdownloads on 2008-04-24
I actually won a bet on this that it would slide through from Alpha, to Beta and onto the Hardy Heron main release:

[This error]("https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/188282"), marked here as closed, is still [very much alive]("http://sudan.ubuntuforums.com/showthread.php?t=685674&page=2").

Copied from the bug report:

> [ 949.312699] input: b43-phy0 as /devices/virtual/input/input25
[ 474.362628] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 474.362636] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).


This is not some usability error, this is a crippling, no-upgrade without notebook surgery kind of error. Seriously, I cannot begin to state aloud how tired I am of the community still trying to support a wireless card most people would be better off ignoring IMHO.

I have never bothered using that POS wireless card in the first place, as I always had the freedom to use my Ralink dongle which works quite well and does not loop my computer as to not even allowing me to use it....

Surely, for the love of life, there is a way to simply blacklist this stupid driver?? :mad:

Looks like it will remain a Gutsy notebook for the time being, unless someone has a solution of a means of blocking this stupid thing from loading?

*Before suggesting to simply download the unwanted driver or to use the alternative CD install, these have all been proven abysmal failures for this bug, thanks.*

---

### Post by jhmiller42 on 2008-04-24
Same deal with my old Averatec 3225HS. Happened with both 7.10 and now 8.04.

Ran the alternate install for 7.10, and while it installed, I spent over fifteen fruitless hours trying to get the wireless up and running -- ndiswrapper, fwcutter, the works. I'm not putting myself through that again.

---

### Post by ctsdownloads on 2008-04-24
> Same deal with my old Averatec 3225HS. Happened with both 7.10 and now 8.04.

Ran the alternate install for 7.10, and while it installed, I spent over fifteen fruitless hours trying to get the wireless up and running -- ndiswrapper, fwcutter, the works. I'm not putting myself through that again.

Actually, I am good without the Broadcom garbage chipset, never wanted or needed it supported. I have plenty of natively work wireless options..Ijust want to get the darn distro upgraded on my Averatec 3200.:(

---

### Post by jhmiller42 on 2008-04-24
Well, it's probably irrational, but I hate the idea of buying a discrete wireless card for a machine that works perfectly well under WinXP. Oh well.

Anyhoo, have you tried the alternate installer?

---

### Post by ctsdownloads on 2008-04-24
Having been through this before pre-release, I already know booting from any of the CDs (alternate or otherwise) fails with the same error. That said, I am going to [try this]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html").

The trick will be to see if it will have the same boot error. And sadly, this would be so preventable by simply providing a boot option to black list this - that is all that would be needed, but whatever.:roll:

---

### Post by ctsdownloads on 2008-04-24
To be honest, this is what drove me to buying a System76 notebook - quality control. See, they test all of this out, then repair crap like this so it is never passed onto their users. I just bought a Gazelle Value - worth every, single penny - and it is Intel wireless, so the Broadcom users can keep their damned b43 module! :)

Afterall, just because I fully support the distro does not mean I drink the koolaid completely. And let's be honest, it can be pretty buggy when compared to other distros.

---

### Post by Patsoe on 2008-04-24
I followed this advice: [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

Basically the guy puts up an init.d script that removes the b43 module and loads the ndiswrapper module. There are some other modules he's unplugging and replugging too.

---

### Post by ctsdownloads on 2008-04-24
> **Patsoe said:**
> I followed this advice: [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

Basically the guy puts up an init.d script that removes the b43 module and loads the ndiswrapper module. There are some other modules he's unplugging and replugging too.

This rocks, should you be able to get the notebook started....

It's a boot-stopping loop error, so some Broadcom chipsets can squeeze through, but some older ones will most certainly not. :)

---

### Post by ctsdownloads on 2008-04-24
Wait, just had a brain-fart - would it not be possible to get to a CLI and simply rmmod the stupid module from loading? I wonder, assuming of course, that the same loop error does not take place as I enter a non-X environment. Grrrr.

---

### Post by Patsoe on 2008-04-24
Oh. That sucks. Now I understand what you said about mentioning the alternate cd install. 

Anyway, I'll be voting with my money: no more Broadcom hardware if I can help it.

---

### Post by Patsoe on 2008-04-24
Actually, can't you temporarily disable the wifi card in the BIOS?

---

### Post by ctsdownloads on 2008-04-24
Yeah, I am even considering starting a fund called "*Based on Ubuntu* (trademark thing) - *Broadcom free Edition*", just so I can this notebook running. :guitar:

---

### Post by ctsdownloads on 2008-04-24
> **Patsoe said:**
> Actually, can't you temporarily disable the wifi card in the BIOS?

You would totally think so. ;) Yeah, these cheap Averatec 3200's do not offer something this helpful. And taking apart this model is really intensive as it is under EVERYTHING. :P

---

### Post by jhmiller42 on 2008-04-24
You ain't kidding. It was two hours of surgery to pull it apart to resolder the DC plug. You really considering physically removing the chip?

---

### Post by ctsdownloads on 2008-04-24
Nah, I have Ubuntu on my System76 notebook - going to put PCLinuxOS on the old Averatec...I hate to do it as RPM based distros make me want to toss my cookies, but I see little choice short of sticking with Gutsy. Downloading pclos-gnome2008. :)

---

### Post by ctsdownloads on 2008-04-24
Well, that ended badly (PCLinuxOS-GNome). Good thing I was dual-booting LinuxMint on that old notebook as a fall back.

---

### Post by rfs1970 on 2008-04-24
Hi there,

To solve this problem. get a pendrive (or a cd) and do that:

1) Download and save these files into your pen drive:
[b43-fwcutter.deb]("http://packages.ubuntu.com/hardy/b43-fwcutter")
[broadcom-wl-4.80.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2")

2) Insert this pen drive in the notebook that you cannot access the internet via broadcom wireless and then: 

a) Install the DEB file
b) unpack the tar.gz file: tar xjf broadcom-wl-4.80.53.0.tar.bz2
c) access the new folder: cd broadcom-wl-4.80.53.0/kmod
d) run the command: export FIRMWARE_INSTALL_DIR="/lib/firmware"
e) install the firmware: b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
f) run the command: sudo chmod 755 /lib/firmware/b43
g) restart your computer

That's it!
I hope it help you guys

For more details, access the original [Solution Source]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43#devicefirmware")

(In my case, I have a HP Pavilion - Wireless Broadcom model BCM4318)

---

### Post by ctsdownloads on 2008-04-24
> **rfs1970 said:**
> Hi there,

To solve this problem. get a pendrive (or a cd) and do that:

1) Download and save these files into your pen drive:
[b43-fwcutter.deb]("http://packages.ubuntu.com/hardy/b43-fwcutter")
[broadcom-wl-4.80.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2")

2) Insert this pen drive in the notebook that you cannot access the internet via broadcom wireless and then: 

a) Install the DEB file
b) unpack the tar.gz file: tar xjf broadcom-wl-4.80.53.0.tar.bz2
c) access the new folder: cd broadcom-wl-4.80.53.0/kmod
d) run the command: export FIRMWARE_INSTALL_DIR="/lib/firmware"
e) install the firmware: b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
f) run the command: sudo chmod 755 /lib/firmware/b43
g) restart your computer

That's it!
I hope it help you guys

For more details, access the original [Solution Source]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43#devicefirmware")

(In my case, I have a HP Pavilion - Wireless Broadcom model BCM4318)

Thanks for the how-to, so this is going to work when a *user cannot boot to the CLI* (command line) from both the mainline and alternate CD, am I correct?
 Just to be clear, this is an infinite loop problem that prevents any access to the live system and also prevents an install as well. So if getting to a CLI is not an option....not sure how I would be able to use this?? 

Thanks

---

### Post by Patsoe on 2008-04-24
Hey I just read here [http://www.debian.org/releases/testing/sparc/ch05s02.html.en](http://www.debian.org/releases/testing/sparc/ch05s02.html.en)
that you can pass b43.blacklist=yes as a kernel boot parameter. This is documentation for the debian installer - it should probably work for at least the alternate cd?

---

### Post by ctsdownloads on 2008-04-24
> **Patsoe said:**
> Hey I just read here [http://www.debian.org/releases/testing/sparc/ch05s02.html.en](http://www.debian.org/releases/testing/sparc/ch05s02.html.en)
that you can pass b43.blacklist=yes as a kernel boot parameter. This is documentation for the debian installer - it should probably work for at least the alternate cd?


Failed on a typical CD, but using the alternate might work, being that it is using the debian installer - thanks, will try this out.:)

---

### Post by ctsdownloads on 2008-04-25
It quickly flashed "unrecognized boot parameter" after showing what I had typed, this said, the Debian installer is installing - let's hope it will also boot after the install. If not, I would imagine I can just blacklist the damned thing the old fashion way.

If it installs, I can LiveCD anything else (Knoppix for that matter), mount the drive and browse to /etc/modprobe.d/blacklist in order to take care of this little b43 turkey. 

Again, thus far things are installing, but the boot parameter did not work. So far, so good. :guitar:


Edit: God this is getting ridiculous. Alternate Cd, after writing the partition tables it has frozen at 6% of the installation......

---

### Post by ctsdownloads on 2008-04-25
Well, this is just sad. Looks like Ubuntu's love for b43 has the best of this old Averatec notebook. Will have to find another distro that is not based on this distro unfortunately. 

I have tried every hack, boot parameter and magic trick I can think of, Heron is officially the release that stopped my long running notebook cold - congrats Broadcom! :(

Remember when I stated I bought another notebook preinstalled with Ubuntu? This is why, because of the fact that I can free myself from this nonsense once and for all.

I have to say, while I am excited to try Heron at some point, it may not be for another 5 and a half months. It was just not well thought out as many Broadcom users cannot even boot the damned disc.

---

### Post by Patsoe on 2008-04-25
> **ctsdownloads said:**
> Well, this is just sad. Looks like Ubuntu's love for b43 has the best of this old Averatec notebook.

Sorry to hear it didn't work, and yes, you're right. It's just very strange behaviour to have a driver insisting on the firmware showing up - obviously it's not going to magically appear after the first check. So basically this is an alpha-quality driver in an LTS release.

It would have made more sense if the system just said "sorry, due to your bad choice of hardware we can't set it up for you"... and then leave it to the user to build b43 modules or whatever they want to try.

---

### Post by ctsdownloads on 2008-04-25
Eh, I need to let it go. I have a new notebook where the company protects users from Ubuntu's development surprises. It has Gutsy 64bit and I could not be happier with it. I will however, wait until I speak with some people before upgrading it, however.

As for the old Averatec, it is still running it with Gutsy/Mint and will likely keep it there - no harm. But this is exactly why it is so helpful to buy preinstalled and with continuous support. Just glad I noticed the writing on the wall with my old notebook early on.

Thanks for the help. :)

---

### Post by louaym on 2008-04-25
I was having the same error message; the I told myself they should found work around already by now; so I start googling a round and I found that by installing "fwcutter" only; I solve it.
here what I have done:

- I connected my LAN wire to my Lappy and connected to the internet
- I ran (sudo apt-get install b43-fwcutter)
- while it installing it asked my that I need firmware to be downloaded and select YES to do so.
- I have selected YES and all done
- copied my manual interface config file from my 7.04 installation and rebooted.

and here I am posting using it. soon I will delete my old 7.04

good luck all.

HP Pavilion dv5002 laptop

---

### Post by jhmiller42 on 2008-04-25
> **ctsdownloads said:**
> Edit: God this is getting ridiculous. Alternate Cd, after writing the partition tables it has frozen at 6% of the installation......

That's odd -- that's exactly where my alternate install hangs, about half the time. I've tried installing maybe ten times now, and I've had it hang at 6 percent several times, 18 percent a couple, and once (friggin' tease) 42 percent.

And pre-emptively: I've burned the disc twice, on different burners, at 4X. Same result.

---

### Post by ctsdownloads on 2008-04-25
> **louaym said:**
> I was having the same error message; the I told myself they should found work around already by now; so I start googling a round and I found that by installing "fwcutter" only; I solve it.
here what I have done:

- I connected my LAN wire to my Lappy and connected to the internet
- I ran (sudo apt-get install b43-fwcutter)
- while it installing it asked my that I need firmware to be downloaded and select YES to do so.
- I have selected YES and all done
- copied my manual interface config file from my 7.04 installation and rebooted.

and here I am posting using it. soon I will delete my old 7.04

good luck all.

HP Pavilion dv5002 laptop

Appreciate the help, however as this thread is getting longer, I suspect the original explanation is getting lost in the shuffle.

This is not a compatibility/working wifi issue. This is an infinite loop that literally prevents some notebooks using select Broadcom chipsets from:

-Booting or installing from the regular Cd
-Installing from the alternate Cd
-The only boot parameter that might have helped to blacklist this using the alternate Cd, is not working - b43.blacklist=yes .

So to emphasize, nothing can be changed on a read only CD short of recompiling  nd recreating the distro without a seek to the problem module. That or some hardcore surgery to remove the problem chipset, which is not an option on my model of notebook.

Again, this is not an issue with an installed system. The bug prevents both live booting or installation with ANY Heron CD or alternate.

I really do appreciate the advice, but just wanted to save everyone time by rehashing what the actual error is.

Thanks everyone. :KS

---

### Post by ctsdownloads on 2008-04-25
> **jhmiller42 said:**
> That's odd -- that's exactly where my alternate install hangs, about half the time. I've tried installing maybe ten times now, and I've had it hang at 6 percent several times, 18 percent a couple, and once (friggin' tease) 42 percent.

And pre-emptively: I've burned the disc twice, on different burners, at 4X. Same result.

> **jhmiller42 said:**
> That's odd -- that's exactly where my alternate install hangs, about half the time. I've tried installing maybe ten times now, and I've had it hang at 6 percent several times, 18 percent a couple, and once (friggin' tease) 42 percent.

And pre-emptively: I've burned the disc twice, on different burners, at 4X. Same result.

Using a Broadcom chipset, by chance? If unsure, which notebook/model are you using. I feel your pain, btw. It's one thing not to work, I can get around incompatibility with a chipset. But to prevent an installation in the name of supporting a really poorly supported chipset is totally unwise in my opinion.

Based on my understanding, when the bug was so wisely labeled as "fixed", it was because two entire users had success with the 64bit alternate Cd. Cool, if you happen to have compatible architecture. :(

---

### Post by jhmiller42 on 2008-04-25
Yeah, it's an Averatec 3225HS with a Broadcom 4306.

The LiveCD didn't work with 7.10 either, but at least there the alternate CD did the trick.

---

### Post by ctsdownloads on 2008-04-25
> **jhmiller42 said:**
> Yeah, it's an Averatec 3225HS with a Broadcom 4306.

The LiveCD didn't work with 7.10 either, but at least there the alternate CD did the trick.

Averatec 3200 here - I am seeing a pattern here... hmm. :|

---

### Post by ctsdownloads on 2008-04-25
Here is where it stands for Averetec users at this point as far as I am concerned.

-Linux Mint Devs are now well aware of this issue, pre-their next release - maybe hope there.

-I am looking to Fedora 9 once it goes live on my Averetec, while happily using my well supported System76 notebook with Heron.

-Other may need to fork out to PCLinuxOS as it too, is a good alternative for some users.

Thank goodness for "distributions" of Linux! :lolflag:

---

### Post by Patsoe on 2008-04-25
Last option I just discovered, although I'm not really sure you'd want to try this: on the alternate cd, at the boot menu, you can hit F6 twice and it gives you the option to flag "Expert" install mode (hit space to select, then Esc and continue to boot). In Expert mode you can decide on any steps to take, modules you want to or don't want to load, packages to install... so you can skip the Broadcom stuff.

But then that's also the big downside: expert mode is giving you so much control that it's not nice anymore - I just went through a few steps and felt a bit uneasy :)

---

### Post by ctsdownloads on 2008-04-25
> **Patsoe said:**
> Last option I just discovered, although I'm not really sure you'd want to try this: on the alternate cd, at the boot menu, you can hit F6 twice and it gives you the option to flag "Expert" install mode (hit space to select, then Esc and continue to boot). In Expert mode you can decide on any steps to take, modules you want to or don't want to load, packages to install... so you can skip the Broadcom stuff.

But then that's also the big downside: expert mode is giving you so much control that it's not nice anymore - I just went through a few steps and felt a bit uneasy :)

Thanks for that. Well, all was well until select software - unfortunately, the term is a bit of an oxymoron as it selects whatever the hell it wants for you and just starts installing...lol. It was looking good for a moment there, but we are back to our friend - 6%.

and just tried again, this time with the Free Software only option...drum roll....it fails even faster at 2% installed! LOL.

---

### Post by dtgolder on 2008-04-26
This thread worked for me and got my Broadcom/NDISWrapper working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Look for the Hardy fix (almost at the end)

---

### Post by ctsdownloads on 2008-04-26
> **dtgolder said:**
> This thread worked for me and got my Broadcom/NDISWrapper working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Look for the Hardy fix (almost at the end)

Please re-read the problem. Again, I *genuinely appreciate the advice*, but I am unclear how much more clear I can make it - this is a "*_getting the distro installed" problem_*". This not an issue with compatibility, we are talking about a install/liveCD loop error that prevents installation or live booting.

[http://ubuntuforums.org/showpost.php?p=4793066&postcount=27](http://ubuntuforums.org/showpost.php?p=4793066&postcount=27)

Thanks everyone.

---

### Post by ctsdownloads on 2008-04-26
Had an obvious revelation. I am going to see about reinstalling Gutsy, then with the alternative Heron CD, running sudo /media/cdrom0/cdromupgrade .

In theory, after it installs, I should be able to then take the Gutsy CD again, then from the Liveboot, browse into the Heron blacklist area and make the needed hacks. Because Heron prevents running the release in any form on Averetec notebooks, this may be the best option.

---

### Post by Guilden_NL on 2008-04-26
> **ctsdownloads said:**
> Thanks for that. Well, all was well until select software - unfortunately, the term is a bit of an oxymoron as it selects whatever the hell it wants for you and just starts installing...lol. It was looking good for a moment there, but we are back to our friend - 6%.

and just tried again, this time with the Free Software only option...drum roll....it fails even faster at 2% installed! LOL.

Ditto.  And to the original poster, this appears to be related.  I have been running HH on a very complex hand built system with no wireless for over a month.  In fact, Dapper, Edgy, Fiesty and Gutsy all failed even with hundreds of hours of custom installs and plenty of loving.  Hardy whacked right in and has been a joy in Beta version.

I tried to upgrade to HH on another system after the LTS version was released and had a massive hang resulting in pulling the power cord.  Downloaded and attempted to blow away everything with a clean install of Hardy and keep seeing the same error about the Broadcom driver screwing up the kernel. On the alternate CD the thing hangs at 6% on the Select Software and Install.....

I believe that this is all related.

Reverting back to XP and sitting on the sidelines until this is worked out.  I have seven other systems to upgrade to Hardy, I can't remember which have Broadcom chipsets but some of them do.

Funny enough, this problematic PC had issues with Gutsy where I bought a Linux supported card but I never needed to install it because Gutsy installed and used the Broadcom card using NDISWrapper.  Maybe I can find the darned card in my meter deep pile of computer stuff.

I am very disappointed that the install routine doesn't allow you to skip networking. This PC is an anchor until I move back to XP.

Sad when Microsoft is the reliable OS that you have to fall back to on install.

This isn't a driver problem, it's a core issue of how the Ubuntu distro installs.  This **has** to change if we're going to increase our numbers. ](*,)

---

### Post by ctsdownloads on 2008-04-26
> **Guilden_NL said:**
> Ditto.  And to the original poster, this appears to be related.  I have been running HH on a very complex hand built system with no wireless for over a month.  In fact, Dapper, Edgy, Fiesty and Gutsy all failed even with hundreds of hours of custom installs and plenty of loving.  Hardy whacked right in and has been a joy in Beta version.

Despite my own mishaps with the install on my made for Windows notebook, I have to fault all of the hoopla surrounding false hope on getting made for Windows wireless hardware working; hence the bug we are fighting with now.

The reality is that Linux wireless is actually fantastic, once you fully understand that you need made for Linux wireless. Intel is your friend and if you need USB suggestions for a working dongle, no stupid revision numbers and it even lists Linux on the box, just let me know.


> **Guilden_NL said:**
> Reverting back to XP and sitting on the sidelines until this is worked out.  I have seven other systems to upgrade to Hardy, I can't remember which have Broadcom chipsets but some of them do.

Funny enough, this problematic PC had issues with Gutsy where I bought a Linux supported card but I never needed to install it because Gutsy installed and used the Broadcom card using NDISWrapper.  Maybe I can find the darned card in my meter deep pile of computer stuff.

Yeah, this is where I hold the select distro promoters responsible myself - tooting the horn of a really bad chipset in Linux, never a good plan. It's musical chipsets, off-again, on-again working headaches and so on, are what lead me to discovering how to step aside from the poor broadcom compatibility.

Some Ubuntu derivatives are so tired of hand-holding the Broadcom (nothing against the users), that they are talking about simply blacklisting it completely, leaving users to fend for themselves with NDISwrapper exclusively. I 110% agree with this, as it will force users to begin seeking out natively working alternatives.


> **Guilden_NL said:**
> I am very disappointed that the install routine doesn't allow you to skip networking. This PC is an anchor until I move back to XP.

Sad when Microsoft is the reliable OS that you have to fall back to on install.

This isn't a driver problem, it's a core issue of how the Ubuntu distro installs.  This **has** to change if we're going to increase our numbers. ](*,)

Heron is full of bugs, no argument there at all. And while I am largely "okay" with it thus far on my notebook recently purchased from a made for Ubuntu vendor, it is definitely not perfect.

But what is interesting is watching the two notebooks side by side. My older made for Windows one, trucking along, with band-aid solutions on Gutsy/whatever distro and my made for Ubuntu model, which has been 100% flawless, despite me being underwhelmed with most of the new features. After installing some needed extra for PulseAudio, I am definitely liking that feature. But other than that, it is not that big a shift in overall feel from Gutsy IMO.

All of this said, I believe I have finally figured out a work-around. It's totally overkill, but will post back if it works.

I agree about this being a core issue, btw. But the solution will piss off a number of users - letting go of the Broadcom nonsense. Unfortunately, everytime I post this, I tend to get flamed... :)

---

### Post by ctsdownloads on 2008-04-26
Okay, so here is how I plan to attempt a fix here.

1- Clean install of Gutsy - done.
2- In your terminal, enter:
   echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
3- Insert the Heron Alternate CD (32bit)
   it should prompt you for the upgrade, if not, run
   sudo /media/cdrom0/cdromupgrade
4- When it nags about not having the right repos or wanting to also update  
   via online, accept that your repos might not be perfect from the dialog   
   then choose NOT to use online updates.
5- Run the update, hope that this works - if successful, will post back.

---

### Post by Guilden_NL on 2008-04-26
> **Guilden_NL said:**
> This isn't a driver problem, it's a core issue of how the Ubuntu distro installs.  This **has** to change if we're going to increase our numbers. ](*,)

I could post nineteen paragraphs about trying to work around the alternate set up and where it got stuck on an inane piece, but after several deep breaths will let go....

Just because I am so honked off about how this mess of an install is, I decided to load SUSE because we run it on our son's laptop in a dual boot (he prefers SUSE with KDE) any my personal laptop in the same mode.  SUSE loaded on this PC with **_ZERO_**, zip, nada, none, no problems in 15 minutes.

Now I am not here to bash Ubuntu, I am running Gutsy on seven of them.  I am very unhappy with the install routine in Hardy; it's crap that is 100 levels below what previous Ubuntu distros have used.

I'm all for limiting distros to one every 18 months at most if this is a signal of what we can expect from Ubuntu going forward.

In all good faith, I cannot recommend Ubuntu to anyone running Windows or Mac and thinking about moving to Linux for the first time.  In fact, I don't recommend it for well seasoned Linux gurus either.  This is Microsoft DOS loader circa 1986, "please start over because we screwed up......"

---

### Post by ctsdownloads on 2008-04-26
> **Guilden_NL said:**
> I could post nineteen paragraphs about trying to work around the alternate set up and where it got stuck on an inane piece, but after several deep breaths will let go....

Just because I am so honked off about how this mess of an install is, I decided to load SUSE because we run it on our son's laptop in a dual boot (he prefers SUSE with KDE) any my personal laptop in the same mode.  SUSE loaded on this PC with **_ZERO_**, zip, nada, none, no problems in 15 minutes.

Now I am not here to bash Ubuntu, I am running Gutsy on seven of them.  I am very unhappy with the install routine in Hardy; it's crap that is 100 levels below what previous Ubuntu distros have used.

I'm all for limiting distros to one every 18 months at most if this is a signal of what we can expect from Ubuntu going forward.

In all good faith, I cannot recommend Ubuntu to anyone running Windows or Mac and thinking about moving to Linux for the first time.  In fact, I don't recommend it for well seasoned Linux gurus either.  This is Microsoft DOS loader circa 1986, "please start over because we screwed up......"

I hear ya, believe me, I do. And generally, I believe that Heron went backwards with non-certified hardware, I have a few suspicions as to why, but will not post them for a lack of proof. ;)

I have been talking at length with the Linux Mint people via the forums and discovered something: they stopped with Feisty, and have simply upgrade the kernel among other critical parts off of the same base, thus really watching its stability while staying cutting (not bleeding) edge.

So basically, take the Ubuntu core and whittling down all of the crap. I agree with your choice of OpenSuse, be it PCLinuxOS is not half bad either.

And while it pains me, I have found myself replacing some of my existing boxes with LinuxMint simply because I can literally ping the devs, complain and see results. :) I have heard the same with PCLinuxOS as well, but do not use the distro much.

And finally, I must agree - unless it is pre-installed, and having a company outside of me providing bug fixes like System76, I too would not be recommending this or future editions of Ubuntu unless the release cycle is reworked with better quality control and smarter priorities on the bugs themselves are put into practice.

All and all, we are on the same page.

..totally off topic, how is Suse 10.3? LOVED 10.0, hated 10.1, ignored 10.2, curious about 10.3. :)

---

### Post by Guilden_NL on 2008-04-27
> **ctsdownloads said:**
> ..totally off topic, how is Suse 10.3? LOVED 10.0, hated 10.1, ignored 10.2, curious about 10.3. :)

So far we've had zero problems with running 10.3 our son's Acer laptop, it loaded in a breeze and everything worked straight out of the chute.  I went with a dual boot Gutsy/SUSE 10.3 because I have Gutsy on 7 other systems at home running Gnome and our son wanted to play with KDE.  I figured since I was going to have to learn the ins and outs of KDE, I would also take a peek at SUSE at the same time.  First time I've run it and I am happy with it.

However, I have to say that the Ubuntu forums rock compared to SUSE support which seems to be hit or miss.  And that includes Deutsch support (I read Deutsch well, so no problems there. Just don't expect good grammar if I reply back to a post!:-# )

I don't have a problem with attempting backward support to legacy bits, but the install routine needs to allow easy blacklisting that works.  If I want to stick with an old Broadcom card, I'll pay the price through working through the mess _after_ install of the base and apps. After all, Windows provides this support, so doing so under Linux allows a change over.

Ah well, I guess that I'll have to volunteer some time on the Install to see if we can get that team on task.

---

### Post by ctsdownloads on 2008-04-27
> **Guilden_NL said:**
> So far we've had zero problems with running 10.3 our son's Acer laptop, it loaded in a breeze and everything worked straight out of the chute.  I went with a dual boot Gutsy/SUSE 10.3 because I have Gutsy on 7 other systems at home running Gnome and our son wanted to play with KDE.  I figured since I was going to have to learn the ins and outs of KDE, I would also take a peek at SUSE at the same time.  First time I've run it and I am happy with it.

However, I have to say that the Ubuntu forums rock compared to SUSE support which seems to be hit or miss.  And that includes Deutsch support (I read Deutsch well, so no problems there. Just don't expect good grammar if I reply back to a post!:-# )

I don't have a problem with attempting backward support to legacy bits, but the install routine needs to allow easy blacklisting that works.  If I want to stick with an old Broadcom card, I'll pay the price through working through the mess _after_ install of the base and apps. After all, Windows provides this support, so doing so under Linux allows a change over.

Ah well, I guess that I'll have to volunteer some time on the Install to see if we can get that team on task.

That rocks about SuSe, will have to get a DVD together later this week and try it out. :)

---

### Post by ctsdownloads on 2008-04-27
> **ctsdownloads said:**
> Okay, so here is how I plan to attempt a fix here.

1- Clean install of Gutsy - done.
2- In your terminal, enter:
   echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
3- Insert the Heron Alternate CD (32bit)
   it should prompt you for the upgrade, if not, run
   sudo /media/cdrom0/cdromupgrade
4- When it nags about not having the right repos or wanting to also update  
   via online, accept that your repos might not be perfect from the dialog   
   then choose NOT to use online updates.
5- Run the update, hope that this works - if successful, will post back.


As quoted above, it worked, my Averatec notebook was able to upgrade to Heron after all. 

Noted changes? 

-The issues with rt73usb being seen as rt2500usb has been fixed. You no longer need to blacklist rt2500usb which is cool. Signal strength issue remains, but it simply not a big deal for me personally. The issue is with this chipset, even standing in front of the access point provides a max of 75% signal. But I am still able to take my notebook across the house and outside without ever going down to a point to where it really degrades. If concerned, think Cantenea or [build something omni directional]("http://www.freeantennas.com/projects/Ez-10/"). I have never needed it, but some people would.

Everything else appears to work, still need to see what has been done to SANE and CUPS.
-

---

### Post by Patsoe on 2008-04-27
Your persistence is really admirable. Glad it worked!

---

### Post by ctsdownloads on 2008-04-27
> **Patsoe said:**
> Your persistence is really admirable. Glad it worked!

Thanks. :)

---

### Post by ctsdownloads on 2008-04-27
This might be something worth note, it appears (speculating) that those lock-ups people are enjoying is due to SATA I/O issues on Heron.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

My new notebook has an SATA drive I believe, so I will be watching for this. In some cases, you have to do a lot of R/W to the drive to get a nice, clean lockup. My old notebook however, is not SATA. Will keep everyone posted.

---

### Post by tattrat on 2008-04-27
I have also been struggling with this issue, and I also think it is much more complex than is perhaps thought. 

I have discovered, that the errors encountered are not consistent, although broadcom drivers appear to be involved. 

I discovered that the solution (on my system at least) for the lockup when booting the live cd, is simply to wait 5-10 minutes, and it eventually works; yes it does seem like an eternity when staring at a motionless screen. 

I then get the same lock up when booting the installed system. Waiting 10 minutes doesn't help. It's frozen to death. However I discovered that if you type CTL+ALT+DEL it will continue almost to the end. Another CTL+ALT+DEL, then (tragically) causes the system to reboot.

If instead I opt for the second item on the grub menu, I get the verbose start up. It turns out it is getting stuck trying to start SD card in my printer. If at this point I press CTL+ALT+DEL it gives me a screen offering:
    CONTINUE BOOTING
    RESTART
    CONFIGURE X MANUALLY

I opt for the first one, and it continues on its merry way. Sometimes it then freezes trying to get the mouse going. SOmetimes it frezzes up trying to get a DVB tuner card going, and sometimes it is with the broadcom drivers. (Before you ask why install and boot with these devices attached. it has not casued troubles with older releases or other distros). Once it carried on and booted successfully and then after blacklisting BCM43xx it would boot happily and speedily. Until I manged to trash the system. Now I am unable to get a fresh install to boot. 

The only other thing of I have noticed is that in under VMware it locks up on boot,  shutdown and whenever lsusb is typed, if any (logical) USB device is attached; previous releases work just fine. 

The plot thickens if you ask me.

---

### Post by Guilden_NL on 2008-04-27
ctsdownloads,
I finally was able to get Hardy to load with no splash, that itself was 20 minute ordeal (Hardy seems to have moved backward from Beta into Alpha.)  Yep, stuck on b43legacy-phy0: Broadcome 4301 WLAN found.

I'll dig through my boxes of 'puter stuff later and see if I can find that Linux/Ubuntu compatible wireless card.

If I can't find it, I'll try dropping back to Gutsy and going your selected route.

Sheez, you would think that this install routine was designed by Jim Allchin/Microsoft Vista Program Executive Leader. ](*,)

---

### Post by Guilden_NL on 2008-04-28
ctsdownloads,
I tried your path that you planned to take and ended up with a clusterf***k of a clean install of Hardy even with the blacklist of the BR43.

Crazy stuff like a broken install that reverts back to two distros previous..... Have now gone in with the intent of breaking anything and everything to force a clean install of Hardy.  Nope.

Hardy requires a wrecking bar, a hot temper and the need to rip hardware from your perfectly working Gutsy machine.

I have the mind to track down the idiot that closed the bug report and kick him 200 kilometers down the road of his choice.

Canonical is taking backwards steps and making Ubuntu fans into naysayers.  Shuttleworth needs to be a little more maniacal about quality; Ubuntu is quickly slipping backwards.

Kick ****, take names.  It works.  I do it every day and have it done unto me.  Accountability is what makes life happen.  Or not.[-X

---

### Post by Guilden_NL on 2008-04-28
> **tattrat said:**
> I have also been struggling with this issue, and I also think it is much more complex than is perhaps thought. 

I have discovered, that the errors encountered are not consistent, although broadcom drivers appear to be involved. 

I discovered that the solution (on my system at least) for the lockup when booting the live cd, is simply to wait 5-10 minutes, and it eventually works; yes it does seem like an eternity when staring at a motionless screen. 

I then get the same lock up when booting the installed system. Waiting 10 minutes doesn't help. It's frozen to death. However I discovered that if you type CTL+ALT+DEL it will continue almost to the end. Another CTL+ALT+DEL, then (tragically) causes the system to reboot.

If instead I opt for the second item on the grub menu, I get the verbose start up. It turns out it is getting stuck trying to start SD card in my printer. If at this point I press CTL+ALT+DEL it gives me a screen offering:
    CONTINUE BOOTING
    RESTART
    CONFIGURE X MANUALLY

I opt for the first one, and it continues on its merry way. Sometimes it then freezes trying to get the mouse going. SOmetimes it frezzes up trying to get a DVB tuner card going, and sometimes it is with the broadcom drivers. (Before you ask why install and boot with these devices attached. it has not casued troubles with older releases or other distros). Once it carried on and booted successfully and then after blacklisting BCM43xx it would boot happily and speedily. Until I manged to trash the system. Now I am unable to get a fresh install to boot. 

The only other thing of I have noticed is that in under VMware it locks up on boot,  shutdown and whenever lsusb is typed, if any (logical) USB device is attached; previous releases work just fine. 

The plot thickens if you ask me.

Sorry mate, but your problem is not related to the Broadcom wireless card driver killer problem.  It sounds like you might have to unrelated problems that are going to be tough to unravel.

Good luck with that!

---

### Post by ctsdownloads on 2008-04-28
> **Guilden_NL said:**
> ctsdownloads,
I tried your path that you planned to take and ended up with a clusterf***k of a clean install of Hardy even with the blacklist of the BR43.

Crazy stuff like a broken install that reverts back to two distros previous..... Have now gone in with the intent of breaking anything and everything to force a clean install of Hardy.  Nope.

Hardy requires a wrecking bar, a hot temper and the need to rip hardware from your perfectly working Gutsy machine.

I have the mind to track down the idiot that closed the bug report and kick him 200 kilometers down the road of his choice.

Canonical is taking backwards steps and making Ubuntu fans into naysayers.  Shuttleworth needs to be a little more maniacal about quality; Ubuntu is quickly slipping backwards.

Kick ****, take names.  It works.  I do it every day and have it done unto me.  Accountability is what makes life happen.  Or not.[-X

No question that allowing this to go through was not exactly their most brilliant moment, especially considering 90% of the time you would need NDISWrapper anyway.

That said, I had this working with the following:

A Clean install of Gutsy (and I mean brand spanking new), blacklist b43, not BR43 (case sensitive), did NOT allow any Internet connection during the process.

If was was done with a well used install of Gutsy, you are on your own man, sorry as updating always sucks - cross platform. ;)

---

### Post by Guilden_NL on 2008-04-29
> **ctsdownloads said:**
> If was was done with a well used install of Gutsy, you are on your own man, sorry as updating always sucks - cross platform. ;)
Nope, I did a full clean install with a complete format of the drive that Ubuntu is on.  Same old same old.

I gave it a breather and came home to a nasty gram from a mod here about my "cruddy cowpie" comments and photo, then had some young girl bash any of us having problems and a pile on after that.

I've decided that my seven systems are now going SUSE and to h_ell with Canonical and Ubuntu.  Read my posts, I am not nasty, not bashing Canonical against their competitors etc.

I don't live in a perfect politically correct world, I say what's on my mind and do it in a humorous and business like language.

If that doesn't fly here, then all I can say is "Ubuntu and Canonical were on the mass murderer list for Linux on the desktop."

See ya on the SUSE forums!

---

### Post by ctsdownloads on 2008-04-29
> **Guilden_NL said:**
> Nope, I did a full clean install with a complete format of the drive that Ubuntu is on.  Same old same old.

I gave it a breather and came home to a nasty gram from a mod here about my "cruddy cowpie" comments and photo, then had some young girl bash any of us having problems and a pile on after that.

I've decided that my seven systems are now going SUSE and to h_ell with Canonical and Ubuntu.  Read my posts, I am not nasty, not bashing Canonical against their competitors etc.

I don't live in a perfect politically correct world, I say what's on my mind and do it in a humorous and business like language.

If that doesn't fly here, then all I can say is "Ubuntu and Canonical were on the mass murderer list for Linux on the desktop."

See ya on the SUSE forums!

Seriously, they gave you a note because you were essentially frustrated? That sucks man as I tend to agree with ya. Sounds like the hardware is not playing ball with the distro. Heck, if SuSE is working, it beats Windows, right? ;)

---

### Post by Guilden_NL on 2008-04-29
> **ctsdownloads said:**
> Seriously, they gave you a note because you were essentially frustrated? That sucks man as I tend to agree with ya. Sounds like the hardware is not playing ball with the distro. Heck, if SuSE is working, it beats Windows, right? ;)
Yes.  I am a reasonable 50 yr old dude that doesn't slam to just vent.  I've posted that HH seems to have been a big step backward, I posted photo of a fresh cow pie, hence "cruddy cow pie" as my personal designation of this release.

Then the shrill girl pushed me over the top.  What Canonical doesn't understand is that personal users sometimes are change agents.  I am an Enterprise Architect for a very large global corp. We've been partnered with the normal companies, but are now looking into alternatives for the obvious reasons.  I just pushed through RHE on web app servers over MSFT.  It wasn't easy, but after 22 mos, it happened.  And we manage several million desktops.

SUSE/Novell looks better and better to me.  

Ubuntu needs to get a life, a sense of humor and better forums mods. 

Or kiss their corporate dreams goodbye.  Mark, do ya hear me or anyone else trying to help you?

---

### Post by tattrat on 2008-04-29
> **Guilden_NL said:**
> Sorry mate, but your problem is not related to the Broadcom wireless card driver killer problem.  It sounds like you might have to unrelated problems that are going to be tough to unravel.

Good luck with that!

It certainly is my friend! I think what others may learn from what I posted, is that if you are patient on booting the live CD, it will get through the problem. I have since managed to complete the install using the live cd, and when it prompts for a restart after the install, I opt for "continue using live CD" and at this point edit the /etc/modprobe.d/blacklist to ad "b43". I now reboot and it works. 

The reason it is clear to me that this is the same problem, is simple: the symptoms and circumstances are IDENTICAL (and replicable and also with alternate install). It is possible that the problem under VMWARE is different but it is certainly interesting to note. 

As for the native install I also experienced the lockup at 6%, when using the alternate install but again discovered that waiting a long time it goes through anyway. 

The reason that I say I think this problem is more complex is based on experience. Having spent decades debugging software, I know that if others have claimed to have a fixed a looping problem, yet it continues to affect others, and when you can interupt the loop it stops in disparate places, the problem is usually more complex than has been thought. 

But I would urge those who are getting this problem and who are still keen to install to wait at these lock ups - go have a shower or something - and you can get through, but remember to edit blacklist before first reboot.

---

### Post by subtex on 2008-04-30
> **ctsdownloads said:**
> As quoted above, it worked, my Averatec notebook was able to upgrade to Heron after all. 
-

YES!

I just did this on my Averatec 3200 and finally got Heron installed.  Thanks for this suggestion!

I haven't setup wireless yet or anything, but at least I'm on a useable desktop!

---

### Post by ctsdownloads on 2008-04-30
> **subtex said:**
> YES!

I just did this on my Averatec 3200 and finally got Heron installed.  Thanks for this suggestion!

I haven't setup wireless yet or anything, but at least I'm on a useable desktop!

Averatec users unite! :guitar:

---

### Post by bluerunner5 on 2008-07-17
You are my hero. I'm running the same laptop and have been looking for a fix.

---

