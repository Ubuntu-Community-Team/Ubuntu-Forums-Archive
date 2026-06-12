---
title: "toshiba satellite t215-s1160"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by His Shadow on 2010-12-07
hi there,

i recently got a netbook from toshiba (the specifics are in the title) and have tried to put ubuntu on it to no avail. i have tried almost every version from 64-bit to 32-bit versions, from 10.10 to 10.04 to 9 to mint even server. they all get up to the standard menu of the installation and when i go to install it starts casper then scans through the hardware on the machine and stops with that. i can never get past this point. am i doomed? will i never get that sweet linux feel on this that i had with my other laptops?

---

### Post by pandeiro on 2010-12-08
The same thing is happening to me. I received this laptop as a gift yesterday and spent all night trying to install Ubuntu on it. Tried both netbook and desktop versions of 10.10, to no avail.

If anyone can suggest a technique or even an alternative Linux distro to try, I would be very grateful.

---

### Post by vegmunky on 2010-12-10
Maybe a stupid question, but did you hit f6 and set acpi=off? I am playing with a Toshiba 215D 1140 and I can boot the 10.10 live cd to a desktop, but only with acpi=off. I am hesitant to install the OS based on your problems.

---

### Post by pandeiro on 2011-01-21
I wanted to update this thread with what I've found in case there are any other frustrated Toshiba T215/T235 owners out there. This is still far from resolved for me, but hopefully some veterans will show up and help us out of the wilderness?

So far I have tried booting from USB nearly every version of Ubuntu and my only success was with 10.10 server edition with acpi=off as vegmunky suggested.

However acpi=off causes several problems:
- computer fans don't work
- wireless doesn't work
- audio and microphone don't work (can only imagine webcam, too, but haven't tested)
- there are no indicators for battery and other peripherals after installing the GUI (ubuntu-desktop)

Anyone got any advice?

---

### Post by vegmunky on 2011-01-21
> **pandeiro said:**
> However acpi=off causes several problems:
- computer fans don't work
- wireless doesn't work
- audio and microphone don't work (can only imagine webcam, too, but haven't tested)
- there are no indicators for battery and other peripherals after installing the GUI (ubuntu-desktop)

I went ahead with acpi=off. It was either that or Windows. Unlike your experience, my wireless, audio, microphone, and webcam all work fine. However the battery indicators don't, which leads to trouble if I don't keep track of my up-time and recharge accordingly.

Edit: The LED battery indicator on the front of the laptop turns red when the AC power is plugged in, and white when the battery is fully charged. So even though the OS doesn't tell me anything, I still have a minimal indication of my battery state. I don't know what I'd do without any indicator at all.  I probably would leave it plugged in full time.

I did not notice any problem running the fan, but I'll pay more attention now.

My results are on a Toshiba Satellite T215D-S1140RD.  I keep checking the Toshiba site for a BIOS update. I'll happily temporarily install XP when it's time for the next Ubuntu update if they release a new BIOS that will fix the problem.

---

### Post by Justpeter6 on 2011-01-21
i have an ubuntu installation problem on my toshiba nb255 but i dont even get as far as you. There seems to be some sort of toshiba problem

---

### Post by vegmunky on 2011-01-21
I almost forgot to mention: my solution involved two steps.

First, I pressed F6 and set acpi=off on the Ubuntu 10.10 installation screen to get the installer to work.

Then I rebooted to enjoy my new desktop, and got nothing.  Black screen.

So I rebooted again, but held down the shift key.  This gave me the GRUB loader.  From here I was able to add acpi=off to my Ubuntu boot option.  Now it boots without intervention.

---

### Post by pandeiro on 2011-01-21
Thanks for the follow-up (and the original suggestion). I'm curious about which version of Ubuntu it is (10.10 Desktop?) and whether you are booting from USB (since the T215 has no optical drive). I really wonder why I can't even install the GUI versions (?) considering our computers are the exact same chipset.

FWIW Toshiba does have an updated BIOS from October 2010 on their webpage but my computer's is already the latest, judging from the version number.

I also took the plunge, it being that or Windows 7, but having a computer with no wireless or cooling mechanism is quite a price to pay. I am surprised that everything would 'just work' on yours with ACPI off. That's awesome.

