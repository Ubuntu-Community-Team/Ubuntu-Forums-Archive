---
title: "Can't Install Ubuntu 9.10"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Power_ on 2010-02-18
[I]Hello,

I've heard that Ubuntu is pretty good, so I decided to try it out. I can get it booted and everything and get to the installation part but I have no keyboard or mouse at all. I've tried 3 different types of mice and nothing. 2 of them were USB and the other was the circular input one. The only time my keyboard or mouse works is when the main menu comes up where you select "Install Ubuntu". After that, I get the screen where everything is loading but on that screen, I noticed that it says something like "cannot connect USB port 1 on address 2 error -110" and it goes all the way to like address 5 but still gives the error but ends up going to the installation process and on that, I have no mouse or keyboard at all. [/I] [I]

So if you can, please help. [/I] *:)*

[COLOR=Blue][SIZE=5]EDIT: I got the keyboard and mouse to work during the installation by checking all of the options in the F6 menu. But, after I restarted my system to complete the installation, I booted up Ubuntu from Grub but the keyboard and mouse stopped working again. What should I do next?[/SIZE][/COLOR]

---

### Post by JPWhite on 2010-02-18
Try Xubuntu as an alternative.

It maybe that you don't have hardware capable of running full ubuntu. Is this a new or old computer?

---

### Post by Power_ on 2010-02-18
It's just over a year old.

---

### Post by wrose51106 on 2010-02-18
What is the make/model of the PC?

Are you plugging directly into the USB port or are you plugging into a USB port say on your monitor and or a hub that connects to a USB port on your motherboard?

-Bill

---

### Post by amsterdamharu on 2010-02-19
So you can boot and run the live cd with keyboard and mouse working?

How do you start the installation? Did you use the install icon on the desktop of the live CD?

---

### Post by kansasnoob on 2010-02-19
> I've tried 3 different types of mice and nothing. 2 of them were USB and the other was the circular input one.

I hope you're not "hot-plugging" a PS-2 device when you say:

> the other was the circular input one

This does sound like a hardware compatibility issue. Can you even run the Live CD? I mean really "run it"?

Try browsing, etc. If so then post the output of:

```
sudo lshw
```

```
lsb_release -a
```

---

### Post by Power_ on 2010-02-19
> **amsterdamharu said:**
> So you can boot and run the live cd with keyboard and mouse working?

How do you start the installation? Did you use the install icon on the desktop of the live CD?

[IMG]http://gallery.techarena.in/data/519/Install-ubuntu.jpg[/IMG]

After I press enter there, they stop working.

---

### Post by Power_ on 2010-02-19
> **kansasnoob said:**
> I hope you're not "hot-plugging" a PS-2 device

I meant as in:

[IMG]http://ic2.pbase.com/o4/95/398095/1/56757858.IMG_3080.JPG[/IMG]

---

### Post by snowpine on 2010-02-19
Select the "Try Ubuntu with no change to your computer" option and spend some time using Ubuntu in Live mode. If the experience is not satisfactory (no mouse and keyboard would be an example) it is not worth installing on that hardware, in my opinion.

---

### Post by Power_ on 2010-02-19
> **snowpine said:**
> Select the "Try Ubuntu with no change to your computer" option and spend some time using Ubuntu in Live mode. If the experience is not satisfactory (no mouse and keyboard would be an example) it is not worth installing on that hardware, in my opinion.

still no keyboard or mouse on that either.

---

### Post by Power_ on 2010-02-19
> **snowpine said:**
> it is not worth installing on that hardware, in my opinion.

and you wonder why tons of people are still using windows.

---

### Post by snowpine on 2010-02-19
> **Power_ said:**
> and you wonder why tons of people are still using windows.

I wasn't trying to give you any attitude; hope you didn't misinterpret it that way. :) My point was simply: Ubuntu is not compatible with all hardware, so why would you install an operating system that does not allow you to use your keyboard or mouse? If your thought is "I'll install it first, then troubleshoot the problem later," how are you going to do that without a working keyboard?

My suggestions at this point are to 1) check your Ubuntu CD for defects (it is an option on the first screen) and 2) if that's not the problem, [test-drive some other Linux distros]("http://distrowatch.com/dwres.php?resource=major"). A third option would be to [purchase a computer with Ubuntu preinstalled]("http://www.system76.com/"), which (presumably) would not have any hardware/driver incompatibilities.

