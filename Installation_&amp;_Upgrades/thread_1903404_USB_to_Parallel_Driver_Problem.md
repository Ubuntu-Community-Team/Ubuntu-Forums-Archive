---
title: "USB to Parallel Driver Problem"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by nuwan243 on 2012-01-02
**USB to Parallel Driver Problem** 			
 			 			 		   		 		 		Wish u all a very Happy New Year!!!!!!

I purchased a USB to Parallel port cable ( it supports ieee1284  standard).This cable is Plug and play cable. it will successfully  install as USB Printing Support at the Device Manager in Windows 7.

[COLOR=Red]Is there a way or Driver to install this as a Parallel port in the Computer with Linux enviorenment?[/COLOR]

This is because i need to use this cable for a JTAG programmer. i dont  have a parallel port on my laptop.If i will be able to install USB to  Parallel Cable(which support ieee1284) as a true parallel port the JTAG  software will support the JTAG Programmer.

I did lots of things regarding this work. Dear all experts Please help  me to resolve this.Im in a sereous issue on this problem.Thank you  verymuch. and Have a nice time.

---

### Post by lkraemer on 2012-01-03
While I've only used one USB to Parallel Cable, (Cables To GO....I believe),
it worked out of the box on my Parallel Printer.  I think yours would do
the same.

Try this in a terminal to see that it's recognized:
```

dmesg | tail

```
then plug in the USB to Parallel Cable and do:
```

dmesg | tail
sudo lshw -C usb
lsusb

```
for more detailed information.

As an example, I've ran the command and then plugged in my USB to Serial
Adapter and I get:
```

larry@debian:~$ lsusb
Bus 002 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
larry@debian:~$ lsusb
Bus 002 Device 007: **ID 058f:9720** Alcor Micro Corp. USB-Serial Adapter
Bus 002 Device 006: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
larry@debian:~$

```
Now I can get more information by adding a couple of options to lsusb,
by adding the VENDOR : PRODUCT information **058f:9720**.

```

lsusb -v -d **058f:9720**

```


If your software is writing to the Parallel port you may need to create a 
symbolic link to the USB device to get the software's output routed
through to the USB Parallel port.  A real Parallel port in *nix typically
is a /dev/lp0 or /dev/lp1 device.  (The USB to Serial Adapter typically are
/dev/ttyACMO or /dev/ttyUSB0, but I've never looked for the USB to Parallel
Cable.)

I've listed the "ls -alt /dev/u*" devices on my Desktop with the USB to Parallel Cable:
> 
larry@LK-Ubuntu:~$ ls -alt /dev/u*
lrwxrwxrwx 1 root root       7 2012-01-03 14:15 /dev/usblp0 -> usb/lp0
lrwxrwxrwx 1 root root       7 2012-01-03 10:29 /dev/usblp1 -> usb/lp1

and the links are shown.......

I've done this type of thing for the Serial Port and it works GREAT!

It appears as you are in for a bit of reading..............

REF: [http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html](http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html)

lk

---

### Post by nuwan243 on 2012-01-06
Thanks for your valuble answer.after the lsusb message i cant find my usb device im new to Linux enviorenment.Please help me.Thank you again!!!!

---

### Post by lkraemer on 2012-01-07
If you have followed my previous post EXACTLY, and you see no difference in
the ```
dmesg | tail
``` commands (**before** USB Device is plugged in, and **after** USB Device is plugged in) your device isn't recognized
by *nix, and no one can help.  You need a device that is detected by *nix.

So, repeat the above steps to make 100% sure.......

lk

---

### Post by nuwan243 on 2012-01-13
for the following codes;
dmesg | tail
sudo lshw -C usb
lsusb
Out put as follows

nuwan@nuwan-laptop:~$ dmesg | tail
[  723.088192] usb 7-1: USB disconnect, address 4
[  723.088410] usblp0: removed
[  757.388063] usb 7-1: new full speed USB device using uhci_hcd and address 5
[  757.568404] usb 7-1: configuration #1 chosen from 1 choice
[  757.672381] usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[  761.776187] usb 7-1: USB disconnect, address 5
[  761.776401] usblp0: removed
[  862.836155] usb 7-1: new full speed USB device using uhci_hcd and address 6
[  863.016403] usb 7-1: configuration #1 chosen from 1 choice
[  863.024416] usblp0: USB Bidirectional printer dev 6 if 0 alt 1 proto 2 vid 0x067B pid 0x2305

