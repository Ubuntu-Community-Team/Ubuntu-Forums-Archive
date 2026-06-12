---
title: "will jaunty have a working fglrx ATI driver?"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-03-01
anyone know?

---

### Post by miegiel on 2009-03-01
Will the sun rise tomorrow ?

I'm not sure, but i have no reason to expect it won't :biggrin:

---

### Post by Rainstride on 2009-03-01
> **sdowney717 said:**
> anyone know?

i would say yes.

---

### Post by Nullack on 2009-03-02
Maybe the question should be, will AMD still actually be in business soon?

---

### Post by Stochastic on 2009-03-02
Personally, I've found Jaunty's newest ATI open source drivers to match/exceed Intrepid's fglrx capabilities (in a dual monitor setup).  I don't care if a closed source fglrx will be rolled out.

---

### Post by caryb on 2009-03-02
I cringe every time someone hands me a ATI or Intel Video carded PC to put Linux on:confused:


Cary

---

### Post by Sand &amp; Mercury on 2009-03-02
They'll get there eventually, either before Jaunty is out or somewhere early in its life cycle.

---

### Post by Lorenz on 2009-03-02
I really hope so, else I'll have to go back to Intrepid.

---

### Post by Martje_001 on 2009-03-02
AMD's fglrx developer, bridgman, says it probably is going to make it.

---

### Post by LordVeovis on 2009-03-02
> **caryb said:**
> I cringe every time someone hands me a ATI or Intel Video carded PC to put Linux on:confused:


Cary

I <3 my NVIDIA card... wierd though, my nvidia-settings app just crashed and I clicked report problem.  The report problem ran and took me to this post. Odd

---

### Post by Nullack on 2009-03-02
Until Intel come out with Larrabee, intel GPUs are a joke. That said, Intel are spending a fair bit on improving their linux gpu drivers.

---

### Post by Pitboss on 2009-03-09
> **Lorenz said:**
> I really hope so, else I'll have to go back to Intrepid.

Are you saying that you actually like the fglrx performance under Intrepid? I really hope that in Jaunty there will be a driver that supports 3d acceleration and doesn't leak my whole memory... Otherwise I plan ritually burning my HD 3600 :D

---

### Post by Lorenz on 2009-03-09
> **Pitboss said:**
> Are you saying that you actually like the fglrx performance under Intrepid? I really hope that in Jaunty there will be a driver that supports 3d acceleration and doesn't leak my whole memory... Otherwise I plan ritually burning my HD 3600 :D

I didn't really like it, actually. I always had to deactivate Compiz, because it messed up video output (and I watch lots of videos). But at least I could watch videos properly and scrolling worked nicely (it is really bad for certain pages now).

---

### Post by zika on 2009-03-10
if I were to upgrade from Intrepid to Jaunty at this moment what should I expect with AMD Phenom 9450X3 and with ASUS ah 3650 (a.k.a. ATI HD 3650) ...? I already do not us compiz, do not use ATI restricted driver 9.2 but, instead I'm using latest from tormod volden's ppa site i.e. xserver-xorg-video-ati (radeon). I do watch videos and that is all that I really use that is graphics-intensive.

---

### Post by Reiger on 2009-03-10
Put it this way: manually compiling & installing a radeonhd driver gives you a good resolution, fast enough 2d, next-to-no 3d, and some weird refreshment problems.