ps I have nothing against Windows :) so please do not turn this into a debate.

---

### Post by darkod on 2010-02-19
I have a wireless mouse and have never used ubuntu before Karmic. Honestly, I didn't expect the usb receiver to be recognized at all but I also have usb mouse around so I wasn't worried.
The wireless mouse/receiver was recognized automatically in Karmic and I didn't have to do anything at all. I could even use it during the install process which means it wasn't depending on starting ubuntu and doing some driver updates.

I'm not trying to defend ubuntu but it's almost impossible that a PS/2 keyboard or mouse are not getting detected just because they're PS/2. I don't know what could be wrong but PS/2 is supported ages ago.

I remember when SATA disks were supported in linux when XP didn't have a clue about a sata disk.

---

### Post by Power_ on 2010-02-19
I should add that when I install Ubuntu on VirtualBox, the mouse and keyboard are working fine on there. I don't know if that means anything or not.

---

### Post by chris_lukehart on 2010-02-20
Before installation or live mode

1) press F6 'other options'

2) i would check all those options; or one by one; or combination of those settings to if it would work.

---

### Post by Power_ on 2010-02-20
> **chris_lukehart said:**
> Before installation or live mode

1) press F6 'other options'

2) i would check all those options; or one by one; or combination of those settings to if it would work.

Ok, that let me use the keyboard and mouse through the installation. But now when I run Ubuntu (after the installation), it doesn't work again. What do I do now?

---

### Post by darkod on 2010-02-20
If you used any specific settings, they can be added to the ubuntu boot commands to make it permanent.
What selection made it work?

---

### Post by Power_ on 2010-02-20
> **darkod said:**
> If you used any specific settings, they can be added to the ubuntu boot commands to make it permanent.
What selection made it work?

I'm not sure which one actually made it work, but I selected all of them accept for the "Free Software Only" option.

---

### Post by darkod on 2010-02-20
There are few different fixes reported here:
[http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689)

One person got his ps/2 KB working after disabling usb keyboard and usb mouse in BIOS. Yes, I know usb doesn't sound related to ps/2, but that's what he says.

Others have seen it work after enabling usb legacy support (not sure if they have separate options for usb keyboard and mouse in BIOS and whether those were disabled or enabled).

I guess it will be playing around for a while until you find the right fix for your case. Hope it works.

---

### Post by Power_ on 2010-02-20
> **darkod said:**
> There are few different fixes reported here:
[http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689)

One person got his ps/2 KB working after disabling usb keyboard and usb mouse in BIOS. Yes, I know usb doesn't sound related to ps/2, but that's what he says.

Others have seen it work after enabling usb legacy support (not sure if they have separate options for usb keyboard and mouse in BIOS and whether those were disabled or enabled).

I guess it will be playing around for a while until you find the right fix for your case. Hope it works.

Ok, I'll try it.

---

### Post by darkod on 2010-02-20
I don't know, it might be even related. If you solve it they both start working. Give it a shot.

---

### Post by Power_ on 2010-02-20
> **darkod said:**
> I don't know, it might be even related. If you solve it they both start working. Give it a shot.

Sorry, but that topic didn't help at all. He said only his mouse stopped working but was still able to fix it with his working keyboard. But for me, neither is working, so as soon I as I press enter on Ubuntu on Grub, it stops.

I almost sure that I need to put "acpi=off" for it to work because that was one of the options that I checked before I installed was that and then after that the mouse and keyboard started working and also multiple posts were people saying that putting "acpi=off" somewhere was the fix.

So, like you said, you can add specific settings to the ubuntu boot commands to make it permanent. So how would I add acpi=off ?

---

### Post by darkod on 2010-02-20
My point for that topic was playing with the BIOS settings, and that's before even grub kicks in.
You can test acpi=off easy. In the grub menu highlight the ubuntu entry but don't hit Enter. Hit 'e' instead. A window will open with the ubuntu boot commands. You can move you cursor with the arrows.
At the end of the line starting with linux... add acpi=off.

If that works, you can make it permanent in:

sudo gedit /etc/default/grub

find the line GRUB_CMD.... ="quiet splash" and edit to "quiet splash acpi=off"

Save and close the file. Run

sudo update-grub

to create updated grub.cfg file. Restart and check if it's OK.

---

