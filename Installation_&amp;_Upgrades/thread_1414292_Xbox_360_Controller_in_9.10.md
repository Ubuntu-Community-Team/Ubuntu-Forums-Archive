---
title: "Xbox 360 Controller in 9.10"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Drumber on 2010-02-23
Ok, so I'm trying to get my Xbox 360 controller (wired) to work with Ubuntu using [this]("https://help.ubuntu.com/community/Xbox360Controller") guide. First problem is with:

```
sudo apt-get install jscalibrator libgii1 libjsw2
```None of those packages seem to exist, but it says they are optional, so I moved on for now.
Second problem is when trying to run "make" under the compiling and installing the driver section. It get the following:

```
make modules -C /usr/src/linux-headers-2.6.31-19-generic SUBDIRS=/home/jake/.x360
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/jake/.x360/xpad.o
/home/jake/.x360/xpad.c: In function ‘xpad_wireless_connect’:
/home/jake/.x360/xpad.c:291: error: implicit declaration of function ‘info’
/home/jake/.x360/xpad.c: In function ‘xpad_open’:
/home/jake/.x360/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/jake/.x360/xpad.c: In function ‘xpad_close’:
/home/jake/.x360/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/jake/.x360/xpad.c: In function ‘xpad_probe’:
/home/jake/.x360/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/jake/.x360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/jake/.x360/xpad.o] Error 1
make[1]: *** [_module_/home/jake/.x360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [all] Error 2

```
I searched around and couldn't find any help. So, can anyone here give me a hand?

---

### Post by MiceMiceRabies on 2010-03-01
I get the same issues as stated above.  

I have had some luck when my Makefile contains 

KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.c

all:
        $(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.c /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick


in this file I changed the extension of xpad.o or xpad.ko to xpad.c
then the rest of the commands in the xbox360controller instructions seem to work.  I still cannot get my joystick to register.

any help is appreciated

---

### Post by Drumber on 2010-03-02
I changed my makefile as stated and it worked. (Or it didn't give me any errors at least.) Moving on to the testing portion, I plug in and run "dmesg" and get a massive amount returned, the interesting bits being (I think):

```
[ 7507.458058] usbcore: registered new interface driver xpad
[ 7507.458068] xpad: X-Box pad driver
[ 7539.456671] usb 5-3: USB disconnect, address 3
[ 7542.816062] usb 5-3: new full speed USB device using ohci_hcd and address 4
[ 7542.992086] usb 5-3: configuration #1 chosen from 1 choice
[ 7542.995355] Registered led device: xpad0
[ 7542.995485] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input7

```

So I think that means its found the device, right? jscalibrator wouldn't install, so I can't configure it. Bit stuck now.

---

### Post by MiceMiceRabies on 2010-03-03
you have gotten further then I have.  The only wired xbox360 controller I have is an arcade stick.  My system isnt picking it up at all, I read that other people are having the same problem.  A friend of mine said that on Lucid he is having no problems with his arcade stick, that it works plug and play.

ANYWAY, now that your controller is detected use JoyToKey to calibrate it,  also a great key mapper you can use is qjoypad, you will have to build that from source as well.  forget about jscalibrator.

so for joy2key 
$ sudo apt-get install joy2key


then to run and calibrate 

$ joy2key -dev /dev/input/js0 -terminal

and follow on screen prompt.

I think that Qjoypad may also have a calibrator in GUI which maybe easier.

---

### Post by proxess on 2010-03-03
Seriously? I just connect mine and play zsnes... 9.10 has default support for xpad360.

---

### Post by MiceMiceRabies on 2010-03-03
are you playing with an arcade style joystick?  or a game pad?

---

### Post by Drumber on 2010-03-04
> **MiceMiceRabies said:**
> you have gotten further then I have.  The only wired xbox360 controller I have is an arcade stick.  My system isnt picking it up at all, I read that other people are having the same problem.  A friend of mine said that on Lucid he is having no problems with his arcade stick, that it works plug and play.

ANYWAY, now that your controller is detected use JoyToKey to calibrate it,  also a great key mapper you can use is qjoypad, you will have to build that from source as well.  forget about jscalibrator.

so for joy2key 
$ sudo apt-get install joy2key


then to run and calibrate 

$ joy2key -dev /dev/input/js0 -terminal

and follow on screen prompt.

I think that Qjoypad may also have a calibrator in GUI which maybe easier.

Ah, cheers. Joy2key definitely recognises my controller, which is nice, but I am having trouble configuring it. What is the form of the .joy2keyrc file?

---

