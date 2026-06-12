---
title: "grub not loading.. version 1.97"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by rflores2323 on 2010-03-18
I have a gateway laptop and had ubuntu 9.04 and then upgraded to 9.10 however the sound was not working due to upgrading it. So I decided to install 9.10 from scratch and also wipe out my other partitions (as I had vista on it and did not use it anymore) so I wanted all my HDD for ubuntu.  

Well I tried to install via usb stick and the installation did not go as smooth.  For some reason it got stuck in the middle of the installation on step 3 and I had to reboot my computer and tried to install again.  this time it installed all the way thru however for some reason it does not load the desktop kernel.. it just hangs and has an underscore blinking on the top left corner.

I show the below before it just starts to hang 

The GNU Grub version 1.97 beta4

Ubuntu, linux 2.6.31-14-generic 
Ubuntu, linux 2.6.31.14-generic (recovery mode)
Memory test (memtest86+)
Memort test (memtest86+, serial console 115200)

can anyone help me? I have tried to reinstall 9.10, 9.10 remix, and even tried to go back to 9.04 however the OS just hangs and does not load the kernel.

Any help please.

---

### Post by phillw on 2010-03-18
> **rflores2323 said:**
> 
The GNU Grub version 1.97 beta4

Ubuntu, linux 2.6.31-14-generic 
Ubuntu, linux 2.6.31.14-generic (recovery mode)
Memory test (memtest86+)
Memort test (memtest86+, serial console 115200)

can anyone help me? I have tried to reinstall 9.10, 9.10 remix, and even tried to go back to 9.04 however the OS just hangs and does not load the kernel.

Any help please.

Hi, most odd as you've tried a couple installs. TBH, I'm a bit stuck as to what to suggest. Have you ran the 'check CD for defects' on the pen-drive you're installing from ?
You could try to manually put the kernel on. Leave it a while and see what other suggestions are posted, the How-To for it is in my Tech Area (Signature), or directly --> [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

Install the 9.10 from your pen-drive, then use the pen-drive as your 'live CD'

That will certainly put a 'clean' linux kernel on for you and tell grub about it.

Regards,

Phill

---

### Post by rflores2323 on 2010-03-18
ok I tried installing from a new usb stick and now it gets hung up on the installation.  

I show the below which looks kinda weird

[ 6.561194] clocksource tsc unstable (delta = 32798582012 ns)
[ 6.582349] usb 1-2: configuration #1 chosen from 1 choice

---

### Post by rflores2323 on 2010-03-18
I think my usb drives are not working correctly so this might be the problem.  I am going to try to install from CD to see if that helps.

---

### Post by z_diver on 2010-03-18
I get this same error with two Aspire Ones and it happens approx. 3 out of 4 boots.  Directly after selecting any 9.10 kernel it hangs with a black screen and the cursor just blinks.  If I choose the Xp or 9.04 it boots perfectly each time.

The fact [COLOR=DarkRed]sometimes[/COLOR] it's able to boot is odd since computers should simply not work like that.

---

### Post by rflores2323 on 2010-03-18
> **z_diver said:**
> I get this same error with two Aspire Ones and it happens approx. 3 out of 4 boots.  Directly after selecting any 9.10 kernel it hangs with a black screen and the cursor just blinks.  If I choose the Xp or 9.04 it boots perfectly each time.

The fact [COLOR=DarkRed]sometimes[/COLOR] it's able to boot is odd since computers should simply not work like that.

that is very weird.  it must be the kernel messing something up.  did you fix it or what was your solution?? Just installing 9.04?

---

### Post by z_diver on 2010-03-18
Well, I forgot to mention that this is with Netbook Remix but I usually just try to boot 3 times and get in but if I have to get in on the first boot, I choose the 9.04 installation and access my files on the 9.10 slice.  It's a rough workaround so I need to know what is going on.  

For what it's worth, UNR 9.10 was booting fine before running an update and grabbing the latest kernel but after that update, which touched a lot of stuff... grub included, both kernels boot inconsistently.

I'm not on that machine right now or I'd give more explicit kernel info.

---

