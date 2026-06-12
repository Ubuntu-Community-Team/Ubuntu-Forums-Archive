---
title: "Wacom under 10.04?"
date: 2010-01-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-01-17
Just wondering if anyone is trying this as I would really like to get one.

I also wonder if anyone trying this is using the xorg edgers stuff.  I have that on one of my installs and was looking through the synaptic "origin" list for that ppa and saw a listing for "wacom-utils".

---

### Post by AllRadioisDead on 2010-01-17
Check the lucid bugs, wacom's busted until final.

---

### Post by ranch hand on 2010-01-17
That is why I was interested it the "edgers" stuff.  All the bugs are for wacom-tools.  Although I was not sure that someone hadn't figured a way to get them to work.

I certainly am not very experienced in testing (or just running a stable version for that matter) but I saw in 9.10-testing some pretty impressive hacks to get things to work.

I still would like to know about the "edgers" crowd and what they may have discovered in that rather strange universe.

---

### Post by Favux on 2010-01-17
I don't think it's a bug, linuxwacom just doesn't work with X Servers 1.7 and later yet.  But you should/might be able to use [xf86-input-wacom 0.10.4]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom") for a compatible Xorg driver and linuxwacom for the usb kernel driver (wacom.ko).  In the meantime they are merging/synching the two.  But linuxwacom will keep the kernel driver.

---

### Post by ranch hand on 2010-01-17
> **Favux said:**
> I don't think it's a bug, linuxwacom just doesn't work with X Servers 1.7 and later yet.  But you should/might be able to use [xf86-input-wacom 0.10.4]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom") for a compatible Xorg driver and linuxwacom for the usb kernel driver (wacom.ko).  In the meantime they are merging/synching the two.  But linuxwacom will keep the kernel driver.
So is this what the xorg.edgers bunch is doing something with or are they just pounding sand?

---

### Post by Favux on 2010-01-17
Don't know, I haven't seen the xorg.edgers stuff(link?).  I know LWP dev.s just talked about seperating out wacomcpl into a seperate "wacom-utils" a few days ago.

---

### Post by ranch hand on 2010-01-17
The launchpad page is;

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I have this installed on 1 of 7 10.04-testing installs that I have.  My ATI video card is poorly supported and I thought I would see what this did.

As I prefer to run with the "effects" set at none the generic driver is fine with me but that is an install that is actually dedicated to ISO testing so it is a throw away install.

I was just browsing throw the "origin" section in synaptic and saw the "wacom-utils listing and just wondered about it as I had heard that was not going to work for a while in 10.04.

I do not have a tablet of any kind but would really like a wacom some time soon.  I am just watching how things develope and from what I hear it just gets better and better on stable releases.

Having caught the testing malady I thought I should check on what was happening in relation to 10.04 and related things.

Thanks for the link it was pretty interesting and I bookmarked it for further study.

---

### Post by Favux on 2010-01-17
It's looking like the inclusion of linuxwacom into Xorg (the Xserver part) is going fairly well and I think it'll be done in time for Lucid's release.  So it looks like things should be good for tablets.  The only possible gotcha seems to involve where the DeviceKit to udev-extras transition will be and what will be needed to configure the tablet.

---

### Post by ranch hand on 2010-01-17
Well I hope so.  I do not think that 9.10 is as bad as a lot of folks think but I spend most of my non-testing time on 9.04.  We still use 8.04 for secure transactions.  It would be great to be able to get a wacom and use it on the nest LTS.

I suspect that if the main stream xorg is not ready the xorg-edgers will be.  They actually have support for my card that allows me to enable "extra" desktop effects.  The regular driver will freeze on that setting.  I am impressed even though on this Lizard (there are folks that think 10.04 is Lucid Lynx but some of us know it is Lounge Lizard), which is my daytime production OS, the setting is "none" as it is on all the OS' I actually use.

---

