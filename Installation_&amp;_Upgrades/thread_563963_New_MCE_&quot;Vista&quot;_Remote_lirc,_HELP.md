---
title: "New MCE &quot;Vista&quot; Remote lirc, HELP"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by dwf_starband on 2007-09-30
Ive just installed a WinTV-PVR 150 Media Center Kit which comes with a usb ir receiver/transmitter.

Its the black remote pictured at [http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)

That site says "Version 1069 (black remote) comes with a new SMK IR receiver which requires lirc_mceusb even though it is a newly released remote."

I have been following the instructions at 

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

but am having dificulties when it comes to testing with the command "irw" It returns a command prompt without waiting for input from the remote.  If i enter "irw" again it says "connect: Connection refused"
If I restart lirc then i can enter the command "irw" again but it still just returns a command prompt.

dmesg | grep -i lirc              shows me

[   36.604091] lirc_dev: IR Remote Control driver registered, at major 61
[   36.616146] lirc_mceusb: no version for "lirc_unregister_plugin" found: kernel tainted.
[   36.616762] usbcore: registered new interface driver lirc_mceusb
[   36.617079] /usr/src/modules/lirc/drivers/lirc_mceusb/lirc_mceusb.c: USB Microsoft IR Transceiver Driver v0.2


does anyone know what I am doing wrong?
does anyone know what "lirc_mceusb: no version for "lirc_unregister_plugin" found: kernel tainted." means?

can anyone help me?

Dennis

---

### Post by Dilligaf on 2007-09-30
I think you need lirc_mceusb2 for the new mce remotes.

Mike

---

### Post by dwf_starband on 2007-09-30
> **Dilligaf said:**
> I think you need lirc_mceusb2 for the new mce remotes.

Mike

I have tried that as well, but if you look at the link i listed 

[http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)

it shows my remote and talkes about it using the mceusb even though its a newer one.

thanks,

dennis

---

### Post by Dilligaf on 2007-09-30
That site is confusing. Under the picture in features it says mceusb2. in the test later it says mceusb. I don't know which is right. I would assume mceusb2 as it is a newer remote.

Mike

---

### Post by dwf_starband on 2007-09-30
here is a section from that page which makes it clear.

****************************************************************************************************************************

Windows Vista MCE Remote 

Another newer remote (version 1069) now responds with the following when you type lsusb: 
# lsusb
Bus 002 Device 002: ID 0609:0334 SMK Manufacturing, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

This remote requires the mceusb _not_ the mceusb2 LIRC module. 

Use the default mceusb2 lircd.conf file and all of the remote's keys work without modifying the example mceusb2 lircd.conf file.

****************************************************************************************************************************

I get the SMK Manufacturing, Inc when i lsusb
so i need to use the mceusb module and the mceusb2 lircd.conf file

That is what i have been trying, but still its not working.

I am still getting the command prompt after "irw"

thanks,
dennis

---

### Post by Cuppa-Chino on 2007-10-06
hmmm I wish I could even get that far!

using [https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty#head-e4d7df8eaaa06d6b36b29f7af3f69f881588d8ce")

I get to the step:

```
Start Lirc & Test

The modules will load when you start lirc, if they aren't already loaded.

    *

      $ sudo /etc/init.d/lirc start
```

and then I always get this output:
```
desktop:/usr/bin$ sudo /etc/init.d/lirc restart
Stopping lirc daemon: lircmd lircd.
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

```

trying to start **irw** nothing happens --> immediate command prompt, oddly enough mythbuntu gutsy beta worked out of the box for my remote...

any ideas

---

### Post by Cuppa-Chino on 2007-10-07
Ok more bits and bobs:

a) I forgot that my video card has remote as well:
```
desktop:~$ cat /proc/bus/input/devices
I: Bus=0001 Vendor=1822 Product=0019 Version=0001
N: Name="cx88 IR (digitalnow DNTV Live! "
P: Phys=pci-0000:00:0c.2/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=100fc326 69d000900000000 0 80118000 1a840004001 9e16c000000000 8ffc

```

