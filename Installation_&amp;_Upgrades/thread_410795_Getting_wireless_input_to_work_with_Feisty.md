---
title: "Getting wireless input to work with Feisty"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by stanbeer on 2007-04-16
Hi - I've tried searching through forum posts, talking to my local Linux guru over the phone and writing an article about this (for which I was mercilessly flamed).

I really do want to get my wireless keyboard and mouse working with my now fully installed Kubuntu Feisty beta so that I can hopefully write more about migrating to Linux from Windows.

I have a new Dell Latitude notebook with Core 2 Duo 2GHz and 2GB RAM. I have installed Kubuntu on an external USB hard drive rather than partition my notebook disk and have a dual boot configuration.

Kubuntu loads fine - actually the system generally has to be cold booted twice because it stalls the first time and gives me an error 21. I don't know if that's significant or an idiosyncracy of this particular beta.

My wireless USB mouse and keyboard are both Microsoft badged. However, my Linux guru assured me that these devices are  merely rebadged Logitech devices.

Any help would be appreciated.:)

---

### Post by muszek on 2007-04-17
While I don't know anything about your problem, I asked in #ubuntu on freenode and fiery-cleric reply.  Maybe this will help:
> muszek: well yeah i've never used wireless mouse/keyboard before so i am not much help ... but maybe that guy should find the vendor/product id of the device when he plugs it in and then searching on [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/) to see if it is supported under linux
muszek: he can find those ids from /proc/bus/usb/devices

---

### Post by encompass on 2007-04-17
well, type this at the command line will you?
lsusb
this will check your devices that are plugged in and make sure there are even seen.
Post the output here.

---

