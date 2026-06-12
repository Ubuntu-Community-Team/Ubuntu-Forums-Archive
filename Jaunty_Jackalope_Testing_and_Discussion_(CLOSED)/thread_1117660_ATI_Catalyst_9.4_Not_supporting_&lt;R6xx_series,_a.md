---
title: "ATI Catalyst 9.4 Not supporting &lt;R6xx series, and Mobility? / RadeonHD problems"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by proxess on 2009-04-06
Now, that Jaunty is running X 1.6. Seeing that it will only be supported by Fglrx 9.4 which in it self doesn't support anything older than the R6xx series (the HD series?), I was wondering where the Mobility GPUs fall into. I myself have a X2300 which is an M64 chip (rebranded x1350, M52). Is my M64 part of the R5xx or R6xx, or below?

Also, running, glxgears with RadeonHD completely hangs my PC.

---

### Post by nimes on 2009-04-06
yes. i have toshiba notebook with ati mobility radeon hd 2600. but this model  doesn't support  by latest fglrx driver. this is an important problem. and must be fixed quickly..

---

### Post by rbmorse on 2009-04-06
Have you tried the xserver-xorg-video-radeon driver? Withe the latest support packages in Jaunty it should be full-function for pre R6XX chipsets.

---

### Post by nimes on 2009-04-06
yes. i installed xserver-xorg-video-radeon and xserver-xorg-video-radeonhd. but my problem not solved. "Desktop effects could not be enabled" 

glxinfo :
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

i don't understand.^^..  

lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 [COLOR="Red"]VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series][/COLOR]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by screaminj3sus on 2009-04-06
I also have the mobility 2600 and the fglrx driver does "work" compiz is EXTREMELY slow (was fine in 9.2) is therew a way to get compiz with the opensource driver?

---

### Post by rbmorse on 2009-04-06
> **rbmorse said:**
> Have you tried the xserver-xorg-video-radeon driver? Withe the latest support packages in Jaunty it should be full-function for pre R6XX chipsets.

My error. HD2600 is an RV630. FGLRX should work.  Have you tried installing the repository version via restricted driver manager?  Note that the version in repository is a special beta version with xserver 1.6 support and differs from the drivers available directly from ATI.

---

### Post by screaminj3sus on 2009-04-06
> **rbmorse said:**
> My error. HD2600 is an RV630. FGLRX should work.  Have you tried installing the repository version via restricted driver manager?  Note that the version in repository is a special beta version with xserver 1.6 support and differs from the drivers available directly from ATI.

AFAIK the mobility radeon 2600 is different and is based on R520 though. Although jaunty's FGLRX does work with it it works pretty poorly for me.

---

### Post by ktp on 2009-04-06
I do have to say that ATI support has gone down hill in 9.04...even the open source drivers.  I mean I had no issues with open source drivers in 8.10, they seemed to work as good as fglrx.  But in 9.04, there seems to lots of issues with redraw...may its compiz but it's really slow.

---

### Post by crjackson on 2009-04-06
I have to chime in and say that ATI has abandoned too many of it's slightly dated cards. I'm about to remove Jaunty and go back to Hardy (AGAIN). The open source drivers are good to have, but just too darned slow for me.

What really bothers me is that only Intrepid/Jaunty will work out of the box with many mobile broadband USB dongles. I use these at work and have to boot into windows if I want decent responsiveness and mobile broadband.

Hardy is responsive but mobile networking just isn't there.

---

### Post by proxess on 2009-04-07
Can't play True Combat: Elite, Can't watch Videos with OpenGL rendering (all other outputs do terrible scaling), can't play Stepmania, it all either hangs after a while or doesn't start at all with the Radeon drivers (xf86-video-ati).

---

### Post by proxess on 2009-04-10
I mailed ATI tech support about the situation, this is the reply:

Although we have drivers for Linux posted on the ATI website, we do not provide technical support for driver or multimedia issues in Linux directly.