NB I cannot see the usb remote there.
```
desktop:~$ lsusb
Bus 005 Device 004: ID 0424:2504 Standard Microsystems Corp.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 003: ID 041e:403a Creative Technology, Ltd WebCam NX Pro 2
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0471:060c Philips
Bus 001 Device 001: ID 0000:0000

``` 
NB Standard Microsystems Corp refers to a USB hub, Philips is the remote

b) I get a kernel tainted reply:
```
desktop:~$ dmesg | grep lirc
[   75.107179] lirc_dev: IR Remote Control driver registered, at major 61
[   75.132570] lirc_mceusb: no version for "lirc_unregister_plugin" found: kernel tainted.
[   75.136397] usbcore: registered new interface driver lirc_mceusb
[   75.136516] /usr/src/modules/lirc/drivers/lirc_mceusb/lirc_mceusb.c: USB Microsoft IR Transceiver Driver v0.2

```

any help -- the philips goes with mceusb not mceusb2 right?

---

### Post by gumperoncini on 2007-10-08
I am having the same problem with the same remote. 

I have installed EVERY possible combination of the mceusb and mceusb2 configurations and I cannot get irw to work. 

I get the same kernel tainted thing from dmesg and the lsusb shows the SMK device.

PLEASE, someone help us!!!

---

### Post by gumperoncini on 2007-10-10
I fixed the problem by installing mythbuntu beta - worked like a freakin charm. no issues at all. 

the remote buttons are sticky but that should be a cinch compared to the problems I had trying to install mythtv on ubuntu

---

### Post by mskradri on 2007-10-12
> **dwf_starband said:**
> here is a section from that page which makes it clear.

****************************************************************************************************************************

Windows Vista MCE Remote 

Another newer remote (version 1069) now responds with the following when you type lsusb: 
# lsusb
Bus 002 Device 002: ID 0609:0334 SMK Manufacturing, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

This remote requires the mceusb _not_ the mceusb2 LIRC module. 

Use the default mceusb2 lircd.conf file and all of the remote's keys work without modifying the example mceusb2 lircd.conf file.

****************************************************************************************************************************

I get the SMK Manufacturing, Inc when i lsusb
so i need to use the mceusb module and the mceusb2 lircd.conf file

That is what i have been trying, but still its not working.

I am still getting the command prompt after "irw"

thanks,
dennis

Dennis,
Sounds like I have the same new Hauppauge WinTV-PVR 150MCE with the black remote.
I also tried all variations of mceusb vs mceusb2 modules and mceusb lircd.conf vs mceusb2 lircd.conf.
Each time I would get to the same errors you are getting. 

I just tried the just released Mythbunto 7.10 RC iso. During the installation, I chose the "Windows Media Center Remote (Old version)" and every worked.

Kris

---

### Post by dwf_starband on 2007-10-13
> **mskradri said:**
> Dennis,
Sounds like I have the same new Hauppauge WinTV-PVR 150MCE with the black remote.
I also tried all variations of mceusb vs mceusb2 modules and mceusb lircd.conf vs mceusb2 lircd.conf.
Each time I would get to the same errors you are getting. 

I just tried the just released Mythbunto 7.10 RC iso. During the installation, I chose the "Windows Media Center Remote (Old version)" and every worked.

Kris

Thanks for your info,

are you using just the remote, or are you transmitting as well?
I have Dish Network and need to be able to change the channels on the receiver.

thanks,

dennis

---

### Post by mskradri on 2007-10-13
> **dwf_starband said:**
> Thanks for your info,

are you using just the remote, or are you transmitting as well?
I have Dish Network and need to be able to change the channels on the receiver.

thanks,

dennis

