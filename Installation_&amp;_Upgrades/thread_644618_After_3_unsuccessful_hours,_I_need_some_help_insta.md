---
title: "After 3 unsuccessful hours, I need some help installing this."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by vpvega on 2007-12-19
So this is my first Linux install. 
While trying to install through the LiveCD (7.10) I've run into a brick wall.
Except for the Memory test option, every option results in the computer completely shutting off, I never make it to the splash screen. 
On one occasion right before shutoff, I saw a glint of an message and it said something about temperature. 
My CPU temp according to BIOS is 63C and MB temp is 35C
I looked around these forums, and a few others had similar problems. The best advice seemed to be adding the acpi command when booting. I tried it but, the computer still turns off before the splash screen. 
I actually do not know if I am entering the command properly. 
I press F6, and in the little command box that pops up, I go alll the way in front of the line and enter (before file=bla bla):  "noacpi acpi=off" without the " ". Is this the correct way to input these commands?

Thanks for reading

---

### Post by forestpixie on 2007-12-19
i thought you added them to the end, without the quotes - not completely sure though

---

### Post by vpvega on 2007-12-19
Does it matter where I add the commands? I've tried at the end as well, if i remember correctly beofre the --.

I should also add my system build to this:

Intel Pentium D 3Ghz
ASRock 775Dual Vsta
1GB of DDR1 Ram
3 Hard Drives( one on SATA)
2 Optical Drives
Power Color Radeon X800
Turtle Beach Santa Cruz

---

### Post by forestpixie on 2007-12-19
I think it does matter where you put them, not gonna be able to help much now - got to go

but - before you do naything else are you sure that the burn is ok, that the md5sum for the iso is ok and did you burn it slow 

you might also need to use the alternate install cd which isn't a livecd it's text bsed like a win install

md5sum
> ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

if the thread doesn't get much movement - use the report button and pretty please ask the mods if they'll move it to Absolute Beginners

I'll be back later to have a look, good luck

---

### Post by vpvega on 2007-12-19
Thanks Forest, I'll give it a try.

---

### Post by rsambuca on 2007-12-19
Yes, definitely check the md5sum of your iso first.
Burn the iso at a very slow rate.
Run the CD integrity check.

---

### Post by vpvega on 2007-12-20
Alright, md5 hashes are matching. 
I was able to install ubuntu with the alternate CD. So now I have a boot selection between XP and Ubuntu. But here's another problem. When I try to boot into ubuntu, my monitor shuts off. As in the LED on it turns red. Though I the computer continues to run. I can hear the HD crunching away. Any idea on what this is?

---

### Post by vpvega on 2007-12-20
An update. 

I can start Ubuntu by going into recovery mode and entering "startx".
But once ubuntu is loaded, I cannot install the restricted ATI drivers, because my internet does not work. 
So when I go to System>admin>network. I get an error message. saying I have no right to access it. What gives?

---

### Post by forestpixie on 2007-12-20
Now you've at least got close, you're going to need to give a bit more infromation here on you graphic card etc

in the meantime try having a look at these 2

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f5e28596120b064aca976f5c8a6ddacfee0d5065](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f5e28596120b064aca976f5c8a6ddacfee0d5065)

[http://ubuntuforums.org/showthread.php?t=632630&page=2](http://ubuntuforums.org/showthread.php?t=632630&page=2)

---

### Post by vpvega on 2007-12-20
> **forestpixie said:**
> Now you've at least got close, you're going to need to give a bit more infromation here on you graphic card etc

in the meantime try having a look at these 2

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f5e28596120b064aca976f5c8a6ddacfee0d5065](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f5e28596120b064aca976f5c8a6ddacfee0d5065)

[http://ubuntuforums.org/showthread.php?t=632630&page=2](http://ubuntuforums.org/showthread.php?t=632630&page=2)

What kind of info should I be providing?
its a Power Color Radeon X800

---

### Post by forestpixie on 2007-12-21
try reconfiguring x server

start in recovery mode and enter this

sudo dpkg-reconfigure xserver-xorg

try using ati (or radeon) - not completely sure here never usded an ati -  as a video driver, if that doesn't help redo the command and use vesa

if that get you started restart and then use restricted driver to get the right driver

---

### Post by c0met on 2007-12-21
Hi,

This might be a silly suggestion, but your problem sounds like you are trying to install the i386 version on Ubuntu onto a machine with a 64 bit processor. I did tried to mismatch Ubuntu and the machine recently; it doesn't work and it's incredibly frustrating. Try this version of Ubuntu "64bit AMD and Intel computers".

Good luck

---

### Post by snkmad on 2007-12-21
Actually you are wrong.
You can install with no problems any x86 OS on a 64-bit processor.
What you cant do is install a x86-x64 OS in a 32-bit processor.

About the network, you can see the status of the NIC using this command: ifconfig
If you use ADSL brigde to connect to the internet, use this command: sudo pppoeconf.

---

