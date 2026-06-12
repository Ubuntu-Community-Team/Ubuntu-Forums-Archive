---
title: "fresh 7.04 install problems. soft lockup? error"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by skot on 2007-04-19
ive been using 6.10 for a few months and love it.
been wait for today!
get home download full i386 image for 7.04 checked the disk for errors... everything ok according to ubuntus check at the begining of the live cd.
after multible attempts to get it to load it woudl freeze on the tan splash screen. tried normal and safe graphic  modes.  then i finaly get some errors.  here they are......

```

[96.568118] bug: soft lockup detected on cpu#0!
[104.744043] rt61M1meEnqueue: full, msg dropped and may corrupt MLME
[125.009630]
[145.271261]
[165.528882]
[185.790516]
[206.056142]
[326.266604]

```

after about 3 more atempts i get into the live cd.  i quickly install. dont want to risk not seeing the desktop again haha.

then i log in and start the updates from the update menu.  only 2 listed at this time.  i forget what they were i think somethign to do with the update manager.  then it freezes.  i restart and try to log on.  now once loaded nothing works and it freezes when trying to open and menu or window.

if there something i can do to get more info on my problem?

my system specs. 
3.0ghz p4
1 GB ram
geforce nvidia 7800gs pci-express 256 mb
430 watt power suppley.

thanks
skot

---

### Post by skot on 2007-04-20
is there a mininum hard drive requirement for 7.04?
ive always in stalled linux fresh onto my 10GB 2nd hard drive.
after burning another cd image and checking it.  i still cant seems to get 
it to work.  im thinking it might be my hardware.
i havent gotten anymore error messages.  it just seems to alwasy lock up/ freezes
when its installing the system onto the hard disk

any thhoughts.

---

### Post by sixstring on 2007-04-20
I get that same error after installing 7.04 alternate x86.  It took me a few reboots to finish installing the xorg-driver-fglrx for my ATI x1900 card as it would keep giving this error and locking up.

"bug: soft lockup detected on cpu#0!"
"rt61M1meEnqueue: full, msg dropped and may corrupt MLME"

I did manage to get the ATI display driver installed and reboot into gnome but the system locks up after a few moments of running from the error.

my machine:
AMD64 X2 3800+
ATI x1900xt
2GB RAM
ATI 200 chipset motherboard

I'm dual booting Windows and don't have a problem with hardware lock ups at any other time.  I'm trying the x64 flavor of 7.04-alt next to see how that goes.

---

### Post by sixstring on 2007-04-20
I forgot another error message, while booting it says:

 "timer not connected to IO-ACPI"

Perhaps it is not playing nice with my dual core CPU?

---

### Post by CRO-MAGnum PI on 2007-04-20
Is there a command you can turn on from the cd boot menu that turns on error reporting? Because I cannot get 6.10 nor fiesty to install on my system, as both installs lock up after the tan splash screen. It has to be a hardware problem and without any type of log or error i don't even know where to begin.

---

