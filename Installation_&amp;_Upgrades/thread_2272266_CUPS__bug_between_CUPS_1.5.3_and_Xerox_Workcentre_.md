---
title: "CUPS : bug between CUPS 1.5.3 and Xerox Workcentre 6015 Driver [solved]"
date: 2015-04-05
forum: Installation &amp; Upgrades
---

### Post by Sendscan on 2015-04-05
Hello everyone,

I am a Ubuntu 12.04 distribution. I have a problem with my Xerox Printer (WorkCentre 6015) and Cups 1.5.3. The colours are not the right one (for ex green on the original document becomes red once printed).

I sent a mail to Xerox and they confirmed me this bug on ubuntu 12.04 (with cups 1.5.3) and ubuntu 12.10 (cups 1.6.1) [http://www.cups.org/str.php?L4186](http://www.cups.org/str.php?L4186) . They told me there is no bug on :
  [COLOR=#1F497D]
- Ubuntu 10.04 (i386) - CUPS 1.4.3[/COLOR]
  [COLOR=#1F497D]- Ubuntu 11.04 (i386) - CUPS 1.4.6[/COLOR]
  [COLOR=#1F497D]- Ubuntu 11.10 (i386) - CUPS 1.5.0[/COLOR]


They tell me the problem comes from the pdf filters

My question is : what can I do to solve this problem ? I tried to uninstall Cups 1.5.3 and install 1.4.3 but it put a big mess in my distribution (But I'm not a specialist of Ubuntu at all / in the end I had to reinstall the system).

I really need your help !

Thanks a lot in advance for your answers !

CD

---

### Post by bapoumba on 2015-04-05
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424)
Seems to be fixed on 13.10, so may be will be working if you upgrade to 14.04 ?

Installing packages that are not for your distribution can indeed create havoc on your system ;)

---

### Post by Sendscan on 2015-04-05
Hello Bapoumba and thanks for your quick answer.
I am using 12.04 LTS because the following versions (13.04 and next) create bugs on my computer which is crrashing. I didn't find any solution to solve this problem.
I found a solution to my problem with cups on the french ubuntu forum. I post the solution for the one who have the same problem. The solution was sent by Emeth

> Emeth wrote :[INDENT]type : wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

Unpack:
    $ tar zxf foo2zjs.tar.gz
    $ cd foo2zjs
    $ make
    $ sudo make install

Then you have to install the printer

$ system-config-printer

during installation, ubuntu will take the default driver. This is what must be corrected. We must go back in the printer properties to change the manufacturer and indicate the new .ppd contained in the unzipped folder. By default monochrome option enabled, simply choose "color". The print is then working ...


[/INDENT]
 

I hope this will be helpful for other ubunteros.

---

### Post by bapoumba on 2015-04-06
Good :)
Which bugs ? Have you posted about them ? Would lighter 14.04 versions (lubuntu or xubuntu) work ?
Please mark your thread as solved (under Thread Tools), thanks !

---

### Post by Sendscan on 2015-04-15
Hello Bapoumba,

I already reported the bug and asked for a solution on Ubuntu forums. To tell it quick, the computer and Ubuntu work well together but after some time, the screen is freezing and there's nothing else to do other than pressing the on/off button on the computer to restart.
Cheers !

CD

---

### Post by bapoumba on 2015-04-15
For that issue, you should start a new thread, providing info about your video card and the drivers you use.

---