nuwan@nuwan-laptop:~$ sudo lshw -C usb
[sudo] password for nuwan: 
nuwan@nuwan-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 15d9:0a4c Unknown 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:180c Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nuwan@nuwan-laptop:~$ 

[COLOR=Red]

with out the cable also the result is same as above.............[/COLOR]


for the following command 
ls -alt /dev/u*

 the output will be like below;

nuwan@nuwan-laptop:~$ ls -alt /dev/u*
crw-rw-rw- 1 root root   1, 9 2012-01-13 19:39 /dev/urandom
crw-rw---- 1 root root 253, 0 2012-01-13 14:39 /dev/usbmon0
crw-rw---- 1 root root 253, 2 2012-01-13 14:39 /dev/usbmon2
crw-rw---- 1 root root 253, 6 2012-01-13 14:39 /dev/usbmon6
crw-rw---- 1 root root 253, 1 2012-01-13 14:39 /dev/usbmon1
crw-rw---- 1 root root 253, 5 2012-01-13 14:39 /dev/usbmon5
crw-rw---- 1 root root 253, 4 2012-01-13 14:39 /dev/usbmon4
crw-rw---- 1 root root 253, 8 2012-01-13 14:39 /dev/usbmon8
crw-rw---- 1 root root 253, 3 2012-01-13 14:39 /dev/usbmon3
crw-rw---- 1 root root 253, 7 2012-01-13 14:39 /dev/usbmon7
lrwxrwxrwx 1 root root      7 2012-01-13 09:22 /dev/usblp0 -> usb/lp0

/dev/usb:
total 0
drwxr-xr-x 18 root root   3920 2012-01-13 09:57 ..
drwxr-xr-x  2 root root     60 2012-01-13 09:22 .
crw-rw----  1 root lp   180, 0 2012-01-13 09:22 lp0


[COLOR=Red]I dont know much more about linux enviorenment...... sorry for the big codings in the forum. Im sorry. Please help me friend. Have a nice time!!!!![/COLOR]

---

### Post by lkraemer on 2012-01-14
Why don't you try creating a symbolic link from lpt1 to /dev/usblp0 by doing the following:
```

ln -s /dev/usblp0 lpt1

```
then run your JTAG Programmer software and make sure it is set for lpt1.  
Maybe it will work to communicate with your Programmer.

You can always remove the symbolic link with:
```

sudo rm lpt1

```
if it doesn't work.

lk

---

### Post by nuwan243 on 2012-01-15
Thanks for the interesting answer.how i check the mapped port for  lpt is gonna work. in the last answer u have mentioned about adding and removing LPT port to usb( mapping).

is there a  seperate software to monitor and control outputs of parallel port? i mean the votages of pins of the parallel port? 

Cheers!!!!!! Thanks again!!!!!

---

### Post by lkraemer on 2012-01-16
Here is a site that has the information you need.

