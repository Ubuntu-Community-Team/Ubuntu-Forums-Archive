---
title: "Can't boot ubuntu from USB"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by Darkmagic on 2010-09-26
I downloaded the .iso from the main page on ubuntu linux. I ran unetbootin to install the.iso onto my Kingston datatraveler 4GB USB stick. 
 
I set my computer to boot from the USB stick and when it boots, it loads the ubuntu boot screen, then disappears, and the screen remains black. What's wrong?
 
I am trying to access my files and Windows is not booting, so I decided to use Ubuntu to boot up my computer.
 
Any suggestions? Thanks!

---

### Post by snowpine on 2010-09-26
Welcome to the forums!

A couple of things you can try if you're having trouble with Unetbootin (which is not really part of the Ubuntu project):

1. Try Ubuntu's own "usb-creator" application [as described here]("https://help.ubuntu.com/community/Installation/FromUSBStick").

2. Burn the .iso image to a CD (important to burn as an "image" not a "data" CD-ROM)... this is the "tried and true" method.

---

### Post by sikander3786 on 2010-09-26
It seems like a graphics issue to me. Does the monitor turnoff after Ubuntu Logo as if it was not receiving any signals? Which graphics card have you got?

---

### Post by Darkmagic on 2010-09-26
It seems to be on. I am not sure because I have a laptop.

---

### Post by C.S.Cameron on 2010-09-26
Check the MD5SUM of the iso?

---

### Post by sikander3786 on 2010-09-26
Snowpine has some suggestion above. I doubt if you will be able to follow his 1st suggestion but you'll have to follow the 2nd one if mine fails. You didn't tell which graphics card you have got?

---

### Post by tekkidd on 2010-09-26
Its a graphics issue, your graphics card cant handle that version of ubuntu. I had an old laptop that gave me a blank screen when it hit the login screen (I ended up using 9.04 on the laptop). Your best bet is to use an older version of Ubuntu

---

### Post by sikander3786 on 2010-09-26
> 
Its a graphics issue, your graphics card cant handle that version of ubuntu. I had an old laptop that gave me a blank screen when it hit the login screen (I ended up using 9.04 on the laptop). Your best bet is to use an older version of Ubuntu

It often happens with the first run only. If it can be fixed here, you can run any version on any computer regardless of the resolution but dependent on other hardware i.e, processor, ram and disk space.

[COLOR="Red"]**Edit: **[/COLOR]

@Darkmagic

As C.S.Cameron suggested, MD5SUM is equally important. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Darkmagic on 2010-09-26
My computer is a 2005 computer. I think it is an Intel Media Accelerator card (not sure of the style).

---

### Post by snowpine on 2010-09-26
> **tekkidd said:**
> Your best bet is to use an older version of Ubuntu

Sorry but I can't agree with this... older "end of life" Ubuntu releases are not supported in any way and will create more problems than they solve. The only releases I can recommend are 8.04 (supported through April 2011), 9.10 (also April 2011), and of course 10.04 (April 2013).

There are a number of good suggestions already mentioned--like figure out  which Intel graphics card you have and use the forum Search feature, check the md5sum, use the Ubuntu-recommended 'usb-creator' instead of Unetbootin, or burn a CD--before doing anything drastic like using an old, unsupported release.

---

### Post by sikander3786 on 2010-09-26
Ok. Boot using the USB. The first page where it lists Default and other boot options there will be an option to edit the boot string. I don't remember that exactly, I used unetbooting long time ago, but you'll be able to find it easily. Edit the default boot command and navigate to "quiet & splash" and type **nomodeset** in their place. Proceed with the boot and see if it helps.

You can also try typing **i915.modeset=0 xforcevesa** or finally only delete "quiet & splash" and type nothing in their place and proceed with boot.

---

### Post by Mi11z on 2010-09-26
> **C.S.Cameron said:**
> Check the MD5SUM of the iso?

I was going to say this.

---

