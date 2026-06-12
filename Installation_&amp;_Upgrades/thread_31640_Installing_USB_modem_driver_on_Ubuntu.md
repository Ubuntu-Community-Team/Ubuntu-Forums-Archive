---
title: "Installing USB modem driver on Ubuntu"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by zodmaner on 2005-05-04
Hello! this is my first post, so be gentle please  :razz: 

I'm trying to install my USB modem driver (Billion BIPAC-7000) and when I issue a "make" command to compile my driver this is what I get :

gcc -O2 -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -DCPU=686 -march=i686  -DMODULE -D__KERNEL__ -DLINUX  -I/lib/modules/`uname -r`/build/include -c BlSrv.c -o BlSrv.o
BlSrv.c: In function `BlDatagramSend':
BlSrv.c:250: warning: passing arg 4 of `USBADSL_ProcessMPXFR' from incompatible pointer type
BlSrv.c: In function `USBADSL_ProcessMPXFR':
BlSrv.c:325: error: `USB_QUEUE_BULK' undeclared (first use in this function)
BlSrv.c:325: error: (Each undeclared identifier is reported only once
BlSrv.c:325: error: for each function it appears in.)
BlSrv.c:327: error: too few arguments to function `usb_submit_urb'
BlSrv.c: In function `BlDatagramReceive':
BlSrv.c:404: warning: passing arg 4 of `USBADSL_MPReceivePacket' from incompatible pointer type
make: *** [BlSrv.o] Error 1

what happen? good people at Linuxquestions.org told me that I may missing kernel source package, is this the case? 

If it is so, then where can I find kernel source package. it doesn't seem to be on the installtion CD. 

thanks for all you help.  :grin:

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=zodmaner]
If it is so, then where can I find kernel source package. it doesn't seem to be on the installtion CD. 

thanks for all you help.  :grin:[/QUOTE]

sudo apt-get install linux-source-2.6.10

---

### Post by cutOff on 2005-05-04
One question: Have you run a 'configure' with no errors before??

As for kernel sources, on Ubuntu are named linux-source.

$ sudo apt-cache search linux-source

---

### Post by zodmaner on 2005-05-04
>Have you run a 'configure' with no errors before??

the only configure I have run was xserver config though command:

'dpkg -reconfigure xserver-xorg'

and it works fine.

and command : 'sudo apt-cache search linux-source' turn up blank, so this mean I don't have kernel source install right?  ](*,) 

and it seems I cannot use 'sudo apt-get install linux-source-2.6.1.0 either(it fails to find the source), I guess this is because I don't have internet connection in linux yet(I'm writing this using window)

One more question if you may: is there a way to obtain the source the other way?(maybe debian web has it?) and,when I get to source, how do I apt-install it(do I have to burn the source into CD?)

again, thanks for all the help guys  :)

---

### Post by zodmaner on 2005-05-04
[http://ubuntuforums.org/showthread.php?t=31655](http://ubuntuforums.org/showthread.php?t=31655)

lol  :grin: well, I'll try that now and see how it's turn out.

thanks cutOff! (and adajar99 too)

---

### Post by notzac on 2005-05-04
> One more question if you may: is there a way to obtain the source the other way?(maybe debian web has it?) and,when I get to source, how do I apt-install it(do I have to burn the source into CD?)

This *might* be what you're after (I'm guessing a bit):

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34_all.deb)

Download the file, burn it to CD, copy it to your desktop in Ubuntu and install it with the following command:

[INDENT][FONT=Courier New]sudo dpkg -i ~/Desktop/linux-source-2.6.10_2.6.10-34_all.deb[/FONT][/INDENT]

---

### Post by zodmaner on 2005-05-04
Thanks notzac!, I'm downloading the .deb file now, hope this work :smile:

---

### Post by notzac on 2005-05-04
let us know how you go..

---

### Post by zodmaner on 2005-05-04
well... bad news I guess...

I successfully install kernel source (using the link provied here) any try run the 'make' command again, to my horror it display the same error as before :

gcc -O2 -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -DCPU=686 -march=i686 -DMODULE -D__KERNEL__ -DLINUX -I/lib/modules/`uname -r`/build/include -c BlSrv.c -o BlSrv.o
BlSrv.c: In function `BlDatagramSend':
BlSrv.c:250: warning: passing arg 4 of `USBADSL_ProcessMPXFR' from incompatible pointer type
BlSrv.c: In function `USBADSL_ProcessMPXFR':
BlSrv.c:325: error: `USB_QUEUE_BULK' undeclared (first use in this function)
BlSrv.c:325: error: (Each undeclared identifier is reported only once
BlSrv.c:325: error: for each function it appears in.)
BlSrv.c:327: error: too few arguments to function `usb_submit_urb'
BlSrv.c: In function `BlDatagramReceive':
BlSrv.c:404: warning: passing arg 4 of `USBADSL_MPReceivePacket' from incompatible pointer type
make: *** [BlSrv.o] Error 1

 ](*,) 

