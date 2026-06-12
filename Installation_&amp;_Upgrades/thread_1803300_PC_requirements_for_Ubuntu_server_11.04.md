---
title: "PC requirements for Ubuntu server 11.04"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by achiel7 on 2011-07-13
Hi guys

I'm using Intel atom 1.8 Ghz, RAM 4GB, but it took 12 hours to install ubuntu server 11.04. Can U guys tell me PC requirements to install it?

thanks

---

### Post by samstreet101 on 2011-07-13
Definitely something wrong there, I've installed 11.04 on a netbook with a 1.6Ghz Atom, 1GB RAM and it took a little over 15 minutes. 

Is anything wrong with the installation? Have you got it up and running yet?

---

### Post by alexan on 2011-07-13
> **achiel7 said:**
> Hi guys

I'm using Intel atom 1.8 Ghz, RAM 4GB, but it took 12 hours to install ubuntu server 11.04. Can U guys tell me PC requirements to install it?

thanks

Slow connection while download the updates? be sure to uncheck the "autodownload" of updates during installation.

---

### Post by samstreet101 on 2011-07-13
Ah sorry, didn't read 'Server' I installed the standard desktop edition. However, I still wouldn't expect it to take 12 hours.

---

### Post by achiel7 on 2011-07-13
i make a booting cd for ubuntu, it took hours just to read from the disc, after the instalation finished, it keep reading usb failed,,so i do re-instalation using usb stick,,the same problem still appears.

---

### Post by samstreet101 on 2011-07-13
sounds like its possibly a hardware problem, though I could be wrong, slightly out of my depth I'm afraid.

---

### Post by westie457 on 2011-07-13
> **achiel7 said:**
> i make a booting cd for ubuntu, it took hours just to read from the disc, after the instalation finished, it keep reading usb failed,,so i do re-instalation using usb stick,,the same problem still appears.

Could be you got a corrupt download. Did you download the iso from here? [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

If you did not I suggest you do so. 

Also you could try this to create the LiveUSB [http://www.howtoforge.com/creating-a-bootable-ubuntu-usb-thumbdrive-from-windows-with-usbuntu-live-creator](http://www.howtoforge.com/creating-a-bootable-ubuntu-usb-thumbdrive-from-windows-with-usbuntu-live-creator)

Or try again using unetbootin available here [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") 

Have just re-read the thread and spotted that you created a LiveCD. Could there you had a bad burn. Try again using the slowest possible speed-settings to eliminate errors in the burn process.

The error about not reading usb could be a different matter. 

Before installing, use the LiveCD/USB in try-out mode first.

In a terminal could you run ```
lspci
```

Copy the output and in a new reply paste between # (code) tags. The little # symbol at the top please.

---

### Post by achiel7 on 2011-07-13
yes, i did download from ubuntu.com and now, it's running properly..but, im curious why it took so long to install, is my pc doesnt support for ubuntu server? or is it possible because it keeps reading usb failed, so it took yearly just to instal?

---

### Post by westie457 on 2011-07-13
> **achiel7 said:**
> yes, i did download from ubuntu.com and now, it's running properly..but, im curious why it took so long to install, is my pc doesnt support for ubuntu server? or is it possible because it keeps reading usb failed, so it took yearly just to instal?

Cannot say for definite what caused your situation. The recommendation generally is to download a Desktop version and create a LiveCD/USB and boot into that to test if a computer and it's hardware is capable of running the operating system.

Generally speaking though transfer speeds from USB are faster than a CD they are still slower than an internal hard drive. What actually caused your install to take so long probably cannot be verified without some detailed problem solving.

If you have any more problems do not hesitate to start a new thread with your question adding details and info to aid the process.

---

### Post by achiel7 on 2011-07-14
1. actually what is your recommendation for PC spec for ubuntu server?
2. im setting up a local network, maybe only for 10 PC, can i use ubuntu desktop?

---

### Post by mastablasta on 2011-07-15
> **achiel7 said:**
> 1. actually what is your recommendation for PC spec for ubuntu server?
2. im setting up a local network, maybe only for 10 PC, can i use ubuntu desktop?
 
 
somethign definatelly went wrong with install. was this an install with default settings or did you put some changes into it (e.g. RAID)? what kind of server is it? data server, web/LAMP server? what is it going to be used for?
 
1. Ubuntu server should be just fine on your specs. for basics it would be goot to have 1Gb ram and some low power consumption cpu such as Atom.
 
2. yes you can. desktop is basicly only GUI interface to server, minus some server specificc packages :-)
 
What i would do in your case is check the USB if all is OK on it and also theck the md5sum of the downloaded iso:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
if you dowload via torrent then this should be done during the download. however if you used normal download then this has to be doen manually after it's finished to check that there are no errors on ISO. otherwise ubuntu installs in 30-45 minues max.
 
EDIT - i forgot to add that for production environment and server (unless necessary) it is better to use LTS editions (current one is Ubuntu 10.04). they are more stable and server edition has 5 years support.

---

### Post by achiel7 on 2011-07-15
im using it for web/lamp server..what your suggestion, ubuntu server or desktop?

---

### Post by mastablasta on 2011-07-15
i would use server.
 
he only thing i can think of is since you are using Atom maybe a different kernel hsould be used. I am not sure hwo is it now, but in 10.04 and 10.10 there was a netbook edition that had some Atom processor optimisation. this was all joined together so it shouldnt' be an issue, but then again....
 
sevrer install should be fast enough. use tasksel to instal LAMP and any admin GUI software if necessary. there is actually a distro based on ubuntu specifically designed for webservers.:
[http://www.zentyal.com/](http://www.zentyal.com/)
 
you can achieve same thing on ubuntu with installing the necessary applications.
 
however i would still suggest you use 10.04 for server. 11.04 is going out of support next october when you will likely have to do an upgrade.

---

### Post by haqking on 2011-07-15
A server is not defined by its hardware but by its services.

The services and their expected load will define the hardware for the server.

Try here [https://help.ubuntu.com/10.04/serverguide/C/index.html]("https://help.ubuntu.com/10.04/")

There is also lots of information here [http://www.ubuntu.com/business/server/overview](http://www.ubuntu.com/business/server/overview)

---

### Post by achiel7 on 2011-07-15
thank you guys for all of the information,,you guys really helpful

---

