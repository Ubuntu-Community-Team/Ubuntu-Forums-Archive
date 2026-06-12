---
title: "NVIDIA GeForce 210 - Manual Installation of Driver"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by david300 on 2014-10-13
Hi there!

Appreciate any and all help, the goal here is to learn as much as possible! :)

Running Ubuntu 14.04.1 LTS

Trying  to add NVIDIA GeForce 210 to PC to run a second monitor. The driver  installed by the 'Additional Driver' manager seemed slow and buggy  (mouse cursor blinks and disappears, graphics only partially load). So I  tried installing a driver I downloaded from  [http://www.geforce.com/drivers](http://www.geforce.com/drivers) in the command line. After I completed  the steps below and rebooted, it boots up fine and displays the login  screen as usual, but only on the monitor connected to the motherboard's  VGA. Then, as soon as I login the screen becomes distorted with a black  bar running across the bottom. I can't even open a terminal. I can  alt+ctrl+F1. Would you say the fault is with the driver or with my  installation of it?

Hopefully the solution is not embarrassingly obvious!

Thanks again!

**Steps I used in installing driver:**

downloaded driver from [http://www.geforce.com/drivers](http://www.geforce.com/drivers).

in terminal: [COLOR=#b22222]sudo gedit  /etc/modprobe.d/blacklist.conf[/COLOR] and added the following to the end:
[COLOR=#b22222]blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/COLOR]

rebooted 

alt+ctrl+F1 and then [COLOR=#b22222]sudo service lightdm stop[/COLOR]

[COLOR=#b22222]chmod +x[/COLOR] the .run file that downloaded
[COLOR=#b22222]./ [/COLOR]the run file

accepted license agreement

It  then asked should it run the nvidia-xconfig utility to update x  configuration so that the NVIDIA x driver will be used when restart x - I  said yes

finally, [COLOR=#b22222]sudo shutdown -r now[/COLOR]

---

### Post by Vladlenin5000 on 2014-10-13
Hi, welcome.

We've been seeing this more and more: Users attempting to use both integrated and discrete graphics cards in a desktop.
Short answer: Not possible.
Long answer: Unlike new notebooks with hybrid graphics (Intel + nividia / Intel +ATI / other), desktops were NEVER made to work that way, except those motherboards that can have 2 discrete (add-on) graphics cards _of the same vendor_, thanks to SLI and CrossFire technologies.

Bottom line: Choose one or the other. If you choose the discrete card NEVER connect anything to the onboard one. Most BIOS are setup as AUTO by default and simply by detecting that both are connect you're in for a lot of trouble and I guess you're just experiencing it.
Any GT210 has at least 2 (usually 3) outputs, DVI, HDMI and/or VGA. Connect both to the card, NEVER one in the card and the other onboard.

---

### Post by david300 on 2014-10-13
Thanks for your quick reply.

Yea I actually had to change settings in the BIOS to get it to even recognize the graphics card. I understand now, I did some research before this into cards and drivers but obviously not enough.

Thanks so much for the information. I'm glad, at least, that it was not something I did, command-line-confidence restored :)

---

### Post by Vladlenin5000 on 2014-10-13
You're welcome.

I didn't comment about your method before because you mentioned no errors during the process so I confidently assumed it should be fine.
It is, however, kinda overkill... Unless you have a bleeding edge nvidia or ATI chipset there's no need to install the driver manually as you did. Just go to System Settings > Software&Updates, find the rightmost tab "Additional Drivers" and select the recommend proprietary driver or, at best, that same version with the "-updates" tag. You should be fine either way, the only different being the "recommend" is the actual version tested for that Ubuntu release and "updates" is basically the same driver with minor corrections introduced after the initial tests. For most usage scenarios they work exactly the same way and with the same performance.
You can also add a PPA with newer versions and do the same procedure at "Additional Drivers" which by now should show a few more options. Again, this usually isn't needed. Either way, it's way easier than installing it with the nvidia's script.

---

### Post by sp40140 on 2014-10-13
Hi, I have this 210 card. It has HDMI, DVI & VGA ports. can't you use DVI or HDMI for one of the monitors and use just the 210?

---

### Post by david300 on 2014-10-13
In the beginning I did actual use the "Additional Driver" in the Software & Updates as you describe and I achieved more success with this method. However, it was still quite buggy with the mouse blinking and trailing and graphics not rendering correctly, this is probably because of the explanation you gave earlier about the motherboard and the incompatible graphics card. 

It definitely was overkill and the Software & Updates make this process idiot proof (which is quite useful for me), but I did want to try using the command line method and do it myself for educational purposes. Slightly out of my depth. For now I might just stick to simple terminal commands :P

Thanks again for all your help, this really is a great community

---

### Post by david300 on 2014-10-13
Hi sp40140,

Thanks for the reply! I originally got this card only because I had two old monitors lying around. The monitors only output VGA. I know there are many workarounds for my problem, like using different adapters, and I know it's excessive to get a graphics card for a low res monitor but I wanted to tinker with the card and driver. If nothing else, I'm more informed for it :)

But that's actually a good idea for my now temporarily useless graphics card though. Maybe a new monitor is in order :P

---

### Post by Vladlenin5000 on 2014-10-13
> **david300 said:**
> I did want to try using the command line method and do it myself for educational purposes.


Commendable. Keep rockin'on :guitar:

---

### Post by david300 on 2014-10-13
:lolflag: Thanks! will do! my poor PC is going to be put through its paces!

---