...well, at least we know it wasn't the kernel source fault, but if so then what is the problem here?

Is it because I'm using AMD64 version of Ubuntu? or is it possible that something is wrong with the makeupfile?

Thanks you all for help guys, I really mean it   :smile: hope I didn't bored you all yet with all these quesntions.

---

### Post by notzac on 2005-05-04
Hate to tell you this, but it refused to compile for me at all. Couldn't figure it out.

The Billion USB modem is Conexant-based, so you could try the normal Conexant drivers for Linux. you'll have to build it from source, patch your Linux kernel and then recompile it. not a great deal of fun.

The other option is to get yourself an ethernet ADSL modem? ;)

---

### Post by zodmaner on 2005-05-04
:smile: Thank you very much for helping notzac, so that means it is mainly the driver problem it self, not the compatibility one right?

Well, anyway it looks like I'd better off with an ethernet modem don't I? oh well...  :roll: at least if I change then I don't have to go though this driver hell agian  \\:D/ 

Say... could you recommended a good ethernet modem for me?, and I have ASUS A8N-SLI Deluxe with built in Lan controller (marvell PCI Gbit LAN), is this compatible with Ubuntu?

And last but not least, thank you all again for helping guys, I really REALLY appreciated it  :grin: (can someone tell me a synonym of a word 'thank you'?, I think I've use this word way too much  ;-) )

Seriously guys, thanks. oh, and Linux community is the best!  :)

---

### Post by notzac on 2005-05-04
Hehe you're welcome.

As far as ethernet modems go - I'm not sure where you are, so I've got no idea what's available (I'm in Australia). That being said, given you've already got a Billion (we've got them here as well); one that is fairly nice for very cheap is the Billion 5102/5102S. Piece of cake to install - it should *just work* where your USB modem *just doesn't*. ;)

[edit: the lan card should (already be) working just fine. it appears to use the sk98lin.ko module, which comes with Ubuntu. go to a shell and type in [FONT=Courier New]ifconfig[/FONT] - is there a section called eth0? ]

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=zodmaner]
Is it because I'm using AMD64 version of Ubuntu?[/QUOTE]

Very possible. As jDong has said before....their is almost no advantage to 64bit Ubuntu unless you need to use a LOT of RAM. x86 burns on those machines...

---

### Post by zodmaner on 2005-05-04
There is another possibility guys, it seems that, although the darn driver won't complies in kernel version 2.6.10, it may be able to in older version (read: 2.4.x.x)

I've not test this yet but one kind soul on linux.thai.net forum told me that he got the thing to complies on his distro which use kernel version 2.4.x.x.

If this is truth, then now I'm face with a choice: use an older kernel, or get a new modem.

hm...  :-| 

PS. Oh, and thanks(again  ;-) ) notzac, I check and it seems my lan card is working just fine(although Ubuntu can't seem to detect DHCP setting for it, but I think that is mainly because I've not connect it yet).

---