I haven't tried transmitting yet.
Others have reported problems:
[http://ubuntuforums.org/showthread.php?t=461901&highlight=hauppauge+remote+lirc](http://ubuntuforums.org/showthread.php?t=461901&highlight=hauppauge+remote+lirc)

I would ideally like a full Ubuntu graphical desktop along 
with MythTV, so I'm now trying to install Ubuntu 7.10RC 
desktop and then install MythTV. We'll see how the LIRC 
install goes in 7.10. 

There is a tutorial for installing LIRC on 7.10:
[https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy)

Kris

---

### Post by Cuppa-Chino on 2007-10-15
> **Cuppa-Chino said:**
> Ok more bits and bobs:

a) I forgot that my video card has remote as well:
```
desktop:~$ ...

```

NB I cannot see the usb remote there.
```
desktop:~$ ...

``` 
NB Standard Microsystems Corp refers to a USB hub, Philips is the remote

b) I get a kernel tainted reply:
```
desktop:~$ ...

```

any help -- the philips goes with mceusb not mceusb2 right?

managed to get the cx88 IR installed and now works great with irkick

also managed to get the philips to work with mythtv rightout of the bag

---

### Post by Hopworks on 2007-10-28
> **mskradri said:**
> Dennis,
Sounds like I have the same new Hauppauge WinTV-PVR 150MCE with the black remote.
I also tried all variations of mceusb vs mceusb2 modules and mceusb lircd.conf vs mceusb2 lircd.conf.
Each time I would get to the same errors you are getting. 

I just tried the just released Mythbunto 7.10 RC iso. During the installation, I chose the "Windows Media Center Remote (Old version)" and every worked.

Kris
Did you get an IR Blaster as well? I have the same remote package I think, but it came with the currently unsupported 1600. I am using a PVR-150 now, but still trying to get the remote and IR Blaster to work with MythTV. The remote is black as you stated, and I know that site that was linked in this thread very well. It states that support is limited to remote support only, and IR Blaster is not supported.

The information on the USB receiver and remote are;
SMK Model RXX6000-0141E and the remote, RRS9002-86XXF

The IR Blaster device plugs into the back of the receiver module, and there are two connection ports (I have no idea why).

I'm getting ready to send this remote package back to hauppauge for a replacement but would rather use it if I can.

And I NEED that IR Blaster to change channels on my cable box.

Sorry, I know this thread is 2 weeks old, but it turned up in a suggestions search as I was trying to post a new cry for help.

Thanks for your time!

Hop

---

### Post by dwf_starband on 2007-10-29
I am using a different transeiver for my backend/frontend/desktop which is working fine and just set up an old computer to use as a seperate frontend.  Im using this remote and its working fine after some dificulity.

I installed mythbuntu and selected the old remote.  The receiver would light up whenever I pushed buttons on the remote, but didnt do anythihng in the frontend.  I exited myth-frontend and ran irw in a terminal and it "hung" waiting for input from the remote just like it was supposed to but never registered anything from the remote even though the receiver light up each time i pushed a button.

I tried all sorts of things including recording the remote but nothing worked.  The closest I got was getting every button on the remote to register "One" in irw. (not very useful!)

I had another old computer that i decided to try it on, so I riped the hard drive out and put it in the other computer and everything worked great.

Im not sure what the difference was, maybe something was damaged on the first computer I tried, I dont know.  They were both restricted to usb1.1 but it worked with the same installation on the same hard drive.

I doubt this helps anyone but thought I would share just in case.

Its worth trying a different computer to make sure its not a hardware issue.

dennis

---

### Post by ryansinn on 2008-03-26
I'm the person who originally got that black mce usb remote and created the MythTV Wiki entry for it... 

It was insanity to setup the first time, but has been working flawless since then -- 

I'm monitoring this thread now, so if anybody still has issues, let me know.

I want to get a 100% complete / working .lircrc file on the wiki for the black remote soon (with a photo including text + arrows defining each button.)  I've been testing everything and had no issues so far.


Ryan

---

