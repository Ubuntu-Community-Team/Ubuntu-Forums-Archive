---
title: "Installed Ubuntu no ADSL"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by harty on 2005-06-26
I have a two pc network ,this one(Host) is an amd750, 384Ram 30 + 80 hd running on xp pro  &  ubuntu 5.04 .this will only access the net while it is on xp pro,when it boots up on Ubuntu it does not detect the modem,it is a sagem F@ST 800 PE,external on the usb port. My isp is Tiscali. 

The other pc is an amd 950 ,256 Ram with 13gb hd,that was on xp pro but I scrubbed it when I loaded Ubuntu.This one detected the network no problems and it was on the web & updated as soon as I started it.(both have ethernet cards)

What is the easiest way to configure the internet connection.
I have never had to write commands before and I am not sure where I write them or how to write them.
Terminal? root teminal?
Any help would be greatfully appreciated but please keep it as simple as possible
this is my first attempt at linux ,please be patient.
                                                                     harty(newbie) :?

---

### Post by podrik0 on 2005-06-26
In the same boat as you mate Sagem F@st 800 + Tiscali!

Noone seems to reply to my topics, so am confused, its the only thing stopping me from getting rid of windows for life

I am a linux noob so need alot of help with the complex commands etc  :???:

---

### Post by az on 2005-06-26
Usb adsl sucks.

I think these packages are what you need:

[http://packages.ubuntu.com/hoary/net/eagle-usb-modules-source](http://packages.ubuntu.com/hoary/net/eagle-usb-modules-source)
[http://packages.ubuntu.com/hoary/net/eagle-usb-data](http://packages.ubuntu.com/hoary/net/eagle-usb-data)
[http://packages.ubuntu.com/hoary/net/eagle-usb-utils](http://packages.ubuntu.com/hoary/net/eagle-usb-utils)

Quote:
"You'll need a kernel module to be able to use these tools. Such a kernel module can be semi-automatically compiled and installed if you install the eagle-usb-modules-source package and follow the instructions in /usr/share/doc/eagle-usb-utils/README.Debian."


You will need the linux-headers as well as build-essential.

I am shooting in the dark.  I do not have your hardware.  Let me know how it goes!

Perhaps this driver should be included in the next Ubuntu kernel.  If it works, please answer back so that I can help you either file a bug report or ask on the devel mailing list...

If you do not do it, who will?

---

### Post by az on 2005-06-26
What do I know!?
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=eagle-usb.ko&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=eagle-usb.ko&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386)

It is already in the kernel.  I assume you just need the data and the utils, then.....

Let me know..

---

### Post by harty on 2005-06-27
Thanks for the quick reply azz
,you may be correct in "saying usb adsl sucks"I have had the thought that if my modem was an internal pci slotted type,the damn thing would have configured without a problem.
The way things are I work nights and won't get the time to get this sorted until the weekend ,so don't think I don't appreciate the info you have given,I most certainly do.

podrick stay with it mate it will be worth the hassle.
If you get this sorted before I have(or anyone for that matter)please post how you acheived it.
       Thanks again azz.
I will post back near the weekend,maybe before if my wife will tolerate it mmmmmmmm.
                harty.

---

### Post by podrik0 on 2005-06-30
Been sorted for days mate! lol

Load kynaptic (Package Manager) >> Enter your password >> Drop-Down to 'Status' >> Select Not Installed >> Scroll to 'linux-headers-(YOUR KERNEL VERSION) >> Select to Install this >> Apply the changes!

Then 

Download this:
[http://baud123.free.fr/eagle-usb/eagle-usb-2.3/eagle-usb-2.3.2.tar.bz2](http://baud123.free.fr/eagle-usb/eagle-usb-2.3/eagle-usb-2.3.2.tar.bz2)

extract to say /home/user/eagle-usb-2.3
cd /home/user/eagle-usb-2.3
sudo apt-get install build-essential
./configure
make
make install
eagleconfig (configs your user and pass and stuff - say NO to ISP encryption)
then type startadsl to connect or stopadsl to disconnect
eaglestat is to check the status - operational etc etc
Hope it works mate!

---

### Post by harty on 2005-07-02
Thanks for that info Podrick,glad to hear you have yours sorted.
This thing is giving me a headache................when I try and follow your instruction,I click on the synaptic package manager and nothing happens?
aswell as that the resolution is too big and it won't let me change it.
      It's doing my head in,might try a fresh install see if it gets any better?
                                                                                                              harty :mad:

---