### Post by ScislaC on 2010-01-18
I have not tested it yet, but how does the wacom driver from the following PPA work:

[https://edge.launchpad.net/~thjaeger/+archive/tabletpc/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid](https://edge.launchpad.net/~thjaeger/+archive/tabletpc/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid)

---

### Post by ranch hand on 2010-01-18
I do not know.  Do not have a wacom but want one soon.  This is the reason I posted this.

I was hoping that someone on this forum had tried it.

---

### Post by ScislaC on 2010-01-19
I just tested the wacom driver from that ppa and it was a no go. :(

---

### Post by ranch hand on 2010-01-19
That is a real bummer.

What kind of tablet do you use?

---

### Post by ScislaC on 2010-01-22
I have a Wacom Intuos 2. Luckily they uploaded a driver to the Lucid repo today that is working for me! I'd say it's safe to get your Wacom now!

---

### Post by ranch hand on 2010-01-22
That is great.  I have it on the way.

I have 8.04, 9.04, 9.10 and Mandriva 2009-1 on here too so I figured it would work.

There are scare stories out there that it will not work even after the release.  None looked credible to me but I knew there was a problem with it early on in 10.04.

As I am using this OS as my production OS during the day time I thought it would be nice if it worked now so I could try it.

Thank you very much.

Do have or have you tried an inking pen?  I think that this would be a great thing for my wife to use in doing jewelry designs for people and like wise for my Blacksmithing.

---

### Post by oldsoundguy on 2010-01-22
stick my nose into this tread to ask a question

Have an Intuos 3 that I tried to use in Ubuntu on and earlier build and it worked .. after much work in terminal.  With exceptions .. the sensitivity could not be dialed down and I could never get the airbrush to work.  (not the airbrush tool .. the actual hardware airbrush that Wacom sells.)

Have those issues been addressed? Would LOVE to be able to use it in Ubuntu!

---

### Post by tempo500 on 2010-04-26
hey,
im using 10.04. wacom intuos 3 is working, but i need to switch the buttons on my pen. wacom-properties.h looks interresting but i wouldnt know how to change it. my old way of switching doesnt work anymore. xsetwacom list gives me the typical stylus, cursor etc, but in upper case letters and xsetwacom set stylus Button3 "button2" wont recognise the device.

---

### Post by Krovas on 2010-04-26
> **ihermit said:**
> Check the lucid bugs, wacom's busted until final.

My old Graphire II works.

---

### Post by Favux on 2010-04-26
Hi tempo500,

They rewrote xsetwacom when they switched from linuxwacom to xf86-input-wacom as the X driver for Xserveer 1.7.  I think Lucid is currently using xf86-input-wacom 0.10.5 which came out 3-19-10.  Unfortunately the patches to fix button maapping came out 3-26-10, see:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=summary](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=summary)

If you cloned the latest git from the repository and compiled it I would think the button changes would then be there.

---

### Post by cheleb on 2010-04-26
> **tempo500 said:**
> ... my old way of switching doesnt work anymore. xsetwacom list gives me the typical stylus, cursor etc, but in upper case letters and xsetwacom set stylus Button3 "button2" wont recognise the device.

For some reason, the device aliases listed by xsetwacom (ERASER, CURSOR, PAD & STYLUS) don't work anymore. Though it works with the full device name (**everything before the alias**).

```
cheleb@larry:~$ xsetwacom list

**Wacom Intuos3 9x12 eraser** ERASER    
**Wacom Intuos3 9x12 cursor** CURSOR    
**Wacom Intuos3 9x12 pad** PAD       
**Wacom Intuos3 9x12** STYLUS    

cheleb@larry:~$ xsetwacom set "**Wacom Intuos3 9x12**" Button3 "button2"
cheleb@larry:~$ 

```

For e.g. the eraser, it would look like this:

```
xsetwacom set "**Wacom Intuos3 9x12 eraser**" Button3 "button2
```

Hope that helps

---

