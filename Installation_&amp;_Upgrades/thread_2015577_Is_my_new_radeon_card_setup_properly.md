---
title: "Is my new radeon card setup properly?"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by freakzilla on 2012-07-03
I switched out my old nvidea geforce card and put in my new ati radeon hd 6450.  I activated ati/amd FGLRX driver using "Additional Drivers" under system settings.  The "post-release updates" driver did not work.

It seems to be working fine but under System Settings>Details>Graphics it reads "Driver  VESA:CAICOS" and "Experience Standard".

Does the "Driver VESA:CAICOS" mean its not using the FGLRX driver that shows active?  I'm a bit confused.

I'm running 12.04LTS 64bit.

---

### Post by QIII on 2012-07-03
The fglrx-updates and fglrx-amdcccle-updates packages have been troublesome for some users.

Using the additional drivers installation method has also been troublesome.

"Caicos" is AMD's name for the graphics processor used in your card.

You may want to remove the -updates packages if you haven't already.

```
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
```and follow the instructions in the ATI driver link in my signature.  I put a section in the wiki titled something like "Alternate command line method with acceleration" or something like that.  Look there and let me know what you think.

---

### Post by coffeecat on 2012-07-03
@freakzilla, my advice would be not to bother with the proprietary driver at all. The system I am posting from atm:

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]
```

Same GPU as yourself. I'm running 12.04 with the open source radeon driver and getting Unity 3d and good dual-monitor support.

---

### Post by QIII on 2012-07-03
> **coffeecat said:**
> I'm running 12.04 with the open source radeon driver and getting Unity 3d and good dual-monitor support.

The open source driver has come a looooong way in a short time, hasn't it!  I have nothing but good things to say about the developers working on it.

---

### Post by coffeecat on 2012-07-03
> **QIII said:**
> The open source driver has come a looooong way in a short time, hasn't it!  I have nothing but good things to say about the developers working on it.

+1

I find it makes life so simple. Install Ubuntu, ignore the pestering from Jockey to install the fglrx driver, enjoy! :)

---

### Post by QIII on 2012-07-03
Unfortunately for me, I do a lot of BOINC stuff using the ATI client, so I have to use it.

---

### Post by efflandt on 2012-07-03
Did you Deactivate nvidia driver before installing the ATI card and activating its drivers.  Not sure if Activate for ATI drivers automatically deactivates and removes nvidia (probably does), but you would have to reboot for a video driver change to take effect.

The only non-legacy ATI video I have is ATI HD video on a tablet PC, which seems to work fine considering that the CPU is AMD C-50 with 2 cores at only 1GHz (booting 64-bit 11.10 from SD)

---

### Post by freakzilla on 2012-07-03
QIII I followed your wiki instructions and I didn't run into any snags.  But I still get the "Driver VESA:CAICOS  Experience Standard" message.  Maybe the VESA:CAICOS message doen't mean the driver isn't being used.  

What is "standard experience" mean anyway?

Sudo vainfo output: 

libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

I didn't deactivate the nvidia driver before swapping out cards.

---

### Post by QIII on 2012-07-03
Don't worry about the Caicos message.  That is just telling you the graphics chip name.

If you did not first remove the NVIDIA driver, you will need to remove both the NVIDIA driver and the ATI driver, then reinstall ATI.

I guess I need to bold that part in the wiki.  It's probably easy to miss.

---

### Post by freakzilla on 2012-07-03
I followed the "sudo apt-get remove --purge fglrx fglrx-amdcccle" command outlined in your wiki.  I figured that removed the old ati stuff.

Is there a similar command to remove nvidia drivers?

---

### Post by QIII on 2012-07-03
Off the top of my head I believe it is

```
sudo apt-get remove --purge nvidia-current
```

---

### Post by freakzilla on 2012-07-03
Purged the ati+nvidea before following steps but still getting VESA.  Is it possible that System Settings>Details>Graphics is reporting the wrong thing even though the ati driver is being used?

---

### Post by msammels on 2012-07-03
Just working off a whim here. Sorry if this makes no sense, it's early morning here.

Have you tried popping in your nVidia card, deactivating all restricted drivers, shutting down the system and switching cards out? You've already purged the nVidia drivers - unless noveau is still there, but maybe that could work?

---

### Post by QIII on 2012-07-03
He's past that already...

---

### Post by msammels on 2012-07-03
Very odd - have you tried purging the ATI drivers, nVidia drivers and downloading the relevant ATI drivers from the website, and installing that way? Or using something like synaptic?

---

### Post by QIII on 2012-07-03
He's beyond that, too.

---

### Post by QIII on 2012-07-03
@freakzilla

If you go to System Settings, click on Additional Drivers in the Hardware section, do you get something that looks like this, with 

"This driver is activated and currently in use"

---

### Post by msammels on 2012-07-03
Honestly, I'm stumped. Above and beyond anything all I can recommend now is move /home to a new partition and reinstall, but that is the absolute last resort.

---

### Post by QIII on 2012-07-03
@msammels

Have you read the thread?

I have this.  OK?

I know you are trying to be helpful.

---

### Post by msammels on 2012-07-03
@Qlll

Yeah, I've read it :) Just trying to think of anything else.

---

### Post by QIII on 2012-07-03
There is little else to think of.

At this point, I believe the poster has the driver installed and running.  I have given him a check to reassure himself.

"Blast off and nuke 'em from orbit" by reinstalling is not even a consideration here.

Again, I know you are trying to be helpful.

---

### Post by freakzilla on 2012-07-03
When I check the Additional Drivers in the Hardware section.  I do get the "This driver is activated and currently in use" message.

---

### Post by QIII on 2012-07-03
Then you are golden.  Your driver is working.

The message that was of concern to you is just indicating, correctly, that your card is a Caicos GPU, AMD/ATI's name for that product.  You will be getting a "Standard Experience" because this is not a high-end card.  That's why I was trying to steer you away from getting wrapped around the axle over that message.

Check [this]("http://www.tomshardware.com/reviews/radeon-hd-6450-caicos-blu-ray-3d,2920.html") out.

---

### Post by freakzilla on 2012-07-03
Great, sorry for the long thread for a simple answer.  I was just confused when I read "Driver VESA:CAICOS".  The VESA part threw me.

---

### Post by msammels on 2012-07-03
And I apologise for my lack of reason here... like I said it's early morning and my brain is everywhere :P but yeah... sorry...

---

### Post by QIII on 2012-07-03
@freakzilla

No problem.  That's what we're here for.

I like to take a "one step at a time" approach when I can.  That's part of the reason this was a little long.

Firing off a laundry list of "do this, that and the other and Presto!" is confusing and often counter-productive.

I come off as grumpy, but I'm generally not.  Spent 24 years in the Army.  I can sometimes be, uh, blunt?

---

### Post by msammels on 2012-07-03
@Qlll

Haha, not to worry mate. To be honest, I've learned something today so everything's good. No one's upset, I hope, and we're all happy. Problem solved. Everybody wins :)

---