### Post by encompass on 2007-04-17
You should not highjack this post.  sorry but please make your questions in a new thread.
non the less... a very fast search give me this...
[http://ubuntuforums.org/showthread.php?t=75978](http://ubuntuforums.org/showthread.php?t=75978)
but you should really search first and not stumble around.

---

### Post by encompass on 2007-04-17
> **stanbeer said:**
> My wireless USB mouse and keyboard are both Microsoft badged. However, my Linux guru assured me that these devices are  merely rebadged Logitech devices.
What kind of keyboard are they? USB, Bluetooth, PS2, or like mine... both.
Did you make sure to press the sync buttons if any.... does this keyboard work in the bios(If you don't know what that is don't worry)?

---

### Post by PriceChild on 2007-04-17
The output of "lsusb" would be very helpful stanbeer. You never know what you're getting with Dells... they just plonk in whatever they have/is cheapest at the time.

---

### Post by leibowitz on 2007-04-17
I don't get it.

You said you want to use your wireless keyboard and mouse with Linux (Kubuntu), but you don't provide any useful information.

I know that you can't use them. That's a starting point.

What's the exact model of the keyboard/mouse combination ? Maybe someone has it and can check if everything's fine.

And finally, those devices are connected with the USB connector right ? Is the device not detected by Linux, or the USB port of the dell notebook ? ie. please try to put any USB device (Storage, or anything else) on the same USB port to see if it's detected.

PS: or maybe you just have to Enable the USB Legacy Support in the BIOS ?

---

### Post by encompass on 2007-04-17
> **leibowitz said:**
> I don't get it.
PS: or maybe you just have to Enable the USB Legacy Support in the BIOS ?
Would he really have to worry about legacy support in the bios when it was working before? Lets just get some feedback from his lsusb command.  If we can't see the device his usb has an issue, if we can see the usb device then we can find the driver or issues with it.  Keyboards and Mice not working in linux are the weirdest thing.  Most, because they need to work in the bios, need to have at lease basic support in any os. Even dos.

---

### Post by stanbeer on 2007-04-17
Hi - Microsoft Comfort Keyboard 1.0A; Microsoft Optical Mouse 2.0A. Both run off a dongle which has dual USB,PS2 jacks but is connected to PC via USB.

Both are enabled in the bios at boot up so there is no USB legacy support issue

---

### Post by stanbeer on 2007-04-17
> **encompass said:**
> What kind of keyboard are they? USB, Bluetooth, PS2, or like mine... both.
Did you make sure to press the sync buttons if any.... does this keyboard work in the bios(If you don't know what that is don't worry)?
Hi - Microsoft Comfort Keyboard 1.0A; Microsoft Optical Mouse 2.0A. Both run off a dongle which has dual USB,PS2 jacks but is connected to PC via USB.

Both are enabled in the bios at boot up so there is no USB legacy support issue

---

### Post by stanbeer on 2007-04-17
> **PriceChild said:**
> The output of "lsusb" would be very helpful stanbeer. You never know what you're getting with Dells... they just plonk in whatever they have/is cheapest at the time.
Thanks I've tried to avoid the command line - but will do as you say and try Isusb

---

### Post by encompass on 2007-04-18
Could you please post the output from the command:
lsusb
It is found in the terminal.
The terminal program can be found in Applications--->Accessories---> terminal
run the command and just copy and paste the output here...

---

### Post by encompass on 2007-04-18
[http://www.hardwareinreview.com/cms/content/view/42/1/](http://www.hardwareinreview.com/cms/content/view/42/1/)
is this is the hardware you have?

---

### Post by encompass on 2007-04-18
Interms of the command line... don't be scared.  I find that it is much better to do things there because of the nature of Linux.
For example, I am running ubuntu... so it is different then kubuntu in some ways. so to use the commandline gives a common environ for everyone to work in.

---

### Post by ckempo on 2007-04-18
Stan - it's "lsusb" as in "el, es, you, es, bee" not a capital "I" - just so you're aware.

---

### Post by GaryH on 2007-04-19
Everybody,
My Logitech wireless mouse and keyboard worked right out of the chute on  my IBM T20 running Feisty.
GaryH

---

### Post by leibowitz on 2007-04-19
That's not helping us at all.

I have a Benq Wireless Keyboard/Mouse working here also.

That is why it seems uncommon to have an USB device not recognised by Linux.

Edit: at least for the mouse/keyboard

---

### Post by Otkon on 2007-04-19
> **GaryH said:**
> Everybody,
My Logitech wireless mouse and keyboard worked right out of the chute on  my IBM T20 running Feisty.
GaryH

Weird. My Logitech S510 wireless keyboard and mouse do not work with either the full AMD64 DVD installation or the alternate AMD64 CD. I don't really feel like hooking up some old wired ones then getting past all the installation issues only to find out if I switch over to the wireless ones, they won't work.

---

### Post by bodean on 2007-04-20
-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 


My wireless mouse doesn't work in the 7.04 ubuntu either. No idea why.

---

### Post by GaryH on 2007-04-20
Everybody,
Results of lsusb for my T20 Feisty with working Logitec wireless:
[I]gary@gary-laptop:~$ lsusb
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. 
Bus 001 Device 002: ID 0424:2504 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000  
gary@gary-laptop:~$
[/I]
It's an outside chance but maybe moving the mouse while booting would help Feisty discover the wireless.

Good luck,
GaryH

---

### Post by encompass on 2007-04-20
Looks like it is not seen by your wireless... do you have a hub that it is plugged into at all?
You could also try unpluggin and plugging it back in while the computer is running... the usb part that is.. not the ps2... it would help there.
You would see something about the keyboard... all you have is something from asus tech.
btw... my wireless mouse and keyboard work perfecting in feisty... just installed the stable version.

---

### Post by Warpnow on 2007-05-30
I have the EXACT same problem with the EXACT same keyboard/mouse...

---

### Post by sn4265 on 2007-08-08
Same problem here with the same hardware.  Unfortunately, I can't provide you with a 'lsusb' output since I can't do ANYTHING at all when I boot the Ubuntu CD.  Any chance I missed a link to the resolution on this?  Thanks.

Scott

---

### Post by encompass on 2007-08-09
> **sn4265 said:**
> Same problem here with the same hardware.  Unfortunately, I can't provide you with a 'lsusb' output since I can't do ANYTHING at all when I boot the Ubuntu CD.  Any chance I missed a link to the resolution on this?  Thanks.

Scott
so you don't have linux installed but you have the same problem?
If you have ubuntu installed you can check if the usb device exists  according to the system with lsusb.
OKOK I see so you don't have any extra keyboards?
I am an out going guy, so I would go nextdoor and barrow one for a day.  I have done that from an old lady once. :P  Don't worry, we chilled all the time. (Like stealing a keyboard from a grandma!)

---

### Post by sn4265 on 2007-08-09
I suppose I can always bring home my keyboard and mouse from the office for a day or the weekend.

---

