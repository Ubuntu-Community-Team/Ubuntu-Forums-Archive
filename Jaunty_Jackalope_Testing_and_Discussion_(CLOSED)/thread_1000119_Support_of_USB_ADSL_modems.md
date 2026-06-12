---
title: "Support of USB ADSL modems"
date: 2008-12-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Azrael Nightwalker on 2008-12-02
Hi.
I'm wondering about the status of USB (A)DSL modems support in Ubuntu.
There are 2 specs about it:
[https://blueprints.launchpad.net/ubuntu/+spec/usb-adsl-modems](https://blueprints.launchpad.net/ubuntu/+spec/usb-adsl-modems)
[https://blueprints.launchpad.net/ubuntu/+spec/dial-up-support](https://blueprints.launchpad.net/ubuntu/+spec/dial-up-support)
But none of them seems implemented.

I know that NetworkManager 0.7 supports handling DSL connections, but
some modems still may be not supported out of the box due to lack of
firmware.

Personally, I don't have an ADSL modem, but I am still concerned about
it because lots of users use them in my country (Poland) and lots of
them complain about Ubuntu's lack of support for this kind of
hardware.

Here you can find howto's (in Polish) about installation of 3 most
popular modems in the Neostrada TP (most popular DSL in Poland)
service:
[http://www.linux.rk.edu.pl/w/p/neostrada-sagem-fast-800/](http://www.linux.rk.edu.pl/w/p/neostrada-sagem-fast-800/)
[http://www.linux.rk.edu.pl/w/p/neostrada-speedtouch-330/](http://www.linux.rk.edu.pl/w/p/neostrada-speedtouch-330/)
[http://www.linux.rk.edu.pl/w/p/neostrada-zxdsl-852/](http://www.linux.rk.edu.pl/w/p/neostrada-zxdsl-852/)
They can be translated with Google Translate. The most relevant parts
(links, outputs, filenames, device names) are understandable without
translation anyway.

Let me describe briefly the issues with these 3 modems:

The firmware for the Sagem modem can be downloaded from the following site:
[http://eagle-usb.org/ueagle-atm/non-free/](http://eagle-usb.org/ueagle-atm/non-free/)
This is the site of the developers of ueagle-atm driver.
So if they have the right to redistribute it then:
a) Canonical could make a similar agreement with the copyrights holder
to redistribute firmware, or
b) Ubuntu could include a script that downloads this firmware from the
above site, just like the script for the flash plugin.

The firmware for the Speedtouch modem can be downloaded from:
[http://www.linux-usb.org/SpeedTouch/firmware/](http://www.linux-usb.org/SpeedTouch/firmware/)
Here are the links to the firmware, one of them is from the official
site of the modem's manufacturer.
([http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip](http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip))

As for the third modem, ZXDSL 852, there are 2 howtos:
[http://riot777.wordpress.com/2006/09/22/zxdsl-852-i-ubuntu/](http://riot777.wordpress.com/2006/09/22/zxdsl-852-i-ubuntu/)
[http://student.icis.pcz.pl/~89573/modem/](http://student.icis.pcz.pl/~89573/modem/)
Both mention patching kernel sources with 3 lines to add recognising
of this modem, and both link to firmware hosted on someone's site in
the warez/ directory. So I guess Ubuntu won't be able to link to it.
A legitimate source for the firmware should be found for this modem.

Also there is a tool made for Ubuntu that helps users install and
configure these modems: UbuDSL.
[http://ubudsl.com](http://ubudsl.com)
It's made by one Polish programmer, but it is avaliable in English and
other languages.
Unfortunately its hacky design and GUI written without regard to any
(Gnome's/KDE's) Human Interface Guidelines won't allow it to be
included in Ubuntu. I tried to encourage the author to collaborate
with Ubuntu devs on integrating UbuDSL's features in Ubuntu in a
proper way but he refused to do it.

Something has to be done for Ubuntu to properly support such modems.
If you require any more information about these issues feel free to
ask me here on the list.

Also see the following links:
[http://brainstorm.ubuntu.com/idea/3853/](http://brainstorm.ubuntu.com/idea/3853/)
[https://help.ubuntu.com/8.10/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/8.10/internet/C/modems-adsl-usb.html)

I wrote about it also to the ubuntu-devel-discuss mailing list. I hope that Ubuntu devs won't forget about users of USB DSL modems this time.

---

