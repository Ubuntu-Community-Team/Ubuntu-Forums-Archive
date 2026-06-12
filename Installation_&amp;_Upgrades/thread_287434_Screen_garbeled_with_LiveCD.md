---
title: "Screen garbeled with LiveCD"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by brokerjoker on 2006-10-28
Hi,

booting from the live CD brings up the boot splash screen, but then either leads to a black screen, scrambeled horizontal lines oder to some grey and blue dots, depending on the resolution I choose at boot time. However, the system seems to run fine, but remains invisible.

I have a Matrox P650 with two EIZO 19"-panels (1280x1024) on DVI. I  somehow have the bad feeling that the graphics board works fine (should run with VESA, as I read), but somehow the monitor(s) cannot sync with the signal.

Does anyone have an idea how I can find out what to do? I am absolutely clueless and stuck before the real fun starts.

Please, please help me ;)

---

### Post by lenkite on 2006-10-28
Hi brokerjoker,

I have the exact same problem you described on my PC. My graphics card is an Nvidia 6600 that works fine. But the monitor is a Philips 23 inch..that shows scrambled lines after the boot splash screen.

Right now..Edgy doesn't install either on my Dell insipron nor on my PC.. ](*,) 

Please do let me know if you find something (I am a brand new Ubuntu user).

---

### Post by taurus on 2006-10-28
If you want to install Edgy on your machine, try using the alternate CD if the LiveCD doesn't work!  Pick the first option, installing with text base, and it should be good...

---

### Post by lenkite on 2006-10-28
Hi taurus..thanks..I didn't realize the text base install came in a separate CD..downloading that right now...

Strangely when you hit Esc in the graphical splash screen of the desktop CD it pops up a dialog confirming whether you wish to commence a text based install :-)

---

### Post by taurus on 2006-10-28
I've never liked using the desktop CD (LiveCD) because I don't want to boot from it first just so I can click on the installing icon to install it on my machine.  Therefore, I always use the alternate CD and besides, I need to manually partition my harddrive and mount others where I want them...  Works just as good.  ;)

---

### Post by DeathOnJuice on 2006-10-28
It's your lucky day! I just had the same problem and could get little support here, so I figured it out on my own.

First, as others have suggested, use the alternative install CD. This should get the OS installed.

Still, when you try to log in, it will give you the garbled screen. Don't log in yet; instead, hold control and alt and press F1. If this gives you a garbled screen too, reboot and select "Recovery Mode" at the bootloader. Log in in this terminal. Then, type:

```

sudo nano /etc/X11/xorg.conf

```

Scroll down to where it says "Section" "Device". Where it says Driver "nv", change the nv to vesa. Then, hold control and press O then press enter (to save changed) and press control-x (to exit nano).

Now, type this:

```

sudo /etc/init.d/gdm restart

```

You can now login every time without a hassle. However, performance will be very, very bad (it takes a few seconds to scroll down in Firefox). So, we need to install a driver. I have only done this with an NVIDIA card, so MAKE SURE YOU ONLY DO THIS WITH AN NVIDIA CARD. The instructions are here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

EDIT: Almost forgot this part.

Also, in addition to these instructions, there is a security hole in the NVidia drivers, unless you're using the beta release. It can compromise your system or (more likely) just restart the X server while you're using Firefox. To fix it, open a terminal and enter:

```

sudo gedit /etc/X11/xorg.conf

```

In the Device section, above the line that says Driver "nvidia" (if you followed the instructions), add this line:

```

Option "RenderAccel" "false"

```

Then log out and press control-alt-backspace.

Enjoy your Edgy-working goodness! If you need help with anything, whether I posted it or it's in the guide, just ask. I'll monitor this topic for a while.

---

### Post by brokerjoker on 2006-10-29
Thanks for all your ideas. I'll download the alternative CD and see what happens then.

(I did't expect to get so much help so quickly. Obviously, (K)ubuntu is quite different from other distros :cool: )

---

### Post by dvord on 2006-10-31
"Still, when you try to log in, it will give you the garbled screen. Don't log in yet; instead, hold control and alt and press F1. Log in in this terminal. Then, type:"

Ok, I have a 6600 GT and I actually don't get garbled screens, I get a monitor OSD popup saying the sync is out of range.

I tried your steps anyway and got as far as the above.  Believe it or not, when I do Ctrl-Alt-F1 I THEN get the garbled screen...

](*,)

Edit:  Went into recovery mode and continued steps.  I got a window popup: Internal Error failed to initialize HAL!  

Going to conting anyway in the hope that error goes away. :mrgreen:

The HAL error went away after a reboot.  The rest of the setup went STELLAR!!  Thank you!!!

---

### Post by gerkin on 2006-11-01
I have the exact same problem > garbled screens from the live install CD.  Unfortunately when I try Ctrl.Alt>F1 the text screen is also unreadable

Has anyone got any suggestions please??

Nvidia 6600 & Phillips 19" LCD both have worked fine on all previous releases of Ubuntu

cheers......

---

### Post by dvord on 2006-11-01
What I did was go into Recovery Mode on boot.  You know where you get the boot loader and you can choose from 2 different linux options and Memtest?  Choose the one that says Recovery mode.

You shouldn't get loaded into a gui, you should just see plain text.  Then you can do the steps that DeathonJuice mentioned. 

It worked great for me!!

---

### Post by DeathOnJuice on 2006-11-02
Thanks, guys! I'll add that into the guide.

---

