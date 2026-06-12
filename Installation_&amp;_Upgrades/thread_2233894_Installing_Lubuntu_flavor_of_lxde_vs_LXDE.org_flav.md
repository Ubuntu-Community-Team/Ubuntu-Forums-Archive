---
title: "Installing Lubuntu flavor of lxde vs LXDE.org flavor."
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by NuxNik on 2014-07-11
I an am ex-Windows geek (20+ years), with 40+ years in IT.
I am slowly coming over the the LINUX side,
    (And gently pulling my family behind me in the process.)

I am installing a small server, to run my in-house network. 
It will be used for:
- install and play with VM (VirtualBox or XEN)
- directory services (Hesiod ?) 
- mail  server
- cloud server.
- file backup server,
- possibly web server,
- and anything else I can think of.
- also possibly run the above services in a VM 

I  would like to install the Lubuntu graphical front-end. Which I would start when needed and stop the rest of the time.
       (I am NOT a "terminal" purist, so on't even bother going there)

Here is what I have done so far, (but am not married to this approach).
1) installed Ubuntu server 14.04 LTS.
2) Installed LXDE from LXDE.org   --    Clearly I have been spoiled running Lubuntu..

So my questions are
1) How can I import and install the Lubuntu front-end on the server
Alternately
2) Should I install Lubuntu 14.04 and turn it into a server ?
2.1)  What components of Lubuntu 14.04  would be redundant for the above objectives
2.2) What components would need to be modified to 

Also any explanation of why one choice is better than the other would be appreciated.

Thank you.


P.S. if this is the wrong forum for this question please re-direct    TNX.

---

### Post by ibjsb4 on 2014-07-11
There's a 100 different ways to add a gui to a server.  IMO lxde is not a bad way to go.  Just depends on how bare bones you want.

[http://packages.ubuntu.com/trusty/lxde](http://packages.ubuntu.com/trusty/lxde)

If you want to step it up a notch (more bells and whistles) you could install lubuntu core and leave off the recommended packages.
```
sudo apt-get install --no-install-recommends lubuntu-core
```
[http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

I have not used the lxde.org download, can't help you there.

---

### Post by NuxNik on 2014-07-11
Thank you for your response

I will be looking at the differences between
Lubuntu-desktop
lubuntu-core
and the [COLOR=#000000][FONT=Ubuntu Mono]--no-install-recommends

To decide how much I want to install and/or remove..

I may not have been very clear, but the LXDE.org install was "stark". The lubuntu variant is much more vibrant and is already something I'm use to... (Old dog comfort zone)




[/FONT][/COLOR]

---

