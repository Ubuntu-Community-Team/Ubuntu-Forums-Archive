---
title: "Installation Problems - CD Drive"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by 71fnRVVm on 2008-07-03
Hi everyone,

I'm trying to install Ubuntu on my new machine ([see my previous problem with RAID]("http://ubuntuforums.org/showthread.php?t=848502")), and it recognizes my CD/DVD drive and will boot from the CD.

Until you get into the installation.  Then it says it can't find the drivers, and asks me to select it's location.

/dev/cdrom
/dev/cdrom0
/dev/cdrom1
/dev/mcdx

All fail.

I tried to do "ls /dev" over on the console view, but it spits out a huge list that blows by so fast I can't even peek at it... and trying to do a --sort on the ls command isn't recognized.

It's an "LG 20x Dual Layer DVD+-R/W Drive w/ LightScribe"... I believe it's [this one]("http://us.lge.com/products/model/detail/computer%20products_optical%20drives_optical%20drives_GH20LS10.jhtml").  It's labeled as "HL-DT-ST DVD-RAM GSA-H55L ATA Device" by the system.

Any thoughts?  Quick help appreciated - I'm on Windows Vista!  Ah!

Thanks

---

### Post by Pumalite on 2008-07-03
Make sure it is well configured in BIOS.

---

### Post by 71fnRVVm on 2008-07-03
Can you elaborate?

Thanks

---

### Post by Pumalite on 2008-07-03
BIOS are all different; so I will have to ask you: How does it show up now?

---

### Post by 71fnRVVm on 2008-07-03
"Show up now"?

Not sure what you mean there, but it shows the Alienware logo for about 30s, flashes text across the screen, does an HD check and gives messages like "Press [whatever] to enter RAID setup", "Press [whatever] to enter BIOS setup", etc.

It's pretty much like every other BIOS I've seen or used...

Is that helpful at all?

---

### Post by Pumalite on 2008-07-04
You have to catch it after POST (with 'Del' probably) and look for CD/DVD Drive. Modify it's settings if necessary.

---

### Post by VMC on 2008-07-04
Sounds more like it wants the location for your RAIS or video drivers and not CD/DVD ROM DRIVE. It already knows where that is.

Is this the output it gives or your output?

/> dev/cdrom
/dev/cdrom0
/dev/cdrom1
/dev/mcdx

---

### Post by 71fnRVVm on 2008-07-04
VMC:  That's what I tried, at different times, when it says "Failed to find the location of your CD drive, please enter it.  Non-standard drives may use /dev/mcdx"

Pumalite:  what?  It's already booting from the CD.  The problem is that it starts the installation setup process, and decides it doesn't see it anymore...

---

### Post by Pumalite on 2008-07-04
That's a BIOS problem, unless you recently added a hard drive in which case it could be a motherboard problem.

---

### Post by 71fnRVVm on 2008-07-04
Ok... so the BIOS is somehow responsible for Ubuntu's installation process running from CD, but failing to (somehow) recognize the CD drive?

If so, what do I need to fix?  Or, what do I need to poke around and look at inside the BIOS?

Thanks

---

### Post by Pumalite on 2008-07-04
Consult your motherboard Manual.

---

### Post by 71fnRVVm on 2008-07-04
Well, does anyone have any other enlightening thoughts?  Like VMC perhaps?

And I'm not talking about suggestions like "just fix it, you know?"

Thanks

---

