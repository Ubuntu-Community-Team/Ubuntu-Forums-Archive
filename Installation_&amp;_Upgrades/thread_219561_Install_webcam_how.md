---
title: "Install webcam how?"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by mock on 2006-07-20
Hi!

I Got a USB webcam (Phillips SPC700NC). i looked at [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)  and according to this it will run on spcaxx/LE drivers.

Correct me if i'm wrong but spca5xx is included in ubuntu, so it should work out of the box.

when i do

lsusb

i get:
Bus 002 Device 002: ID 0471:0328 Philips

(So i know it found it)

i also tryed to
sudo modprobe spca5xx

but to no effect.

When i run camerama it says it cant connect to video device (etc/video0)

Can anyone help me figure out what's wrong.
When i run Ekiga all i get is static from my tvcard (pinnacle pctv) (and that the ony videodevice that seems to be found)

Please, help me with this.

I run a amd64
with the latest kernek
***.26 generic.

/kind regards
Mike

---

### Post by John.Michael.Kane on 2006-07-20
mock are you running the 64bit version of dapper or 32bit?

---

### Post by mock on 2006-07-20
I run the 64bit version (is spca5xx included in the updates or do they need to be rebuilt?)

/Mike

---

### Post by John.Michael.Kane on 2006-07-20
Not sure if they are or not. I would suggest you use the 32bit version of ubuntu to find out if your cam is supported. some drivers are not yet made for 64bit-OS'es.

---

