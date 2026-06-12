---
title: "display problems"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by xcalibur32 on 2007-07-05
Hi, I could finally install ubuntu. After installing, I clicked on the icon which said 'restricted driver' on the right hand top corner and then enabled graphics accelerator. It asked me to reboot. I did that and then I only get a blank screen after booting. 

I would appreciate if anybody would help me fix them

Thanks

---

### Post by Kralizec on 2007-07-06
To restore your display, logically you could disable the restricted driver. 

From the research I did really quick, boot into Ubuntu's version of 'safe mode' (can't remember what it's called) or when the X server (gui) tries to start, hit ctrl+alt+F1 to enter a text-only environment (virtual console) and login. Once logged in, enter:

```
sudo restricted-manager --disable=MODULE
```
where MODULE is the name of the device you enabled. To determine the name of the module, run
```
restricted-manager -l
```
this will list the name of all restricted devices you have on your system.

Issue the restart command to see if it worked after doing the above.

```
sudo shutdown -r 00
```
where 00 is the time to wait before restarting.

**Example:**

I have an ATI restricted graphics driver on my system, so I do this
```
restricted-manager -l
``` which outputs this:
```
fglrx
``` so I then do this:
```
sudo restricted-manager --disable=fglrx
``` and then restart.


Hope I helped some.

---

### Post by Viewtifulj on 2007-07-06
> **xcalibur32 said:**
> Hi, I could finally install ubuntu. After installing, I clicked on the icon which said 'restricted driver' on the right hand top corner and then enabled graphics accelerator. It asked me to reboot. I did that and then I only get a blank screen after booting. 

I would appreciate if anybody would help me fix them

Thanks

Be prepared for a HUGE headache. I went through the same thing a few weeks ago and never actually found workable solution. I gave up and now i just use the "vesa" drivers. The situation sucks though because i cant watch any of the programs i normally watch, so i am stuck with Xp as my main OS.

---

### Post by xcalibur32 on 2007-07-07
How did you revert back to 'vesa' Could you please  let me know

Thanks

---

### Post by foxmuldr on 2007-07-07
> **xcalibur32 said:**
> How did you revert back to 'vesa' Could you please  let me know

I'd like to know too.

---

### Post by xcalibur32 on 2007-07-07
Figured it out.. .. you can run

sudo dpkg-reconfigure xserver-xorg

and ask it to autodetect, if it can't it will select the default which is 'vesa' , then you can go through the different menu options. That will atleast fix it for you.

---

