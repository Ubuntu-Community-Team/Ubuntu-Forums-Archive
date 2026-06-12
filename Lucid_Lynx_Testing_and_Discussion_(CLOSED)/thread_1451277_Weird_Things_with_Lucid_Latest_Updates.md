---
title: "Weird Things with Lucid Latest Updates:"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2010-04-10
for the first time my ATI video card no longer works,I get no special video effects and lost the window buttons

now firefox will not connect to some common websites like westernunion.com and some others,i still can go there with windowzzzz

appearance has been afected so much that I will go back to Karmic waiting until the official release if it works or will windozzz for a while :(

---

### Post by Didius Falco on 2010-04-10
what video card do you have and what driver are you using?

---

### Post by kuvanito on 2010-04-10
this is my ATI video card ATI Video Card HD4350 PCIE-512M 
it's funny cause it was working fine until yesterday's updates and then no more.
i can not get any video efects to work on my appearance,like i said i even lost my window buttons and when i go to change my appearance it will let me get some things back but until next boot all gone again and i can not even close the change appearance windows,it will say something like settings will go back to previous if you do not take action in the next 34 minutes or something like that,never had this problem before

my guess is that lucid still needs a lot of polishing,lots of them

and the firefox issue it's mind bothering,i can go with 7 and IE no problem but Ubuntu and Firefox NO GO!

---

### Post by Killigrew on 2010-04-10
> **Didius Falco said:**
> ... what driver are you using?

please answer, otherwise we are not able to help...

greetings :)

---

### Post by kuvanito on 2010-04-10
the only driver that ubuntu has for me, a propietary driver:
ATI/AMD propietary FLGRX graphics driver

come on guys you know that crap...

---

### Post by ranch hand on 2010-04-10
No we do not know that crap.

I am using the generic driver, for instance, and do not even like the childish effects.

I can also, with my ATI card, and the generic driver, enable and "enjoy" all effects.

Therefore knowing what you are running is important and your attitude insulting.

---

### Post by Didius Falco on 2010-04-10
> **kuvanito said:**
> the only driver that ubuntu has for me, a propietary driver:
ATI/AMD propietary FLGRX graphics driver

come on guys you know that crap...

Actually, we *don't* "know that crap" - it's important information if you want to solve your problem.

I'd suggest that you disable the proprietary FGLRX driver and install/use the x driver.

For your card it would be xserver-xorg-video-radeon.
BTW, I agree with Ranch Hand - you'll find that acting all annoyed when people are taking their time to try and help you for free is not a good strategy.

Good luck...

---

### Post by podfish on 2010-04-15
Hello!

I did a fresh install of 10.04 on a Compaq n400c with a Radeon Mobility M6 yv (?) yesterday, and acceleration worked very well out of the box, including xv support for x11 (video rendering for totem, etc.) under the radeon open source driver (awesome!) I was able to select the "radeon texture" device when running gstreamer-properties, and video playback was reasonably fast in the test.

Then I decided to enable the proposed updates, did a full upgrade, installed the ubuntu-restricted-extras and rebooted.  Now the device isn't showing, and video playback is fouled up.  However, desktop effects are running just fine.

Unfortunately, I have no idea what exactly upgraded, other than the usual suspects--xorg, mesa, the driver, the kernel, and basically every other component that touches video.  :-)  I'm not using an xorg.conf, and I haven't monkeyed with my kernel options in grub to do anything other than the default KMS setup for my video.

Thoughts/ideas?  I'm loathe to file a bug on launchpad just yet because I don't know what the offending package is...

---