The Linux drivers available (For laptops, RADEON and All in wonder Products) from AMD are provided are "as is".

---

### Post by zika on 2009-04-10
> **proxess said:**
> I mailed ATI tech support about the situation, this is the reply:

Although we have drivers for Linux posted on the ATI website, we do not provide technical support for driver or multimedia issues in Linux directly.

The Linux drivers available (For laptops, RADEON and All in wonder Products) from AMD are provided are "as is".
nice and honest. that explains much ... :)

---

### Post by oldrocker99 on 2009-04-10
I used EnvyNG to delete all ATI drivers, then downloaded the 9.1 drivers. Compiz works, OpenGL works, all is well on my 4 month old Toshiba with an X1200.

:guitar:

---

### Post by proxess on 2009-04-11
But that's on Hardy or Intrepid, right? X Server 1.6 is on Jaunty only. Rolling back the drivers on other versions is of no problem. On Jaunty we'll have to roll back Xorg. I don't know what kind of effects that will have on the system in general.

---

### Post by MALEADt on 2009-04-11
<R600 support should be pretty decent with the open-source drivers. I'm happily playing Nexuiz on my X1600 (R520), with a full-blown compiz configuration while watching HD video's.
So instead of reverting to older versions of Ubuntu (Hardy, ugh), why not try to get the open source driver working? Pick a ubuntu version and make sure you use the newest drivers (tormod volden has a PPA with more recent drivers for Intrepid), and troubleshoot it. The IRC channel has many helpful people in it, launchpad is fairly responsive on driver issues, and the ubuntu wiki as well as the X one contains some troubleshooting guides to get the drivers working.

---

### Post by brendanpiater on 2009-04-11
Hi All,

Any idea if Mobility X700 will be supported with the 9.4 drivers? This would be a show stopper for me upgrading if not... and surely many many many others? I don't want to go backwards in performance! I still game on this machine.

Thanks
B

---

### Post by proxess on 2009-04-11
I'm pretty sure it isn't supported. My guess says that anything bellow the Mobility HD2400 is not supported. Correct me if I'm wrong.

---

### Post by brendanpiater on 2009-04-12
Hi there, you quite right... not supported. A list of cards and their respective chip sets can be found here;

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

The frustrating thing is that because Jaunty has chosen to use xserver 1.6, a fast majority of ATI users will suffer quite a large REGRESSION as the opensource drivers do not provide the same 3D performance as the propriety ones, yet.

I just find it a little disconcerting after two years of Ubuntu getting better with each release that it won't be fit for purpose! (for me & other ATI users at least...)

Is the jump move from 1.5 > 1.6 that beneficial that it's being put in above these concerns?

Surely if 1.6 must stay then we should have the option to downgrade to 1.5? But I hear this will most likely not work atm...

So it seems my options as follows;
> Stay at 8.10 till end of life (and then what??) or
> Loose current 3D performance and upgrade/use opensource driver (no thanks) or
> Buy a new laptop (this one is not even 3 years old yet!)

Is not one of Ubuntu's key selling points that it boosts performance on older machines? I.e. not a hardware killer like vista...

This is turning into a rant now, but I must say I'm just flabergasted. I was really looking forward to my upgrade this weekend and well, looks like it's not going to happen for me.

I know this is an ATI issue at heart, but as we cannot control their thinking/actions, surely we should have some work around in place to keep 3D performance AT IT'S CURRENT STATE, not regress.

Ok enough from me now.

Any suggestions would be be most welcome.

Cheers
B

---

### Post by MALEADt on 2009-04-12
> **brendanpiater said:**
> I just find it a little disconcerting after two years of Ubuntu getting better with each release that it won't be fit for purpose! (for me & other ATI users at least...)

I keep wondering why users seem to blaim Ubuntu for this... When one of the core parts of the Linux desktop gets an upgrade, it is absolutely normal a distribution ships this update. If this upgrade, combined with a decision from AMD, causes a performance loss for a minority of the users, too bad for them... You'd rather hold back an essential package to suit that minority? Then a way bigger group of users will complain about Ubuntu not being up to date enough...
Also, this so called quality decrease won't only apply to Ubuntu, but to _all_ distributions shipping 1.6.

