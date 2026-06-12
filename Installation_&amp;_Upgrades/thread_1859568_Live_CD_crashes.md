---
title: "Live CD crashes"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2011-10-14
I burned an ubuntu-11.10-desktop-amd64 CD and it crashes. The system boot up, but then I sit there and watch all sorts of bizarre things get written across the top and left side of the screen. I can move the mouse point, but clicking has no effect. This does not give me great confidence that I could use the live CD to fix things if something goes wrong with the installation.

I've been burning my own Ubuntu CDs for several years, and this is the first one that has been "delivered" broken.

---

### Post by garvinrick4 on 2011-10-14
> I've been burning my own Ubuntu CDs for several years, and this is the first one that has been [COLOR=Red]"delivered"[/COLOR] broken.
You download an iso file and Burn your own disk, at times you just get a bad burn or a bad
download. Do it over again. Not something that is delivered so is not checked for errors.
Use torrent download is faster if you choose to.

---

### Post by Tanargbob on 2011-10-14
> **rplantz said:**
> I burned an ubuntu-11.10-desktop-amd64 CD and it crashes. The system boot up, but then I sit there and watch all sorts of bizarre things get written across the top and left side of the screen. I can move the mouse point, but clicking has no effect. This does not give me great confidence that I could use the live CD to fix things if something goes wrong with the installation.

I've been burning my own Ubuntu CDs for several years, and this is the first one that has been "delivered" broken.

I am getting exactly the same as you do. I only wanted to see if 11.10 would let my PC run Unity as 11.04 never has. 
Guess I will stick with 11.04 then.

---

### Post by rplantz on 2011-10-14
> **Tanargbob said:**
> I am getting exactly the same as you do. I only wanted to see if 11.10 would let my PC run Unity as 11.04 never has. 
Guess I will stick with 11.04 then.

A friend has burned another copy for me on his computer. I'm picking it up later today. I'll let you know how that copy works.

---

### Post by rplantz on 2011-10-14
> **rplantz said:**
> A friend has burned another copy for me on his computer. I'm picking it up later today. I'll let you know how that copy works.

I tried the second CD. Same result. When I click on "Try Ubuntu" the desktop comes up, then slowly deteriorates. Unresponsive to mouse.

The CDs work quite well in my Acer Extensa 5620 laptop.

I've been programming professionally for over 40 years, and my friend is the sysadmin in the CS department at the university where I taught for 20 of those 40 years. So neither if us is a newbie at this stuff.

My suspicion is that this has something to do with the nvidia card (GT 220, 1GB) in my desktop machine. Again, I'm nervous about installing this version without having a live CD to use in case of problems. That's saved me several times in the past.

---

### Post by garvinrick4 on 2011-10-14
> My suspicion is that this has something to do with the nvidia card (GT 220, 1GB) in my desktop machinePut in Live CD and hit  spacebar when icons appear on bottom at startup.
Now hit F6 and start in nomodeset in menu and see if that gets you going.
 > Again, I'm  nervous about installing this version without having a live CD to use in  case of problems. That's saved me several times in the past. 		                   		  		  		 		 			 				__________________
Understandable.
I know nothing about nvidia but lots of users have them so should not be to bad a problem.

---

### Post by MAFoElffen on 2011-10-14
> **rplantz said:**
> I tried the second CD. Same result. When I click on "Try Ubuntu" the desktop comes up, then slowly deteriorates. Unresponsive to mouse.

The CDs work quite well in my Acer Extensa 5620 laptop.

I've been programming professionally for over 40 years, and my friend is the sysadmin in the CS department at the university where I taught for 20 of those 40 years. So neither if us is a newbie at this stuff.

My suspicion is that this has something to do with the nvidia card (GT 220, 1GB) in my desktop machine. Again, I'm nervous about installing this version without having a live CD to use in case of problems. That's saved me several times in the past.
When you are starting the LivecD disk, the first screen is black with a person/keyboard icon centered at the bottom screen.  Press the <esc> key.  It will go to a language select box, press <enter> or <esc>.  You will be at the advanced menu, press <F6>, arrow down to "nomodeset", press the spacebar. Press <esc>, then select "Try"

Yes, with your video card, you need to use a "nomodeset" kernel boot option to run the LiveCD and... upon a new-fresh install, you'll have to add the same temporarily on the first reboot, to be able to boot up and install your particular video driver.  After your driver is installed, you will no longer need to use that boot option.

Confirm that the LiveCD image runs okay with that option.  If not, I have others that work with that card.  When it does, that may reveal tweaks that you may need in your install.  When it does, I'll explain what to do in grub in your initial reboot after install.

---

### Post by rplantz on 2011-10-14
> **garvinrick4 said:**
> Put in Live CD and hit  spacebar when icons appear on bottom at startup.
Now hit F6 and start in nomodeset in menu and see if that gets you going.

Thank you, I'm doing this from the live CD right now!

One more point is that one has to use esc to get out of the nomodeset menu.

BTW, what does nomodeset do? I can see that it puts my display in a much lower resolution. Does it bypass the nvidia driver?

> 
Understandable.
I know nothing about nvidia but lots of users have them so should not be to bad a problem.
One of my reasons for selecting nvidia when I built this box is that I have the general impression that nvidia is a little better about providing linux drivers.

---

### Post by garvinrick4 on 2011-10-14
> BTW, what does nomodeset do?

nomodeset

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. 
While this is a major step forward for the graphics architecture in 
Ubuntu, in some rare cases KMS will prevent your 
video output from working correctly, or from working at all. 
If you need to disable KMS, you can do so by booting with 
the nomodeset option. You can also save this setting so that 
it's applied at every boot by adding it to your grub config 
(for GRUB 2: edit /etc/default/grub and add nomodeset to 
GRUB_CMDLINE_LINUX, then run sudo update-grub

---

### Post by MAFoElffen on 2011-10-14
> **rplantz said:**
> Thank you, I'm doing this from the live CD right now!

One more point is that one has to use esc to get out of the nomodeset menu.

BTW, what does nomodeset do? I can see that it puts my display in a much lower resolution. Does it bypass the nvidia driver?


One of my reasons for selecting nvidia when I built this box is that I have the general impression that nvidia is a little better about providing linux drivers.
<esc> will backout from there but retains the settings selected.

ATI and NVidia cards are VESA compatible and do VESA (which the LiveCD and Ubuntu without a driver installs tries to use), but you have to specifically tell them to go into and use that mode... They don't do it automatically. Ubuntu, if a driver is not specified, tries to use the nouveau driver (generic), then the VESA driver.

To turn off KMS and put an NVida Card into a VESA mode, try these options one at a time:
```

nomodeset
xforcevesa
vga=792

```NVidia is "my" main personal choice.  Good support in Linux and Unix. I have additional other GPU's here on test boxes for testing purposes, but I like to live and play with what I like.  ATI is also well supported and has the same kinds of challenges in running, boot options (that are different than nvidia), etc.  Once it is installed, they're great.

---