Using the distribution-channel drivers gives you a bumped up VGA resolution with stretch (1920x1200 dumbed down to 1600x1200 does not a pretty sight make), getting-there-slowly-speeds 2d, next-to-no 3d, and all kinds of semi-random weird refreshment issues which keep the entire system hostage (it is so poor you can't even keep a screensaver going).

Video card? HD4870 1024MB GDD5 if you want to know. Yes, I definitely eagerly await the day a closed source but working with reasonable 3d (as it used to on Intrepid) fglrx driver will become available. (Or that the radeonhd/other driver becomes mature enough to support my card more fully)

---

### Post by MilesRdz on 2009-03-10
From the looks of it, the open source driver shows more promise than the fglrx driver.

---

### Post by zika on 2009-03-10
but (even the latest, from tormod volden's ppa) radeonhd in Intrepid is not working with my card. would it work in Jaunty? with every answer I am more and more confused about the state of support for my card in Jaunty. it seems very gloomy ... :(

installed jaunty yesterday. compiz doesn't work but everything else does ... :) I do not miss compiz. needed to reinstall since my latest radeon open-source from tormod's ppa conflicted after upgared from Ibex and I thought it was less pain to reinstall than to explore. now I'm on defaults again .. ;)

---

### Post by fujikofujio on 2009-03-14
I pray all day that they will get it working so that i could run XBMC again on my pc. XBMC seems to work on jaunty on every computer I tried, except this one and it has an ATI card.

I really really hope they make it part of jaunty soon, might have to go back to Intrepid too. But really really love how snappy jaunty feels on this old box, and ext4 is a nice bonus too.

---

### Post by luvr on 2009-03-17
> **MilesRdz said:**
> From the looks of it, the open source driver shows more promise than the fglrx driver.

I think you're quite right. The proprietary driver doesn't work, and, in my opinion, never will. If I had any say in it, ATI would simply drop it, and concentrate on the open-source effort that's going on.

The open-source driver is awfully limited for now, and will remain so for a while, but I read somewhere (cannot remember where exactly, though) that it *"should"* finally get fully functional in time for the Ubuntu 9.10 release.

I gave 9.04 a quick test drive on a system with an nVIDIA graphics adapter, and the nVIDIA proprietary driver *seemed* to work quite nicely. I'm not too fond of it, though; some five or six years ago, it was my only option to get the X Window System operational on my then hardware, and it worked fine, but it had deteriorated as Linux evolved. It may have caught up again lately, but I cannot really trust that it will *keep* up this time.

I really prefer an open-source driver, just because its development will be better integrated with Linux kernel development. I do hope that we will see a great open-source driver for ATI graphics adapters sometime soon!

---

### Post by markbuntu on 2009-03-17
I am using the radeonhd driver from the repos on Jaunty with my HD3650 and it works for me and my 2 monitors, 24 inch 1920x1200 and 19 inch 1280x1024 on a big desktop . No 3D but I don't really care about that.

---

### Post by factotum218 on 2009-03-17
I'm betting on something being released. What it will be, who knows. I'd be astonished if it had anything to do with a mobility 3650 HD supporting full 3d acceleration.
I've actually posted on another thread about this card and so now my and a co-worker have wagered a bet. We are giving it a year. If any distro gets there we have to donate the amount of money we are wagering and run that distro for the next year, regardless of which it is.

Yes, we have no lives and are locked in out cubes. Send taco's.

---

### Post by zika on 2009-03-18
to answer the question made on the beginning of this thread: Yes. xorg-driver-fglrx is in You Synaptic.

---

### Post by raulih on 2009-04-17
I just installed Jaunty RC. xserver-xorg-video-radeon works ok. Proprietary fglrx seems to be unusable (extremely slow/nearly halts system). Is there any news in that area to get 3D working?

---

### Post by keypox on 2009-04-17
I guess we are all waiting for ATI to release their new driver 9.4 for linux

---

### Post by Martje_001 on 2009-04-17
> **raulih said:**
> I just installed Jaunty RC. xserver-xorg-video-radeon works ok. Proprietary fglrx seems to be unusable (extremely slow/nearly halts system). Is there any news in that area to get 3D working?
[http://www.phoronix.com/scan.php?page=news_item&px=NzE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzE5Ng)

Atm, no.

---

### Post by DougieFresh4U on 2009-04-17
I have AMD Athlon  dual core 5200 with ATI Radeon HD 3200 onboard graphics.
What is the proper driver from 'Synaptic' that should be installed? Will  'compiz' work ?
Also, how can I get 'fglrx' to work with the .30rc2 kernel?
Thanks for any input that can be provided.

---

### Post by uBeer on 2009-04-17
System > Administration > Hardware Drivers should do the trick. There is a preview of 9.4 already. My laptop is running it for 2 or 3 weeks and works fine.

---

### Post by DougieFresh4U on 2009-04-17
> **uBeer said:**
> System > Administration > Hardware Drivers should do the trick. There is a preview of 9.4 already. My laptop is running it for 2 or 3 weeks and works fine.

Absolutely not for the .30 kernel. Just get a nice colorful screen where login should be, if I can get that far.
Works fine for .28 kernel.

---

### Post by luvr on 2009-04-17
> **keypox said:**
> I guess we are all waiting for ATI to release their new driver 9.4 for linux
Yeah, right... And then, that won't work either, and we will all be waiting for their new driver 9.5 for linux.

Yeah, right... And then, that won't work either, and we will all be waiting for their new driver 9.6 for linux.

Yeah, right... And then, that won't work either, and we will all be waiting for their new driver 9.7 for linux.

...

I have a better idea: Let's all wait for a good-working, full-function **open-source** driver. The open-source driver *is* improving (albeit slowly), and I'm betting that it will, one day, actually **work**--and sooner, much sooner, than the proprietary crap they keep releasing.

In fact, the functionality that the open-source driver *does* support, works fine, and I wouldn't want to see the quality of the driver deteriorate just because any new features that it collects are horribly buggy.

I prefer a high-quality driver *tomorrow* (or even the day *after* tomorrow) over a crappy one *today.* After all, if I want to see crap in action, I can simply install the proprietary driver and be done.

---

### Post by eldragon on 2009-04-17
> **luvr said:**
> Yeah, right... And then, that won't work either, and we will all be waiting for their new driver 9.5 for linux.

Yeah, right... And then, that won't work either, and we will all be waiting for their new driver 9.6 for linux.

Yeah, right... And then, that won't work either, and we will all be waiting for their new driver 9.7 for linux.

...

I have a better idea: Let's all wait for a good-working, full-function **open-source** driver. The open-source driver *is* improving (albeit slowly), and I'm betting that it will, one day, actually **work**--and sooner, much sooner, than the proprietary crap they keep releasing.

In fact, the functionality that the open-source driver *does* support, works fine, and I wouldn't want to see the quality of the driver deteriorate just because any new features that it collects are horribly buggy.

I prefer a high-quality driver *tomorrow* (or even the day *after* tomorrow) over a crappy one *today.* After all, if I want to see crap in action, I can simply install the proprietary driver and be done.

forget it, the promises are there, but there will never be an open source ati driver. if there are licensing issues with the binary blob, they should hire a separate team to develop open source drivers...they already have an eager comunity willing to debug / test / help. instead they keep developing these blobs and in the process dropping support for older (not quite) hardware. ive actually lost faith.

if they wait till the userbase is big enough, it will be too late, users will already have shifted to competing vendors. gaining their trust again will be tough. ive flipped to ati a couple of years ago, and feel really disappointed. when i had the chance to get a notebook, i looked into intel graphics just cause their drivers are open source and actually evolve with the community..no wonder its the first driver to support KMS. again, thats me not gaming. for gamers, intel is a no-go.

anyway, good luck with that defective piece of hardware

---

### Post by luvr on 2009-04-17
> **eldragon said:**
> forget it, the promises are there, but there will never be an open source ati driver.
To be honest, I agree that that remains a real possibility indeed; I'm certainly not holding my breath.
Without a working open-source driver, they will lose me as a customer, though--and I won't be coming back. I'm not it a hurry to throw them out, but if any of my current hardware breaks, or is in urgent need of a replacement for any other reason, I'll choose Intel graphics (unless ATI has become a valid option by then).

> if they wait till the userbase is big enough, it will be too late, users will already have shifted to competing vendors. gaining their trust again will be tough.
Exactly! We're clearly on the same page about this.

> ive flipped to ati a couple of years ago, and feel really disappointed.
The same goes for me.

> when i had the chance to get a notebook, i looked into intel graphics just cause their drivers are open source and actually evolve with the community
I got a notebook with an Intel graphics chip, too, albeit more by accident. I wasn't really looking for a notebook just yet, but then a colleague of mine had bought a Dell Studio 17, and found it too big for his purposes. He let me try out Ubuntu on it, and I liked it, so I bought it from him. It was a great buy! (He subsequently bought a Studio 15 instead, which fits him much better.)

> for gamers, intel is a no-go.
For now, yes, it is--but I'm confident that Intel will be doing something about this in the not-too-distant future. (I'm not a gamer either, so I don't really care that much, though.)

> anyway, good luck with that defective piece of hardware
That is, assuming that I will keep it... ;-) Which will depend entirely on ATI. I will gladly leave it up to **them** to make up my mind!

---

### Post by crjackson on 2009-04-17
I have 12 desktop PC's and 4 laptops at my house. I still need to convert 3 of my desktops to nVidia (they used to be ATI but I gave up). One laptop has ATI (works great with hardy and ATI blob), the other laptos have nVidia/Intel.

The ATI and the Intel won't run Intrepid smoothly due to graphics drivers. The ATI won't run Jaunty smoothly for the same reason. I haven't tried Jaunty on the Intel or nVidia laptops yet (except for the A6 liveCD which worked very well).

Gutsy, Hardy, and Intrepid all work well with the ATI desktops.

Jaunty RC works well with the nVidia powered desktops. No issues at all so far.

I'll be keeping Hardy on one Laptop. And moving everything else to Jaunty as soon as my 3 remaining desktops have the ATI junk removed and replaced with nVidia.

---

### Post by Sandsound on 2009-04-17
I can understand the frustration with ATI.

I had many problems with ATI-cards in breezy, so I have been using Nvidia for a long time. but when my Nidia card broke down last month, I bought a Radeon 4830, hoping that the release of their documentation would further the development of a stable open-source driver, and thou it IS getting better, it's not quite there yet, but I haven't lost hope.

I read a blog post (dated April 8th) by Ian McNaughton on AMD's website about catalyst 9.4 that said "the driver is available on or about April 17th" so I've been checking the driver site all day.

In fact.. just before clicking "submit reply" I checked their site, AND IT'S THERE NOW :D

EDIT : [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English")

---

### Post by crjackson on 2009-04-17
> **Sandsound said:**
> I can understand the frustration with ATI.

I had many problems with ATI-cards in breezy, so I have been using Nvidia for a long time. but when my Nidia card broke down last month, I bought a Radeon 4830, hoping that the release of their documentation would further the development of a stable open-source driver, and thou it IS getting better, it's not quite there yet, but I haven't lost hope.

I read a blog post (dated April 8th) by Ian McNaughton on AMD's website about catalyst 9.4 that said "the driver is available on or about April 17th" so I've been checking the driver site all day.

In fact.. just before clicking "submit reply" I checked their site, AND IT'S THERE NOW :D

EDIT : [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English")

Which is cool if you have a fairly new ATI video device, but doesn't help those of us who fall into the "Support Discontinued" Catagory. I would gladly upgrade to a supported device if it worked well with these drivers, but that's not an option for laptops.

---

### Post by SigmaSanti on 2009-04-17
> **caryb said:**
> I cringe every time someone hands me a ATI or Intel Video carded PC to put Linux on:confused:


Cary

I know how you feel, I have an integrated intel card that causes me trouble, but nvidia has turned on me when I bought my new motherboard with an integrated 8200, that thing has only brought trouble to me (and several others);

---

### Post by PGHammer on 2009-04-17
> **crjackson said:**
> Which is cool if you have a fairly new ATI video device, but doesn't help those of us who fall into the "Support Discontinued" Catagory. I would gladly upgrade to a supported device if it worked well with these drivers, but that's not an option for laptops.

Folks, if you have X1K or older chipsets (including the Mobility Radeon counterparts back to the original Radeon), you can still use the open-source radeon (NOT radeonhd) server, which was designed with these chips in mind.  HD2000 and above can use the radeonhd server (2D only) or the FGLRX proprietary (Catalyst 9.4) server.

Further, the Catalyst 9.4 server *does* support the Mobility Radeon versions of the HD2000 and above; I have an HD3450 in PCIe; despite the fact that I'm using it in a desktop, the GPU itself is actually recognized, both by Catalyst and the open-source radeonhd server as the *Mobility Radeon* HD3450.  (I'm using the FGLRX driver in Jaunty right now.)

---

### Post by PGHammer on 2009-04-17
> **SigmaSanti said:**
> I know how you feel, I have an integrated intel card that causes me trouble, but nvidia has turned on me when I bought my new motherboard with an integrated 8200, that thing has only brought trouble to me (and several others);

Here's the breakdown for ATI's chipsets:

RAGE series and older (includes RAGE II+): open-source ati server
Original Radeon through X1K (including Mobility Radeon varants of these chips): open-source radeon server
HD2000 and later: open-source radeonhd server (2D-only) or Catalyst 9.4 from Canonical restricted-driver repo (includes 3D/Compiz and GLX/Xv acceleration support)

All personally tested.

---

### Post by Mazza558 on 2009-04-17
The Open Source ATI driver works brilliantly on my Laptop with mobile ATI graphics and has done since Intrepid. I don't know why it doesn't work for others. 

It has blazing 2D rendering and decent 3D, and can only improve from here.

---

### Post by crjackson on 2009-04-17
> **Mazza558 said:**
> The Open Source ATI driver works brilliantly on my Laptop with mobile ATI graphics and has done since Intrepid. I don't know why it doesn't work for others. 

It has blazing 2D rendering and decent 3D, and can only improve from here.

It craws like a snail on my Radeon Mobility 9600 - Video Playback tears, 3D Games are unplayable mostly, 2D desktop performance is shameful.

Blazing Fast on Hardy with the Proprietary blob installed.

---

### Post by Mazza558 on 2009-04-17
> **crjackson said:**
> It craws like a snail on my Radeon Mobility 9600 - Video Playback tears, 3D Games are unplayable mostly, 2D desktop performance is shameful.

Blazing Fast on Hardy with the Proprietary blob installed.

Is your rendering set to XAA or EXA in xorg.conf?

---

### Post by naveensn on 2009-04-17
I installed Catalyst 9.4 on Jaunty (64 bit) and it seems to work well. DVD would not play properly and would crash earlier with compiz enabled, but now it seems to work.

---

### Post by DougieFresh4U on 2009-04-17
I have an AMD Athlon dual 5200 with onboard 'ATI Radeon HD 3200'
What can I do , or install to get compiz? I am using the .30rc2 kernel and the 'fglrx' is not an option as it won't work with that kernel yet.
I would be glad for any help.
Thanks

---

### Post by Reiger on 2009-04-17
The `official' 9.4 is a lot better for me than the `beta from the repositories':
(a) Enabling/Disabling compositing Just Works. With the beta enabling used to work only after the card had `warmed up' so to speak (requiring several reboots before it would work, though it worked consistently `that way'). However, [partially] disabling afterwards never worked on the beta (which meant no wine for me).
(b) Faster. From KDM login to fully working KDE takes about as much time as to type a password.
(c) Log out is smoother too.

---

### Post by Martje_001 on 2009-04-18
> **eldragon said:**
> forget it, the promises are there, but there will never be an open source ati driver. if there are licensing issues with the binary blob, they should hire a separate team to develop open source drivers...
They already do.. and all the documentation is availalbe, so help us code.

---

### Post by yellerKat on 2009-04-18
> **Sandsound said:**
> 
...
In fact.. just before clicking "submit reply" I checked their site, AND IT'S THERE NOW :D

EDIT : [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English")
...


Thanks for that; installed and it works pretty well. Just the faintest bit of tearing if I wave a window about on the desktop (so I won't!) and the very odd artifact popping up.

---