I'm in the same situation myself right now, and I have to admit the open source driver can't really compete with fglrx when talking about raw performance. But it works remarkably well (compiz works fluently, I can perfectly watch HD videos, flash works, ...), apart from some obscure bugs which I'm doing my best to gather as much information about to pass to relevant developers. Normal desktop usage works perfectly, multimedia use works also very good (for the largest part of the users), "bling bling" works as well, only heavy 3D games have issues due to lower performance.

If you really care about the 3D performance, use the LTS release or just keep using 8.10 which both ship a compatible X server. And keep up good hopes that 3D performance might increase in Karmic (or 9.10), when Gallium gets introduced.

---

### Post by brendanpiater on 2009-04-12
Thanks for your reply, but just to clarify!

Not blaming Ubuntu, I do state that I know the root cause of the issue  is the ATI driver, but as we cannot control what ATI do...what about a work around!

And the obvious question for me was, is 1.6 essential? It will cause a regression for many users if it there is no option to downgrade to 1.5. I.e. Decreased 3D performance for all cards no longer supported by the new driver (and not fully supported by the open source driver). If 1.5 is fit for purpose, and can be used in Jaunty, it will mean that users like myself will be able to upgrade to Jaunty to get the full benefits of all the stuff like the ext4 file system which I'm really really looking forward to.

If the answer is yes, 1.6 is essential, then fine. Lets hope the open source driver catches up soon then everyone will be able to enjoy the Jaunty goodness.

Cheers
B

---

### Post by GerMulvey on 2009-04-18
Unfortunately ATI are the root cause - having paid a great deal of money only 3 years ago to find the driver support also the same in windows by the way stopped is out of order. It has basically put an end to Ubuntu for me. Just when everything worked so well. Unfortunately I loose all round. I can't use Ubuntu 9.04 - yes the opensource driver works but to a point. I tried the 9.3 and that was bye-bye xserver. So until I can afford a "newer" gpu I'm stuck in Vista. Also now my replacement is likely to be an Nvidia gpu.
Oh well that's progress I guess!

---

### Post by eldragon on 2009-04-18
people should stop complaining in the wrong place.


if there is anyone to blame, thats ati, not the kernel, not xorg, not even ubuntu are to blame, would you rather it ships with an oudated xorg server?

and well, considering amd isnt doing that well on the cpu market, and it is shooting itself to the foot with ati's support... i dont see a future for them. unless there is a radical change on how they treat their hardware. not only for linux's sake, but in general, amd is doomed.

how did sun strive? supporting OSS
how did ibm strive? supporting OSS
how did novel strive? scratching ms's back,err, supporting OSS ;)

so, amd/ati needs to pay more attention to the future, not the past. software monopoly is doomed. either open their drivers or help the os radeon driver group.

---

### Post by ktp on 2009-04-18
> **eldragon said:**
> so, amd/ati needs to pay more attention to the future, not the past. software monopoly is doomed. either open their drivers or help the os radeon driver group.

I think they are helping the open source drivers by releasing information about the cards (can't find where I read that).  This is one of the reason why the support for 3D in open source is expected to come soon.

---

### Post by markbuntu on 2009-04-18
Ati has provided information, personnel, and cash to the open source driver effort. The RV200-RV500 open source drivers have working 2D and 3D. Preliminary 3D for RV600 is available but not finished.

There is a lot of xorg.conf tweaking needed to dial in the open source drivers for individual cards. So, you need to do some searching to find the tweaks that work best for your card.

---

### Post by krazyd on 2009-04-18
> **markbuntu said:**
> There is a lot of xorg.conf tweaking needed to dial in the open source drivers for individual cards. So, you need to do some searching to find the tweaks that work best for your card.
This should no longer be true for the drivers in Jaunty. If it is, please file some bugs.

---

