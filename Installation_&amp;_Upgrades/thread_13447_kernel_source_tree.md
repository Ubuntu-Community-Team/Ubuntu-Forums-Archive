---
title: "kernel source tree"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by DaveM on 2005-01-31
Hey All,
I Have just installed ubuntu to my computer and its working nice, but i'm having troble installing my modem i'm using a netodragon and i downloaded the drivers in the readme it says you should have the kernel source tree installed there is some files in /lib/modules/<kernel ver> but their is no /build subdir so make install stops.   I looked in the package manager but could not find any thing to install that, where can i download the source or can i install it from the disk . 

Thanks for any help.
David Morrisroe.

---

### Post by az on 2005-01-31
sudo apt-get install linux-headers-2.6-386

symlink /usr/src/linux-headers-(*whatever version you are using..) to /lib/modules/(whatever version)/build

What driver are you given?

---

### Post by DaveM on 2005-02-01
> sudo apt-get install linux-headers-2.6-386 
I Will try that,  but will it work without a net connection?

I Just downloaded the driver from their web page it comes i source so i have to build it.

Thanks for your help 8-) 

David Morrisroe

---

### Post by az on 2005-02-01
Linux headers are on the cd.

Make sure that their source is compatible with a 2.6 kernel.  What is the name of the file?

---

### Post by DaveM on 2005-02-01
Thanks for all your  help i got the code compiled and it seems to be working I am Having problems getting the diler to work i'm using wvdial  i used the wvdialconf to make a conf file for it and entered the phone number and password  and the line

Carrier Check = no  (as in the read me for the modem)
but it still gives me the error 
ATDT1890924042
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT1890924042
--> Waiting for carrier.
ATDT1890924042
NO CARRIER
ERROR

it just keeps doing that till i ctrl +C the console
the modem uses a pseudo-terminal

the driver file name is "slmodem-2.9.10_netodragon.tar" which I got from their website 

it also says you can use ALSA mode i'll look into that in the morning 
I Just want to get my modem working so i can dump window$ and live happly ever  after.

thanks for all the help much much appreched 

David Morrisroe

---