I have already accepted that my destiny is something like this (I don't think Canonical or Toshiba are gonna save me): [http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems](http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems)

---

### Post by vegmunky on 2011-01-21
Wow, thanks for the link! That looks promising, albeit time-consuming. I saw the BIOS update on Toshiba's site too, but it's the same version I already have.

To answer your question, I installed 10.10 Desktop from an external optical drive connected by USB.

---

### Post by vegmunky on 2011-01-24
> **pandeiro said:**
> However acpi=off causes several problems:
- computer fans don't work
I just checked. My fan works whether I boot using AC power or battery power. I'm not sure if the fan adjusts to CPU activity, but at least it's running.

So as far as I can tell, the only problems I'm having with ACPI off with my Toshiba are:
* no battery meter.
* computer doesn't power off after shutting down; i have to wait for "system halted" message on the screen, then hit the power button.

---

### Post by pandeiro on 2011-01-24
Thanks for the info, vegmunky.

My own situation is the same. I have successfully gotten Ubuntu 10.10 up and running, with computer fans and wireless working, but several issues remain:

1) No battery indicator
2) No HDMI output
3) No screen brightness control
4) System requires manual shutdown

If anyone has any leads on any of these issues, please let us know!

Finally, in case anyone else is stuck with this laptop and can't get Ubuntu on it, here's what finally worked for me:

1. Install Ubuntu 10.10 Server Edition from USB. After selecting language, press F6 at the initial menu and select 'acpi=off'.

2. Using tasksel, install ubuntu-desktop (or kubuntu or xubuntu or ubuntu netbook) if you want a graphical desktop.

3. To solve audio/microphone issues:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

4. To solve wireless issues with Atheros wlan card:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

Hope this helps somebody.

---

### Post by z_mikowski on 2011-05-05
Although this has helped, the Satellite T235 is just too much trouble, IMO.  It took all day to get it running, and connecting a separate monitor was an exercise in futility.  My advice is to research your hardware well before buying.  

My current laptop, a Dell Studio 15 (preloaded with Ubuntu) has required much less maintenance and usually works flawlessly, even with the Intel graphics (nVidia was an option).

---

### Post by ander111 on 2011-06-07
I hope you've tried Ubuntu 11.04, which has solved many of these problems. I'm running it on my Toshiba NB255 netbook, and except for a [small problem]("http://ubuntuforums.org/showthread.php?t=1776950&highlight=nb255") with the wireless (which should be easy enough to fix), everything's working great.

---

### Post by muchristian on 2011-07-30
> **pandeiro said:**
> Thanks for the info, vegmunky.

My own situation is the same. I have successfully gotten Ubuntu 10.10 up and running, with computer fans and wireless working, but several issues remain:

1) No battery indicator
2) No HDMI output
3) No screen brightness control
4) System requires manual shutdown

If anyone has any leads on any of these issues, please let us know!

Finally, in case anyone else is stuck with this laptop and can't get Ubuntu on it, here's what finally worked for me:

1. Install Ubuntu 10.10 Server Edition from USB. After selecting language, press F6 at the initial menu and select 'acpi=off'.

2. Using tasksel, install ubuntu-desktop (or kubuntu or xubuntu or ubuntu netbook) if you want a graphical desktop.

3. To solve audio/microphone issues:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

4. To solve wireless issues with Atheros wlan card:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

Hope this helps somebody.

I know this is an old thread but I've managed to get mine running recently with what appears to be everything working. Including function keys on the keyboard. Here is my uname -a output:
2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
The only part I have not yet tested is the HDMI out. All wireless, screen brightness, fan control, battery level indicator, processor throttling and shutdown features work correctly. 

I realized that I didn't need ACPI=off in the grub config when I was playing with Linux Mint 11 and forgot to edit the boot options before booting from the CD rom.

I was planning on selling this computer on eBay since I won't own a system that can run Linux properly, but looks like this thing is running like a champ now!

---

### Post by steve11911 on 2011-07-31
Success stories are always a worthwhile post.For those who wander this far I'll offer these two resource pages:

Linux on Toshiba
[http://www.linux-laptop.net/toshiba.html](http://www.linux-laptop.net/toshiba.html)

and:

[http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html)

---

