---
title: "[GUIDE] Multiple LIRC serial devices"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by markdavidoff on 2010-07-02
[SIZE="5"]**1. Background:**[/SIZE]

My box had a serial IR Reciever which I built and plugged into my motherboard's only serial port, ttyS0, and set up to work with LIRC.

I later went and built myself a serial IR Blaster to work with the box too, and bought a PCI Serial card off ebay to attach it to, however, much to my despair, I learned that LIRC wasn't built for multiple serial devices. I also learned the hard way that a USB serial device wasn't going to work either.

I emailed the LIRC dev and asked about this, and he responded with something about compiling another lirc_serial device and assigning it a different number or something. Well, I was no module expert, so I figured that I was out of luck for the time being.

About a year later, I stumbed upon a guide from [OzMyth]("http://www.ozmyth.com/wiki/configuring+multiple+serial+ir+blasters").
It was written for Fedora, and was quite outdated, but with some modification, I worked it out, and now I will share my method

[SIZE="5"]**2. Before we begin:**[/SIZE]

I am boldly going to assume that you have lirc working for one of your serial devices. If not, please don't ask for help here, this tutorial is for those wishing to add a SECOND (or more) lirc serial device to their rig.

> _The Digital Camera Trick:_

If you are wanting to add an IR Blaster, I discovered a neat little trick to test IR devices.

Hold up a digital camera (a phone camera, for example) to an IR Remote, and hit buttons.

You will see the LED light up on the display of your digital camera! You can use this to test if your IR Blaster is working on a certain serial port!

Test your IR Blaster with my trick, and this command:

```
echo (lotsOfCharacters) > /dev/ttyS1
``` (or whatever your serial port number is).

You can test IR Reciever using:

```
cat < /dev/ttySX
``` (where X is your serial port number)

Once you have found a good serial port, and you know it's ttySx number, you need to get the address and IRQ of that port.
You can do this by entering:

```
dmesg | grep ttyS
```

My ttyS1 was at 0xbc00 (irq = 22). Yours will likely be different. _Note this down._

[SIZE="5"]**3. Get the stuff:**[/SIZE]

You will need to install **'dialog'** for the configure program included with lirc.

```
sudo apt-get install dialog
```

I have provided you with multiple alternatives for getting the source code you need, depending on your level of laziness/experience.
[LIST=1]
[*]You can download the pre-modified source code I have attached
[*]You can download the original source code from the lirc website, change the file names you need to change, and patch it with the attached patch I made.
[*]You can download the original source code from the lirc website and modify it yourself.
[/LIST]

_1. You have downloaded my modified code:_
[LIST]
[*]Extract the source code anywhere
[*]Skip to the "**Configuring and compiling**" section below
[/LIST]

_2. You have downloaded the original source code, and are going to modify it with the patch_
[LIST]
[*]Download the attached patch
[*]Download Source code to 0.86 from the LIRC website
[*]Extract the source code anywhere
[*]Rename /drivers/lirc_serial to /drivers/lirc_serial2, and rename lirc_serial.c to lirc_serial2.c
[*]Patch the code (google and man pages are your friend)
[/LIST]

[U]3. You are going to modify the source code yourself:
Download your source code from the LIRC website.[/U]
[LIST]
[*]Extract the source code anywhere
[*]Rename /drivers/lirc_serial to /drivers/lirc_serial2, and rename lirc_serial.c to lirc_serial2.c
[*]Use your own method to change all instances of lirc_serial to lirc_serial2 . I used Notepad++.
[/LIST]

[SIZE="5"]**4. Configuring and compiling:**[/SIZE]
> **UPDATE:**
edit your /etc/serial.conf file, and add the line (vary as appropriate for your new serial device):
```
setserial ttyS1 uart none
```
This will eliminate some problems

Also, using the same method, I have confirmed this working with Lirc 0.8.7

'cd' into the source code's directory, and run

```
./configure
```

go to driver configuration, and set up appropriately using the _address and IRQ_ you noted in the **"Before we begin"** section.

Hit _"save and run configure"_ option once you have done this.

```
cd drivers
sudo make
sudo make install
```

create a file called **lirc_serial2.sh** and place the script somewhere, let's assume your home directory:

```
#!/bin/sh
sleep 30
setserial /dev/ttyS1 uart none
mknod /dev/lirc2 c 61 1
cp -a /dev/lircd /dev/lircd2
modprobe lirc-serial2
sleep 5
/usr/sbin/lircd --driver=default --device=/dev/lirc2 --output=/dev/lircd2 --pidfile=/var/run/lircd2.pid --listen=8766 /etc/lirc/lircd2.conf
```

and make it executable with chmod. I used ```
sudo chmod a+x lirc_serial2.sh
```

The reason we have "sleep" commands is because I had problems with the setserial command not executing at the early booting stage.

Feel free to change the sleep times to whatever you like, but for me, my computer takes longer than 30 seconds to boot, so it worked out fine.

you can download my attached script, for the lazy.

The script above assumes your second serial device is ttyS1. Please modify the 'setserial' line appropriately to your serial device.

It also assumes that your intended config file is at /etc/lirc/lircd2.conf . Let's go edit it now...

```
sudo gedit /etc/lirc/lircd2.conf
```

This is where you tell lirc which remote codes file(s) it's going to read/send.

You can use lircd.conf as a template to set up your additional remote/blaster.

You can download my attached lircd2.conf if you need an example.

now, edit your **/etc/rc.local** file. You will need sudo access, and add the path of the script to the end of your file, but before the _"exit 0"_ line.

eg.

```
...

/home/<username goes here>/lirc_serial2.sh

exit 0
```

Now, edit your hardware.conf in /etc/lirc. I added the lines:

```
#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART)"
TRANSMITTER_MODULES="lirc_dev lirc_serial2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc2"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/home/myth/FoxtelDigital"
TRANSMITTER_LIRCD_ARGS="/etc/lirc/lircd2.conf"


```

"/home/myth/FoxtelDigital" is my remote config. You can download a compatible foxtel remote config by [clicking here]("http://www.ozmyth.com/wiki/_media/lircd.conf?id=configuring%2Blirc%2Bfor%2Bfoxtel&cache=cache").

I have attached my hardware.conf file, in case you want it.

Now reboot!

**[SIZE="5"]5. Testing:[/SIZE]**

If you attached an IR Blaster, you can test it with irsend, but use --device=/dev/lircd2 in the parameters

eg.

```
irsend &#8211;-device=/dev/lircd2 SEND_ONCE directtv power
```
And use my camera trick above to see if it worked!

Also make sure your original serial device works.

**Congratulations!**
Hopefully you now have two working LIRC serial devices!

**[SIZE="4"]List of attachments:[/SIZE]**
(I had to zip them all (except the .sh file), and the source code is in two parts. This is due to restrictions on the forum, sorry.):

[LIST=1]
[*]**lirc-0.8.6.zip** - Modified source code, ready for compilation. In two parts due to file size restrictions on this forum (option 1)
[*]**lirc_serial2.patch** - a patch for the source code if you choose to patch it yourself (option 2)
[*]**lirc_serial2.sh** - My lirc_serial2 boot initialization script, for the lazy
[*]**hardware.conf** - my sample lirc hardware.conf file, for the inquisitive
[/LIST]

---

