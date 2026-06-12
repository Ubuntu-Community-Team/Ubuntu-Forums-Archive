---
title: "Scangearmp for Canon mg6320 Not Working in Linux Mint 18.1"
date: 2017-05-23
forum: MINT
---

### Post by Atulo on 2017-05-23
Hello,

I'm having trouble running scangearmp on Linux Mint 18.1   I'm using a Canon mg6320 and would like to get the scanner going.  My understanding is that I have to use the scangearmp program provided by Canon.

I've tried installing scangear ([http://support-au.canon.com.au/conte...100470802.html]("http://support-au.canon.com.au/contents/AU/EN/0100470802.html")) and scangear 2 ([http://www.canon.ca/inetCA/en/serviceDetail?m=load&directLink=Y&mid=0515C002&type=D&opt=1](http://www.canon.ca/inetCA/en/serviceDetail?m=load&directLink=Y&mid=0515C002&type=D&opt=1)).  I used alien to covert the tar to a deb and installed.  

When I type 'scangearmp' or 'scangearmp2' into the terminal, it says 'command not found'.  Was hoping to check and see if anyone might have any ideas on how to get scangear working?  Thank you for your time and advice.

~AB

---

### Post by pdc on 2017-05-24
sorry to hear of your troubles; 

so alien was to convert between rpm packages and debian I understood; so I wonder if it would carry out its job if you got it to work on a tar package; you could check what was installed with the command ```
dpkg -l scangear*
```  ... you need to COPY that, and paste it into a terminal; you could tell us what the result is; if not much show, you could follow the advice below and see if it works any better

_________

for quite a few years now, Canon have supplied drivers in 3 formats for linux users: rpm packages; debian packages and source code. Mint uses Ubuntu; Ubuntu uses Debian so debian packages are used; so just use a debian package from canon

for the MG6300 series drivers, I would start at the Canon Asia website [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) and that takes me to here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100470702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100470702.html) and you get [COLOR="#0000FF"]scangearmp-mg6300series-2.00-1-deb.tar.gz[/COLOR]

......... so that is a debian package ....... compressed into a tar.gz format; it is a 5yr old driver; if you were to click to download and select SAVE, it should end up in your Downloads folder; commands to install; one line at a time and hit ENTER after each paste would be:
```
cd Downloads
```
```
tar -zxvf scangearmp-mg6300series-2.00-1-deb.tar.gz
```
```
cd scangearmp-mg6300series-2.00-1-deb
```
```
./install.sh
```

and then to run it the command would ```
scangearmp
``` and you could tell us which desktop of Mint you are using; so we can tell you about setting up a launcher; Mint has its own forums too [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

______________________
Incidentally, the open-source sane says it has full support for your MG6300 series device ..... if you type ```
lsusb
``` in a terminal, it should give you ```
04a9:1765
``` [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) so if you install xsane ```
sudo apt install xsane
```, it is a sophisticated front-end for sane ..... and it *should* ....... find your MG if you so wish to use another programme

---

### Post by Atulo on 2017-05-25
Hi Pdc,

Thanks for your advice.

- this is the result I got from the dpkg -l command...

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  scangearmp-sou 2.00-2       all          Converted tgz package
ii  scangearmp2    3.20-2       all          Converted tgz package

-thanks for those instructions on installing the .deb.  That worked like a charm and now I can run scangearmp.  
--In the hopes of learning a bit more, I was wondering if you might happen to have an idea why the converted packages didn't run?  I'm running Linux Mint 18.1 Cinnamon.  The scangear tarball from Canon Australia worked on another computer running Ubuntu Mate.

-Also tried xsane, but got an error when it tried to connect to the MG-6320.

Much appreciation again for your help.  Glad to have this up and running.

~AB

---

### Post by pdc on 2017-05-25
glad to hear it is all working 

> I was wondering if you might happen to have an idea why the converted packages didn't run?   ......... perhaps you run the command ```
dpkg -l scangear*
``` again and we see how many versions of scangear you have installed now 

.... by the way, as you own the thread, you can go to thread tools and edit the title to say SOLVED:

---

### Post by QIII on 2017-05-25
Moved to MINT.

---

### Post by pdc on 2017-05-25
thanks; very organised of you; I do hope Atulo can now find it here on the Mint forum!!

The debian packages from canon seem to work for all systems that need debian packages

---

### Post by Atulo on 2017-05-26
> again and we see how many versions of scangear you have installed now

Thank you for the advice Pdc,

I ran the 'dpkg' command, and this is what I got...

||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  scangearmp-com 2.00-1       amd64        ScanGear MP for Linux.
ii  scangearmp-mg6 2.00-1       amd64        ScanGear MP for Linux.
ii  scangearmp-sou 2.00-2       all          Converted tgz package
ii  scangearmp2    3.20-2       all          Converted tgz package

---

