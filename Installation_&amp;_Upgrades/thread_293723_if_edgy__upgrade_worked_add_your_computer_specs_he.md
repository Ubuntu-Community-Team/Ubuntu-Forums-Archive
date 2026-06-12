---
title: "if edgy  upgrade worked: add your computer specs here"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by tvst on 2006-11-05
**I thought this might be useful for people trying to upgrade.**
--------------------------------------

I'll start: I'm on a 5-year-old Dell Inspiron 8100 laptop. Here are the specs that should matter:

1GHz Pentium III m
512Mb RAM
1600x1200 screen
NVidia GeForce2Go 32Mb
D-Link AirXpert DWL-AG650 Wifi

My upgrade went on almost flawlessly. Since I knew there were people having trouble booting into X, I downloaded my video drivers from NVidia's site and put it on my home folder, for using in case of emergency.

Then I did a [FONT="Courier New"]gksu "sh /cdrom/cdromupgrade"[/FONT] using the Ubuntu Alternate CD. It took a few hours upgrading everything (around 5hrs!!).

On reboot, upstart worked (yay!) but X didn't. So I did a [FONT="Courier New"]Ctrl+Alt+F1[/FONT] and logged into the command prompt. Then I went to the place where I had saved my NVidia driver and installed it (you need to "[FONT="Courier New"]sudo[/FONT]", and you will also need to have the right linux-header package).

Since I was already on the terminal, I did an "[FONT="Courier New"]sudo apt-get update[/FONT]" followed by "[FONT="Courier New"]sudo apt-get upgrade[/FONT]" a few times, until there was nothing left to install.

After that, X booted normally.

The only thing now is that all my Python stuff (I do some Python development) is screwed, so I'm reinstalling my modules. No biggie, given the scary stories I've heard of Edgy.

Oh, and I also had to reinstall the Murrina theme, for some reason.

Hope it helps!

---

### Post by sproit on 2006-11-05
IBM T41

It's basically a pentium M banias with a 2200BG wireless card. Maybe intersting to mention that X still works like before, on a radeon 7500. Xorg driver: radeon
No problems after the update, some old problems were even fixed, probably because of the new kernel.

---

### Post by tvst on 2006-11-06
nice. let's keep this rolling.

---

### Post by rpkehoe on 2006-11-06
AMD 3000+
1gig ram
nvidia geforce 9300
dlink ma101 wireless

I upgraded from dapper to edgy pre-release, then to final release flawlessly with apt.

---

### Post by tvst on 2006-11-07
more!

---

### Post by scorp001 on 2006-11-10
Hi
Upgraded my system 2 days back...
Intel D815EEA2 mboard built in sound AC' 97 Audio
Nvidia Gforce3 64 mb
512 mb ram
Realtek / surecom network card
res: 1280x1024 
mon: LCD Samsunnnng Syncmaster 171s
4 hdd all seagate 7200 rpm Barracuda 80,80,200,400
sony dvd writer on usb 2 ide kit ;-)

Used Alternate CD for upgrade

In the morning i had trouble as cud not figure why the upgrade kept going to the net to download and upgrade...4 5 6 hours estimate is what i got...

left it upgrading and in the evening i saw - screen locked and my password not being accepted...rebooted and found x not coming up.

I had read a few days earlier while tweeking my desktop that using aptitude was the way to go - it is really far better than using apt-get...as nothing seemed to work i booted using the recovery menu and got into root shell...now was able to run aptitude and actually honestly ran it out of sheer frustration and what do u know - it actually saved me sooo much trouble - it said that my x was broken and shud run dpkg and some command i do not remember - but it worked like a charm and my system was back into action...

No it had not yet upgraded...I ran synaptic and it complained it cud not access the cdrom while i was running the upgrade thingy cdromupgrade script from the cdrom and checked to find it was called dvdrecorder and the cdrom link was pointing to cdrom0 - duh - and i was more one than anyone and saw the light. Yes and all the lovely invectives strike the mind lol.

created a new link pointing to dvdrecorder this time and took out the router power lol b4 i attacked the upgrade again - this time it used the cdrom properly and continued from where it had left b4 it stopped. It did install fully and i got a few updates and 1 library i had to remove by removing lives and then reinstalled transcode.

I am playing with xfce4 as well - which also got updated - but i found the 2.16 is certainly faster than 2.14 gnome but xfce4 is still faster.

I feel metacity is too dumb for everyday use [plus it slows gnome quite abit - switch the window manager and u will feel ur gnome on steroids] - so found that i cud not use xfce4 window manager - which i wud like to use since i already have xfce4-desktop but finaly found close enuf match with kwin - kde window manager. But i think there must be a way to get xfce4 wm to work with gnome - i dont like the shadows and fading and transparencies - they are a distraction i feel.

Now my only problem is that when i decode wmv video with mencoder i get a slanted warped raw video - any ans anywhere - it worked well in dapper and breezy,

cheers

---

### Post by cudaman73 on 2006-11-10
I upgraded my box from dapper to edgy flawlessly (almost) at home using debian's style of upgrading (editing sources.list and dist-upgrading), as I used to use debian, and that's what I'm used to.

Posted also in the 'bitch about edgy not working' thread.

AMD Athlon-xp 2500+ mobile barton
1 gig of ram
MSI K7N2 LSR (integrated nvidia ehternet)
nvidia 6800 (running two screens at 1280x1024)

four harddrives, 40/30 gig western digital, 200 gig maxtor, 20 gig samsung, 200 is the only sata drive.

Only had to dist-upgrade twice to catch all packages

---

### Post by el_itur on 2006-11-10
this are my specs from ubuntu's hwdb > 	Vendor: AuthenticAMD
Speed: 1830.245 MHz
Model: AMD Sempron(tm) 2600+ 	
		Memory: 515 MB
Swap: 1012 MB	
		Videodriver: "nv"
Colordepth: 24
Videomodes: "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
Videoram: 131072 kByte
	
 
I should say that my video card is an Nvidia FX5200.

Upgraded trough gksudo update-manager -c but I've took some regards.
I unnistalled the propietary nvidia driver since I knew there was a kernel upgrade and it will crash my X.
Commented out every non ubuntu repository even multiverse.
and uninstalled every KDE package I had, I wasn't using it anyway.

So, I dind't have any problem but my alsa driver, I've workaround it and filled a bug report. 

Best upgrade ever.

---

### Post by Fittersman on 2006-11-11
read my signature for my specifics

it actually makes direct rendering work now (when i type in glxinfo) i havent had the oppourtunity to test on a game yet though

---

### Post by gianpy69 on 2006-11-12
Edgy upgrade worked fine on my Acer Aspire 5633 Core2 Duo.

Cheers

---

