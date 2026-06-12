---
title: "Graphics Card Error"
date: 2013-04-24
forum: Installation &amp; Upgrades
---

### Post by iTac on 2013-04-24
Hello Everyone,

Sorry in advanced if this is posted in the wrong section.
I just installed Ubuntu 12.10 on my Desktop PC. I'm a very new user. 
It asked me to update a ton of things so I did. (I had successful startup and was running successfully for a few hours doing normal things).

When I restarted because of the updates, I now get a popup before launch stating:
"Your screen, graphics card, and input device settings could not be detected".
It has options for me to run in low graphics mode etc. However, I've tried all the options and either get this black screen with gray "Starting... X" "Stopping ... X" stuff that I cannot type in, or the option just doesn't work. 

For the record, I don't have a *real* so to say graphics card. I have this small device that came attached to my motherboard with VGA. I guess its a graphics card so to say, but its a terrible one if that.

Please Advise,
iTac

---

### Post by Mark Phelps on 2013-04-24
To see what graphics chipset it uses, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  Post that information back here.

---

### Post by iTac on 2013-04-24
Sorry, I'm really new. I don't know how to open a terminal.
All I get is that one window when I start the computer.

---

### Post by Bashing-om on 2013-04-24
iTac; Hi !

Try this to open a terminal:
Boot 'buntu and at the desk top key combo ctl+alt+f1 yields a login terminal; To return to the GUI, key combo ctl+alt+f7.
[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by iTac on 2013-04-24
I cannot get to the login screen. I get a graphics card error that prevents me from getting to any form of the GUI.

---

### Post by Mark Phelps on 2013-04-24
Ok, so do you get to a command line? OR, do you only get a black screen?

---

### Post by iTac on 2013-04-24
Right after the ubuntu loading screen, this is what I see:
[IMG]http://i35.tinypic.com/10fn82b.jpg[/IMG]

If I click next I can see this:
[IMG]http://i35.tinypic.com/2a69ffo.jpg[/IMG]

And most of the steps do this and nothing else:
[IMG]http://i33.tinypic.com/2qwixs2.jpg[/IMG]

Sorry for low quality, not like I can screenshot ;)
If you need a better picture, just ask.

---

### Post by Mark Phelps on 2013-04-24
Can't read the text screen -- too blurred.  What does it say on the last line? Does it leave you at a command line?

---

### Post by iTac on 2013-04-24
> **Mark Phelps said:**
> Can't read the text screen -- too blurred.  What does it say on the last line? Does it leave you at a command line?

Most of them say:
```
* Stopping X ....... [OK]
```

The last line says: 
```
Mountall: Disconnected from Plymouth
```

---

### Post by iTac on 2013-04-25
Bump. Hello, someone please help.

---

### Post by Bashing-om on 2013-04-25
iTac; Hi !

Try this for starters:
Boot your install and as soon as the bios screen clears depress and hold the shift key -> grub menu;
Press the "e" key for edit mode:
In this grub menu arrow down to a line similar to this --:
"linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff"
Arrow down and across to the terms "quiet splash" remove these and all else after, insert the term "text" - with out the quotes -
ctl+x to continue the boot process to a text login terminal.

Enter your username followed by your pass word (pass word gives no result to the screen, security reasons),

Now what results from the terminal command:
```
sudo service lightdm start
```(pass word required)
keycombo ctl+alt+f7 to activate the GUI, ctl+alt+f1 returns to the text console.
```
sudo shutdown -r now
``` to re-boot
[INDENT=2]further advise pending
     
[/INDENT]

---

### Post by iTac on 2013-04-25
Well I did everything.  
When I did the: sudo service lightdm start
it brought back up the error window that I originally had but with the low graphics mode
then I did the rest of the steps and restarted.
But I still see the low graphics mode error and can't get to my normal PC.

help.

---

### Post by Bashing-om on 2013-04-25
iTac; All we know at this time is there exist a graphics problem; Before looking at possible problems with the desk top, let's see what the display and graphics card are:
Boot up to the text login terminal and post the output of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
lsmod

```Maybe a driver is not loaded and the "lsmod" command will list a driver that can be loaded;
else perhaps we can start the Additional Drivers utility (???) aka jockey... I seem to recall though that the utility is no longer available in version 12.10 ( I am running 12.04, so can not test ).... there is the final authority the - command line interface - to remove/(re-)install a graphics driver if needed. We will see.[INDENT=2]
where there is a will there is a way

[/INDENT]

---

### Post by iTac on 2013-04-27
Hey there,
thanks for your help.

My PC outputed these things:
```
VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family [8086:0102] (rev 09)
```

```
description: VGA compatible controller
product: 2nd generation Core Processor Family Intel
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: mis pm vga_controller bus_master Integrated Graphics Controller
configuration: driver=i915 latency=0
resources: irq:46 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)
```

Let me know if you need more information.
Thank you for your help.

---

### Post by Bashing-om on 2013-04-27
iTac; 

I can not be of much help.
You are running intell for graphics and that is well supported by ubuntu's kernel.
A graphics driver - i915 - is loaded ... however the driver may be for older hardware and a better driver maybe available.

In that recovery mode -low graphics mode; see what the Additional Drivers utility has to offer for other drivers.
I do not recall that any driver is available outside of what is provided from Additional Drivers.

Intell is no longer in my sphere of knowledge, perhaps others can advise better ???[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by iTac on 2013-04-28
Bump.

Still need help please.
*Also thank you for your information Bashing-om.*

---

### Post by iTac on 2013-04-30
Hi there everyone.
I REALLY need help!!! This is the only PC I have and it doesn't work!!!
im on my phone now and need a running PC!!!

---

### Post by Bashing-om on 2013-04-30
iTac; Hey, still hanging in there with you.
Again I say I have no experience with the Intel graphics, With Nvidia and ATI cards sometimes it is needed to install "linux-header-generic"; perhaps it will help with Intel also.
Do this:
```
sudo apt-get install linux-headers-generic
uname -r # enter the output in the following CMD
sudo apt-get install linux-headers-'uname -i' # eg:".....linux-headers-3.5.0.27-generic"
sudo apt-get update
sudo apt-get upgrade

```

Then look at the Additional Drivers utility and see if there is an alternate driver available:
Launcher ->System Settings -> Software Sources (task bar menu option) -> Additional Drivers (tab in Software Sources).

Are there any alternatives ?[INDENT=2]
hope this helps

[/INDENT]

---

