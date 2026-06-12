---
title: "Help total newb installing Ubuntu"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by lsujim on 2007-09-01
Hello everyone!

I'm a total windows guy so I'm not familiar with the linux lingo. I never looked at linux until a friend at work finally got me to try it out. Since then I've been trying without any success to get ubuntu to run on my box.

Here are my stats:

Gigabyte GA-M59SLI-S5 AMD Socket AM2
Athlon X2 3800
2gb DDR2 RAM
Nvidia Geforce 7800 GTX

I have tried AMD 64 iso, alternate install. I burned the cd at 4x speed, did the MD5 check and everything looked fine. What happens is whenever I try to select any of the options I get some commands that appear on the screen and then it goes blank and thats it. I can then try and press CTRL-ALT 1 and I see "Loading, Please wait...". I've tried waiting and I still there is nothing. However, if I change the screen resolution to 1024x768 32 and then select an option, I'll see the ubuntu logo with a progress bar under it and then it just sits there doing nothing.

Any assistance would be very appreciated.

Thank you for reading.

---

### Post by seshomaru samma on 2007-09-01
Firstly if you are not familiar with Linux I would suggest the 32 version
 > What happens is whenever I try to select any of the options
can you be more specific , which options? at which stage?
> I get some commands that appear on the screen and then it goes blank and thats it
do you remember what it says?

---

### Post by lsujim on 2007-09-01
> **seshomaru samma said:**
> Firstly if you are not familiar with Linux I would suggest the 32 version
 
can you be more specific , which options? at which stage?

do you remember what it says?

I'm currently downloading the 32bit version right now. 7.04

Right after I boot the machine, an ubuntu menu shows up. It has Start/Install, Start with safe graphics option, something about install drivers, check cd for errors. If i select any of these options, it'll show

Loading /casper/wmlinuz......
Loading /casper/initrd.gz...................................................

The screen will flicker off then on and then go to black screen. However the monitor will still have video input.

---

### Post by Midwest-Linux on 2007-09-01
> **lsujim said:**
> I'm currently downloading the 32bit version right now. 7.04

Right after I boot the machine, an ubuntu menu shows up. It has Start/Install, Start with safe graphics option, something about install drivers, check cd for errors. If i select any of these options, it'll show

Loading /casper/wmlinuz......
Loading /casper/initrd.gz...................................................

The screen will flicker off then on and then go to black screen. However the monitor will still have video input.

Do you have two video outputs? If so try the other one. I had a issue installing Ubuntu on a mac G3, it never showed the install menu....screen went blank...The simple answer after a week of trying to figure it out was that though both video outputs would display the mac OS 9, only one would display the Ubuntu installer. Now if you only have one video output, try a smaller resolution ...sometimes that helps. 

If you want to install it on your system, you can partition it around your existing Operating system. I always use the ALTERNATE Text based installer for 7.04. It is a straight forward install and the screen always stays on. I had little luck with the live install disk, but 100% success with the alternate install.

 On yet on another machine a pentium 166 Mhz with 130 meg Ram I had the black screen problem when I tried to install DSL linux, right after the the loading the screen went blank. I gave up and installed Vector Linux instead and this time though the screen went black , by hitting the left arrow  (on the keyboard) it would show the screen again. So try that too hitting the left or back arrow on your keyboard...why It did this I have no clue...except a 166 Pentium is pretty low end  for todays standard.

 Another thing to try is to turn off your power management and screen saver. Select on all the time and maybe it might clear the install problem .

---

### Post by wavell2003 on 2007-09-02
I'd like to suggest turning off apci and smp when booting.  follow the instructions here:

wiki.ubuntu.com/hp_dv6000_series_(dv6116eu

this user had a simliar problem to yours and this seems to work for him, although he performed the instructions a little differently:
ubuntuforums.org/showthread.php?t=529735&highlight=nvidia+install+blank+screen


PS I have had this exact same problem with an nvdia card install but I don't remember how i fixed it.  The solution was with playing with boot parameters.

--Wavell

---

