---
title: "3 minutes after installation - I'm hooked"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by lndc on 2005-08-30
I cannot believe how easy installing the live version of Ubuntu is!. Everything works perfectly and it even installed my ADSL broadband wireless modem. 
I have one query, and perhaps someone can help.
UBUNTU works with my computer which is 'wired' to my modem, but it cannot connect to my kids computer which has a wireless Lynksys usb modem.
Anyone had this problem? 
oh and by the way I've never understood programming or computers to any degree at all so if there is a simple way to do this then thats the one for me.

Thanks

---

### Post by numberexhaust on 2005-08-30
Wireless is probably the aspect of linux in general that will give you the most trouble.  Usually linksys cards are fairly compatible, but they will often give you trobule as well, depending on the model.

You see, in linux, the model and even where it was made (Korea vs China) could govern whether it works right out of the box or not.  Chances are, with a little manipulation, we could get the card to work.

When searching these forums, there are a couple of things you should know about wireless cards.

1) ndiswrapper - a tool used to "wrap" windows drivers around so that they are compatible with linux.  a fairly decent took (i use it myself) and is compatible with a lot of cards, but there are some stability issues, i believe.

2) madwifi - some drivers that are in their very early development, but are good if you have the right card.  Chances are, since you have a Linksys card, that madwifi will not work with it (I don't have much experience with it, so I wouldn't be the one to say for sure).  Also, compiling and using madwifi would take a fair amount of general knowledge of linux, a prerequisite which I myself may not even fullfill.

To start out, find out the exact model of your wireless card.  If you don't have the box or don't know, post whatever you can about it here.

Also, for now, open a terminal (Applications - System Tools - Terminal) and post the output of the following command, word for word.

```
sudo ifconfig
``` 

We'll see where we can go from there.

---

### Post by lndc on 2005-08-30
Thanks for the post. the model is (Linksys wireless G 2.4GHZ USB network adapter model number WUSB54G) or see below

[http://www.amazon.com/exec/obidos/tg/detail/-/B00009X6PH/002-6190627-0488039?v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B00009X6PH/002-6190627-0488039?v=glance)

I posted the instruction in (Applications - System Tools - Terminal) and got the following message.

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:2C:26:E1
          inet6 addr: fe80::20a:e6ff:fe2c:26e1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1334 (1.3 KiB)
          Interrupt:11 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:96950 (94.6 KiB)  TX bytes:96950 (94.6 KiB)

Hope this makes sense 

Thanks

---

### Post by numberexhaust on 2005-08-30
Assuming that you booted with the hardware plugged in at least a couple of times, I think it's safe to say the driver isn't installed.  I'm going to lead you down the path of ndiswrapper, which involves a lot of steps, so I won't come out and explain everything, but I will guide you with some good links.

You will need to download a few things through the Synaptic Package Manager for this process, and in order to set that up follow "How do I add extra repositories" in this guide:

[www.ubuntuguide.org](www.ubuntuguide.org)

btw, anything in black there, and almost all the code (probably all) that I give you is going to have to be entered in the terminal that I showed you earlier.

Some things in that guide are out-dated, but this will work (100% sure) if you follow it exactly.

Secondly, you need to get the package "wireless-tools".  Go into System-Administration-Synaptic Package Manager and click on search.  Chances are, the package is already installed.  If it isn't, mark it and hit apply.

Continue on to download and install ndiswrapper.  Do this by going back into the package manager and search "ndiswrapper".  The package is called ndiswrapper-utils, i believe, and there is another one called ndiswrapper-source.  you only need the utils one.  Mark it for installation and hit apply.

Now it's time to download the drivers.  If you have a CD that came with your modem, it would be easiest to use.  Go into the folder called Driver, and keep following the folder structure until you come to an "something.inf" file.  If there is a split, it is probably because of the verison of the modem you have.  Make your best judgement, it may or may not matter.

If you don't have the CD, you have to download the driver from the Linksys website and extract it IN WINDOWS, and then somehow bring the "Driver" folder over to linux.

Once you have ndiswrapper installed and the driver in your possession, post again and I will guide you through the rest.  Also, check to make sure that there is no "Wireless Connection" in System-Adminstration-Networking, because if there is it would make it a lot simpler. :-#

---

### Post by lndc on 2005-09-02
Sorry for the delay. I am progressing through your instructions by running an ethernet cable to my 'wireless' computer to download the nescessary drivers.
When i complete the instructions you sent  will contact you again.

thanks

---

