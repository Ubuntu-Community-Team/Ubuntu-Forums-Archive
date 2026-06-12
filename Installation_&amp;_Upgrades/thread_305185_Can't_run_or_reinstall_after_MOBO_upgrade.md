---
title: "Can't run or reinstall after MOBO upgrade"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by ptipton on 2006-11-22
I had Edgy, upgraded from Dapper running fine dual booting with windows on a machine with amd semperon cpu and ati graphics card.
Have changed motherboard to MSI K9N Neo with Athlon AM2 and Gforce 7300GS graphics card. When booting to Edgy it reaches the splash screen and then hangs, tried in safe graphics mode and it also hangs. Have also tried booting from CD (Edgy Desktop 386, Dapper 64 bit and also the Mint Ubuntu varient) and all of them hang.
It would seem the hardware is basically ok as Windows runs fine.

---

### Post by futz on 2006-11-22
In my experience, a mobo change pretty much always requires a fresh OS install. The old install loads all the wrong drivers for a new mainboard and crashes happen.

---

### Post by ptipton on 2006-11-22
I'm happy to do a freah install but I cant as Ubuntu won't boot from CD either, tried 3cd's, as above ,all of which worked fine on other machines. Thanks

---

### Post by futz on 2006-11-23
> **ptipton said:**
> I'm happy to do a freah install but I cant as Ubuntu won't boot from CD either, tried 3cd's, as above ,all of which worked fine on other machines. Thanks
Check your BIOS for boot priority (boot sequence). Make sure your optical drive is at the top of the list.

Alternately, most modern computers have a bootup option called a Boot Menu  that you reach by hitting F12 or whatever the BIOS requires (Asus has another, very odd name for it - hit F8 for that - stupid choice of key as F8 is also used by MS Windoze for their boot option thing). 

Read fast on the first boot screen past the video POST screen and hit the required key. The boot menu gives you a list of drives available to boot from. Very convenient - saves ya having to change boot priority in the BIOS for a one-time odd boot. Choose your optical drive and it should boot.

I've occasionally had optical drives that refuse to boot for some reason. They work fine for everything else. If you have a second drive put that one at the top of the boot priority list and try that. If not, borrow one from another box, or from a friend or even buy one (they're cheap these days). Plug it in and see if that works better.

EDIT: If you run a pre-built package machine from a major vendor, you may not have such an easy time of all this. Package systems have dumbed-down BIOSes. "If there's no options, they can't hurt themselves." Also, their cases are tiny, miserable pieces of crap to work in. Makes quick hardware changes tough.

---

### Post by ptipton on 2006-11-23
Have the boot priority set correctly and with all three CD's I get the install menu and whether I choose install, or safe graphics intsall installation starts and then freezes. Seems to freeze at slightly different stages with the different Cd's

---

### Post by futz on 2006-11-23
> **ptipton said:**
> Have the boot priority set correctly and with all three CD's I get the install menu and whether I choose install, or safe graphics intsall installation starts and then freezes. Seems to freeze at slightly different stages with the different Cd's
Ah! I'm off on a rant then. Disregard that previous post. :mrgreen: 

Now you need to start trying boot options, like nousb, noprobe, noapic, etc. There are lots of others too, but those first two especially can sometimes make the difference between a puke and a successful install.

Enter em by hitting F6 and adding them to the end of the command line. Try one at a time. Then select your install type and hit Enter.

---

### Post by ptipton on 2006-11-23
Thanks, will try tonight.

---

### Post by cotcot on 2006-11-23
Have you tried the alternate installCD ?

---

### Post by ptipton on 2006-11-23
I have managed to isolate the problem - if I have the USB hub on my Dell LCD monitor connected then Ubuntu will not boot from either CD or the hard drive. Remove the USB cable to the monitor and can boot no problem from either CD or hard drive. In fact after installing the NVidia video driver my original installation now works fine with the new hardware. Now just need to figure out how to get it to boot with the USB hub attached.

---