[http://www.epanorama.net/circuits/parallel_output.html](http://www.epanorama.net/circuits/parallel_output.html)

But, I think you are making this too hard.  If the Printer Functions
under Windows with the USB to Parallel Cable, *nix should see it also.
  
Is the JTAG Programmer software for *nix or Windows?  Have you tried
running the Windows Software under WINE or in Crossover by Codeweavers?

Have a look here:
[http://www-user.tu-chemnitz.de/~heha/bastelecke/Rund%20um%20den%20PC/USB2LPT/index.html.en](http://www-user.tu-chemnitz.de/~heha/bastelecke/Rund%20um%20den%20PC/USB2LPT/index.html.en)


lk

---

### Post by nuwan243 on 2012-01-20
Thanks for the Nice reply. I have tried the first link u provided above.but i failed to install my cable with that software.That was the only software i found for this purpose.But the problem was i cannot install the above given driver because my cable is automatically installed as a USB printer suppport device.but i want to install that like a true parallel port device under Ports in device manager in Windows enviorenment.But i failed to find a solution under windows.

following link specify there is a problem of mapping USB to a True LPT port.

[http://www.microchip.com/forums/m491714-print.aspx](http://www.microchip.com/forums/m491714-print.aspx)

So i guessed that i can find a solution with linux. Thats why still im trying this.

The Second link u sent me was notworking. Any way thank you very much for the kindness u have payed for my question.Its very big for me.if u can send me an alternative link for the second link you provided.Thank you verymuch and have a nice time!!!!!

---

### Post by lkraemer on 2012-01-26
The link is:
[http://www.epanorama.net/circuits/parallel_output.html](http://www.epanorama.net/circuits/parallel_output.html)


LK

---

### Post by Witold Wolski on 2012-05-18
Hello everyone,
I am new on this forum even if being Linux user since years.
But I have just the same problem now with my "new" laptop-without-lpt having to cooperate with  an old printer-without-usb.
What's been written above is all very useful, but... :

WHAT TO DO IF NOTHING RESSEMBLING ***/****dev/usblp0*** OR ***/usb/lp0*** APPEARS AT ALL IN MY KRUSADER ???

Still, the lsusb code shows clearly an usb-lpt adapter recognized :

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a125 Suyin Corp. 
Bus 004 Device 004: ID 046d:c503 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 012: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
**Bus 002 Device 020: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port**
Bus 002 Device 014: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 002 Device 016: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver

as this line disappears while the adater is disconnected...

ANY IDEAS ??

My current OS is LinuxMint12 _based_ on Ubuntu (I abandoned Ubuntu recently because of its layout becoming uglier and uglier from one version to another...)

Thanks in advance

ww

---

### Post by lkraemer on 2012-05-19
Wolski,
Since your USB to Parallel Hardware is detected, you just need to
create a symbolic link from your USB device, which links your USB
device to whatever Krusader wants/has in the menu.

Assume Krusader has a menu item for lp0, or lp1
Assume your USB to Parallel is detected by your System as /dev/usblp0

You can compare the contents of /dev/usb* and /dev/l* before and after
you plug in the USB to Parallel adapter to locate what it is named by
your system.
 
Create a symbolic link from lp0 or lp1 to /dev/usblp0 (or whatever your
system assigns as the device name) by doing the following:
```

ln -s /dev/usblp0 lp0

```
then run Krusader (software ????) and make sure it is set for lp0 in the menu.
Test to make sure it works correctly.

You can always remove the symbolic link with:
```

sudo rm lp0

```
if it doesn't work.

lk

---

### Post by Witold Wolski on 2012-05-22
Hi lkraemer and thanks for your concern !

Looking for solutions or bug reports at LinuxMint page, after my report,  I found out that a new version - 13, based on Precise - has just been out. So instead of looking further how to mend th v.12 I've decided to install v.13, what I am now doing.
Hence my not answering.
But as soon as I have finished installing this (and here the LPT-USB printing works the same way as it does in Precise, not very elegant one but sure : usb://Unknown/Printer) I will come back to v.12 to try out your solution, so you can have, as well as other users,  an interesting feedback, hope I.

But I am now more or less convinced that it is somehow depending on the machine itself - I am not very trustful to these Windows-from-factory computers with very reduced BIOS, as my Compaq Presario is...  I have for example a severe hibernation / suspend problem which doesn't occur, with same OS, on my desktop computer....
It might be similar with this printing bug. 

So - till the while - Wezran

---

### Post by Witold Wolski on 2012-05-23
Hi lk,

OK :
 I created the link "ln -s /dev/bus/usb/002/011 /dev/lp0", re-installed the printer (HP LaserJet 2p plus) which appears now to be attached to "parallel:/dev/lp0" 
and _no printing of whatsever came  out of it_.

The dmesg | tail output after this  is :

usb 2-3.4.3: usbfs: process 4279 (usb) did not claim interface 1 before use

(And these same devices work under Ubuntu 12.04...)

Besides, anothe problem is that the device number (presently 011) changes at every connection, so the printer would need to be reinstalled with every session from beginning...

ww

---

