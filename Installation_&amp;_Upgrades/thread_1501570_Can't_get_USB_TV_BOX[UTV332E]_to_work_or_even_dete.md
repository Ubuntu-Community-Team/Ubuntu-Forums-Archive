---
title: "Can't get USB TV BOX[UTV332E] to work or even detect ???"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by rockstarsavin on 2010-06-04
I have bought a USB TV Box device  (Gadmei USB TV Box UTV 332E). But my  ubuntu does not recognize it. While  it works perfectly on windows with  its CD driver.

**Here is what I get when I use [COLOR=DarkRed]lsusb[/COLOR] :**

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Blue]Bus 001 Device 002: ID 1f71:3301  [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and my [COLOR=DarkRed]**lsmod |grep em28**[/COLOR] output is:

v4l2_common            15431  1 em28xx
videodev               34361  2 em28xx,v4l2_common
ir_common              38875  1 em28xx
videobuf_vmalloc        5586  1 em28xx
videobuf_core          16356  2 em28xx,videobuf_vmalloc
tveeprom               11102  1 em28xx


and  **[COLOR=DarkRed]dmesg[/COLOR]** output is:


   64.517519] sr 0:0:1:0: [sr0] Add. Sense: L-EC uncorrectable error
[   64.517527] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 5b 6e 00 00 01 00
[   64.517545] end_request: I/O error, dev sr0, sector 93624
[   64.517552] Buffer I/O error on device sr0, logical block 23406
[   71.059863] sr 0:0:1:0: [sr0] Unhandled sense code
[   71.059869] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   71.059875] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[   71.059883] sr 0:0:1:0: [sr0] Add. Sense: L-EC uncorrectable error
[   71.059891] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 5b 6e 00 00 01 00
[   71.059909] end_request: I/O error, dev sr0, sector 93624
[   71.059916] Buffer I/O error on device sr0, logical block 23406
[   71.358474] ISO 9660 Extensions: Microsoft Joliet Level 3
[   71.602760] ISOFS: changing to secondary root
[ 1487.780041] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 1487.915429] usb 1-3: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[ 1487.918688] usb 1-3: configuration #1 chosen from 1 choice
[ 1813.339584] Linux video capture interface: v2.00
[ 1813.368530] usbcore: registered new interface driver em28xx
[ 1813.368850] em28xx driver loaded

**[SIZE=3][COLOR=Red]Please help, I am new to ubuntu and i have tried several other related posts as well, to get to know these commands.[/COLOR][/SIZE]**:confused::confused::confused::confused:

---

### Post by davidmohammed on 2010-06-04
I'm not familiar with what this device is - but the last message says that it is recognised - and is recognised as a video capture device.

Are you using something like tvtime or mythtv (available from synaptic) to view tv?

---

### Post by rockstarsavin on 2010-06-08
):P Thank you very much for the reply.

Yes  i have installed all the tv viewing softwares like xaw Tv, tvtime and ... others but the problem is   when i run the [COLOR=Red]video4linux control panel[/COLOR] form system->preference
I get this message, may be there is sth wrong.




**[COLOR=Red]Unable to open file /dev/video0[/COLOR]**
 **[COLOR=Red]No such file or directory[/COLOR]**


[B][COLOR=Red][COLOR=Black]Still no luck [/COLOR]
[/COLOR][/B]
[SIZE=4][COLOR=Green]
Please assist[/COLOR][/SIZE]

---

### Post by davidmohammed on 2010-06-08
ok,
  I've found a similar model as yours - [the post]("http://www.linuxforums.org/forum/ubuntu-help/111029-gadmei-utv-330-usb-tv-tuner.html") is a little old, but hopefully still applies to you.. but given you've got a new kernel, hopefully you wont have to compile stuff as suggested in the post.

reboot your PC without your usb device plugged in

then in a terminal type
dmesg

note where the last entry is.

plug in your device

type 
dmesg

copy and paste all the new output here in a code block

I'm hoping something like 
[ 2549.692000] em28xx #0: V4L2 device registered as /dev/video0
is displayed - or at least an error of some sort

I'm hoping also if you type
v4l-info

and

v4l-conf

this will give you more information about your device - if they give an error can you dump it here.

---

### Post by rockstarsavin on 2010-06-08
Thanks, [davidmohammed]("http://ubuntuforums.org/member.php?u=600258")
 

 Here is what I get when I reboot with the usb dev. Plugged in (**dmesg)**.
 

 > 0.288612] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
 

 

  0.739458] usb 1-3: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256 
 [    0.742591] usb 1-3: configuration #1 chosen from 1 choice 
 [    0.751212] Adding 1548376k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1548376k SS 
 

 [    0.603601] usb 1-3: new high speed USB device using ehci_hcd and address 2 
    0.739458] usb 1-3: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256 
 

 

 

 And outputs of
 

 > **v4l-info **
 open /dev/video0: No such file or directory 
 

 

 > **v4l-conf **
 v4l-conf: using X11 display :0.0 
 dga: version 2.0 
 WARNING: No DGA direct video mode for this display. 
 mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown 
 can't open /dev/video0: No such file or directory 
 

 Still no change. I have followed the blog you mentioned an have followed all the instruction earlier, but no luck.

---

### Post by rockstarsavin on 2010-06-09
**[COLOR=DarkRed]Please Help it is taking all my time, i cant focus on anything else unless i complete the installation ?[/COLOR]**

---

### Post by davidmohammed on 2010-06-09
The dmesg dump you gave doesnt make any sense - is that really the only output when you insert your usb device?  Need to see all of the output of dmesg immediately after the usb device is inserted and switched on.

When the usb device is inserted and switch on then it should report something like

[ 2549.628000] EEPROM ID= 0x9567eb1a
[ 2549.628000] Vendor/Product ID= eb1a:2861
[ 2549.628000] AC97 audio (5 sample rates)
[ 2549.628000] 500mA max power
[ 2549.628000] Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 2549.632000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[ 2549.632000] tuner 1-0060: chip found @ 0xc0 (em28xx #0)
[ 2549.632000] attach inform (default): detected I2C address c0
[ 2549.632000] tuner 0x60: Configuration acknowledged
[ 2549.632000] tuner 1-0060: type set to 69 (Tena TNF 5335 and similar models)
[ 2549.656000] saa7115 1-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[ 2549.684000] attach_inform: saa7113 detected.
[ 2549.692000] em28xx #0: V4L2 device registered as /dev/video0
[ 2549.692000] em28xx #0: Found Gadmei UTV330
[ 2549.692000] em28xx audio device (eb1a:2861): interface 1, class 1
[ 2549.692000] em28xx audio device (eb1a:2861): interface 2, class 1
[ 2549.900000] usbcore: registered new interface driver snd-usb-audio

also your latest dmesg doesnt look anything like your first post.
Have you only posted selected parts of the dmesg?

separately can you dump the results of the following

dmesg | grep em28xx

---

### Post by rockstarsavin on 2010-06-09
I am sorry for my earlier post, I just posted the lines containing usb. Here's my dmesg output



Please Help ! I dont't understand !!!!!!!!!!:confused::confused:

---

### Post by rockstarsavin on 2010-06-09
But when I use 

sudo modprobe em28xx
[COLOR=Red]
I dont know what this means [please tell me if you have time][/COLOR] :confused:

the output i mentioned changes

[CODE] dmesg | tail
[   24.375590] vboxdrv: Successfully loaded version 3.2.0 (interface 0x00140001).
[   25.516040] eth0: no IPv6 routers present
[

---

### Post by davidmohammed on 2010-06-10
Ok - that sound like good news - the em28xx module is the thing that is loaded when it recognises your USB device.

Given that you poked it via sudo modprobe em28xx, you saw that it loaded the driver into the kernel but the kernel did not really recognise your device still.

From that post with a similar sounding device to yours the guy did this..

sudo modprobe em28xx card=37

I would suggest you do something similar - examine dmesg and hopefully you will see something different than you current dmesg output.

if it doesnt work - you might want experiment with numbers other than 37.

dont forget when experimenting to unload the em28xx kernel module i.e.

sudo modprobe -r em28xx

before your next
sudo modprobe em28xx card =<number>

---

### Post by rockstarsavin on 2010-06-11
What other numbers to try

sudo modprobe em28xx card=[COLOR=Red]37[/COLOR]

[COLOR=Red](0~9999999)[/COLOR] is there some kind of range or is there some tricks i could find which number fits my device(brute force?)

Please help!!!!!!!!!!!!:confused:

---

### Post by davidmohammed on 2010-06-11
ok,
  I've done some research for you - bad news I'm afraid.  Your particular board is currently not recognized by the lucid kernel.  Nor is it listed in the em28xx source code

the nearest models with the GADMEI name (I believe that is the name of your manufacturer) is as follows:

#define EM2820_BOARD_GADMEI_UTV310		  25
#define EM2860_BOARD_GADMEI_UTV330		  37
#define EM2820_BOARD_GADMEI_TVR200		  62
#define EM2861_BOARD_GADMEI_UTV330PLUS           72

The last number in the above list is the card type you could try.

If this doesn't work, then you will have to start compiling kernel modules - dont worry it isnt as scary as it sounds.

The following [link]("http://forums.linuxmint.com/viewtopic.php?f=49&t=42181&p=244002") will help you.
... also [this link]("http://ubuntuforums.org/archive/index.php/t-869684.html") gives you a step by step guide on how to compile and insert details for your board

Alternatively - I would recommend you visit [this website]("http://www.linuxtv.org/") and post a request through them.  If they do fix your issue, they will fix it in source code.  You will still have to compile kernel modules yourself because em28xx only gets updated in the latest kernels - I would guess if you get a fix right now, then the next kernel to include your fix would be 2.6.36.  Thus you wont see that fix in a linux distribution like ubuntu until april next year!

I've tried my best.  Over to you I'm afraid.  Good luck.):P

---

### Post by rockstarsavin on 2010-06-11
Thank you David for your support, links and your time,
:confused:
I guess I will have to wail till others will buy this device, I think it is relatively a new product so..........

I have tried  compiling kernel as well but i end up with errors,

Anyway thank you and please reply me if you find sth new.

---

### Post by rockstarsavin on 2010-06-15
Hello David,
Can you help me with v4l-dvb kernel compilation of this device. I followed the link you have given but the link is not active.

```

hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel/

```

alternately i have downloaded from

```

hg clone http://linuxtv.org/hg/v4l-dvb

```

Please help me insert the details of my board, i followed the post and ended up with  errors 

```

make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/sabin/driver/v4l-dvb/v4l'
make: *** [all] Error 2



```

Please also tell me if it will help other wise i will stop trying !

---

### Post by davidmohammed on 2010-06-15
ok,
  I followed this to get the source code to compile

cd Downloads
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make release VER=2.6.32-22-generic
make

this started compiling and after about 5 minutes failed with the error 
make[3]: *** [/home/dad/Downloads/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/dad/Downloads/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dad/Downloads/v4l-dvb/v4l'
make: *** [all] Error 2
dad@ubuntu-laptop:~/Downloads/v4l-dvb$ 

I then typed
gedit v4l/.config

I searched for
CONFIG_DVB_FIREDTV=m
and changed it to read
CONFIG_DVB_FIREDTV=n
saved and exited gedit.

resumed the compile

make

this completed compiling successfully.

To add your board I would - at a guess - assume that your 332E is close to the GADMEI 330 model.  Unfortunately there is a similar 330plus model so you may have to have a go at two different coding; so backup the two files below that you will edit just in case you need to reinstate them later and try different coding.

for example assuming your 332E is similar to the 330 model I would

gedit linux/drivers/media/video/em28xx/em28xx.h

add a new line for your board - e.g. base on model 330 i.e. the line  #define ...GADMEI_UTV330    37

#define EM2800_BOARD_VC211A			  74
#define EM2882_BOARD_DIKOM_DK300		  75
**#define EM2860_BOARD_GADMEI_UTV332E		  76**

save and exit.

now for the interesting part - making the source code recognise your board

gedit linux/drivers/media/video/em28xx/em28xx-cards.c

search for EM2860_BOARD_GADMEI_UTV330
duplicate the section starting [EM...
   to  }, and replace the 330 with 332E i.e. your board

for example

[EM2860_BOARD_GADMEI_**UTV332E**] = {
		.name         = "Gadmei **UTV332E**",
		.valid        = EM28XX_BOARD_NOT_VALIDATED,
		.tuner_type   = TUNER_TNF_5335MF,
		.tda9887_conf = TDA9887_PRESENT,
		.decoder      = EM28XX_SAA711X,
		.input        = { {
			.type     = EM28XX_VMUX_TELEVISION,
			.vmux     = SAA7115_COMPOSITE2,
			.amux     = EM28XX_AMUX_VIDEO,
		}, {
			.type     = EM28XX_VMUX_COMPOSITE1,
			.vmux     = SAA7115_COMPOSITE0,
			.amux     = EM28XX_AMUX_LINE_IN,
		}, {
			.type     = EM28XX_VMUX_SVIDEO,
			.vmux     = SAA7115_SVIDEO3,
			.amux     = EM28XX_AMUX_LINE_IN,
		} },
	},
search again
you'll see the 330 board defining the USB ID
{ USB_DEVICE(0xeb1a, 0x50a6),
			.driver_info = EM2860_BOARD_GADMEI_UTV330 },
duplicate it and replace the IDs for your board ( you found this when you did lsusb) e.g.
{ USB_DEVICE(0x1f71, 0x3301),
			.driver_info = EM2860_BOARD_GADMEI_UTV332E },

save and exit

compile your new source code

make

it should compile without errors - if it doesnt you have made your code modifications incorrectly

then install the new modules you have compiled

sudo make install
sudo depmod -a

run a dmesg and note the output
plugin and switch on your device
run a dmesg

hopefully you will see the output change indicating that it has recognised your device and have created /dev/video0

I would love to test this code myself but since I dont have a tv tuner, all of this is just pure guess work.  I'm sure the v4l kernel guys on that website link would be more helpful than me on trying to understand how to code your board.

---

### Post by rockstarsavin on 2010-06-16
I followed all your steps but, the problem persists!
```

[ 4157.688032] usb 1-2: new high speed USB device using ehci_hcd and address 2
[ 4157.823413] usb 1-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[ 4157.826314] usb 1-2: configuration #1 chosen from 1 choice
[ 4157.848172] IR NEC protocol handler initialized
[ 4157.851073] IR RC5(x) protocol handler initialized
[ 4157.857285] Linux video capture interface: v2.00
[ 4157.868838] IR RC6 protocol handler initialized
[ 4157.869253] em28xx video device (1f71:3301): interface 0, class 255 found.
[ 4157.869257] em28xx This is an anciliary interface not used by the driver
[ 4157.869291] usbcore: registered new interface driver em28xx
[ 4157.869295] em28xx driver loaded
[ 4157.874011] IR JVC protocol handler initialized
[ 4157.876840] IR Sony protocol handler initialized
[ 5723.846560] usb 1-2: USB disconnect, address 2
[ 6199.924030] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 6200.059371] usb 1-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[ 6200.062517] usb 1-2: configuration #1 chosen from 1 choice
[ 6200.063200] em28xx video device (1f71:3301): interface 0, class 255 found.
[ 6200.063206] em28xx This is an anciliary interface not used by the driver


```

and they don't reply me at v4l.

---

### Post by davidmohammed on 2010-06-16
hi there,
  'fraid not much more help from me.  Difficult to investigate further without having the tuner to play with.

[ 6200.063200] em28xx video device (1f71:3301): interface 0, class 255 found.
[ 6200.063206] em28xx This is an anciliary interface not used by the driver

this part of the trace shows that the tv tuner is now understood by the kernel - however the last line says it doesnt understand that there is a "webcam" element of the tuner.

Can I suggest one more try - where you have duplicated the section starting [EM...
to }, 

use the same values as the UTV330PLUS i.e.

[EM2860_BOARD_GADMEI_UTV332E] = {
		.name         = "Gadmei UTV33E",
		.tuner_type   = TUNER_TNF_5335MF,
		.tda9887_conf = TDA9887_PRESENT,
		.ir_codes     = RC_MAP_GADMEI_RM008Z,
		.decoder      = EM28XX_SAA711X,
		.xclk         = EM28XX_XCLK_FREQUENCY_12MHZ,
		.input        = { {
			.type     = EM28XX_VMUX_TELEVISION,
			.vmux     = SAA7115_COMPOSITE2,
			.amux     = EM28XX_AMUX_VIDEO,
		}, {
			.type     = EM28XX_VMUX_COMPOSITE1,
			.vmux     = SAA7115_COMPOSITE0,
			.amux     = EM28XX_AMUX_LINE_IN,
		}, {
			.type     = EM28XX_VMUX_SVIDEO,
			.vmux     = SAA7115_SVIDEO3,
			.amux     = EM28XX_AMUX_LINE_IN,
		} },
	},

compile and install as before.

Assuming this doesnt work and you dont get any help from the v4l guys, then my only suggestion is to continue using the tuner under windows - or you might want to try virtualbox - install windows XP in virtual box, install the windows tuner software into that windows guest.  Then when you start the application, investigate running in "seamless mode".  This makes it look like the windows XP tuner application is running under ubuntu.

---

### Post by rockstarsavin on 2010-06-16
Thanks david,

I have been using virtual box, but i can assign only 128 MB video ram under it, so the performance is sluggish (video hangs for 1 to 2 seconds and resumes every now and then). Thats why I am trying to use it under ubuntu itself.

and also I have tried compiling both 330 and 300PLUS but I end up with same error mentioned on the earlier post.

---

### Post by rockstarsavin on 2010-06-17
David

Is there some way i can get more information about my device like what my device is similar to (like i came to know  it is not similar to 330 or 330plus). and can you  give me the mailing address of v4l guys(Don't they have forum ?).

---

### Post by davidmohammed on 2010-06-17
there is a [wiki page here]("http://www.linuxtv.org/wiki/index.php/Em28xx_devices") that you should read.  It has instructions on how to identify various information, and where to send that information.

---

### Post by rockstarsavin on 2010-06-19
This is getting very interesting I compiled and tried every thing , but........................
It seems I am the only one who is trying to use this device in Ubuntu

---

### Post by rockstarsavin on 2010-07-06
David is not there some kind of update yet that I could try????

---

### Post by davidmohammed on 2010-07-07
Hi there,
  I've looked at the latest experimental code tree - no mention of your model.

If I had your model tv-card I would try myself to code...!  

Sorry, can't help further.

---

