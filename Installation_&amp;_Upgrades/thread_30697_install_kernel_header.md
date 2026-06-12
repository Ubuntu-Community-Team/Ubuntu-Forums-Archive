---
title: "install kernel header"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by pdc on 2005-04-29
Hi; I'm new to linux; I have installed 5.04 Ubuntu from the March 2005 Linux magazine DVD, and would like to get a HAM modem working; all I need is to install the kernel source header for 2.6.10-2-k7

I have tried to follow various leads; not successfully;

(as I need the header to get a modem working, I cannot obviously use apt get-install kernel-header..)

*I have access to a modem on another computer: so can download .tgz etc onto that ..*

I would be very grateful for instructions as to how to get the kernel source header detailed above;
am I correct that they should be installed into /usr/src? 
If the package I am pointed to does not automatically install the kernel source header into usr/src/, I would be equally grateful for instructions on how to install?

many thanks

---

### Post by az on 2005-04-29
"as I need the header to get a modem working, I cannot obviously use apt get-install kernel-header"

Although that dvd was about two-and-a-half months premature  - (YOU DO NOT HAVE ANYTHING CLOSE TO THE FINAL VERSION OF HOARY!) yes, you should have the appropriate linux-headers package on your disc.

sudo apt-get install linux-headers-2.6.10(whatever version)

---

### Post by pdc on 2005-04-29
as a new user to linux, I would be very grateful for detailed instructions as to which directory of the DVD would contain the kernel source headers;

thanks also for the advice on using sudo get-install ........ but .........

*I want to get a HAM modem working on Ubuntu*; and for that, I need kernel source headers;

I have access to a modem on another computer; but *apt-get-install on that computer* is NOT the one with Ubuntu;

so I would be very grateful for pointers for downloading the kernel source headers I need; to then move (by USB or CD) to the Ubuntu computer;

many thanks

---

### Post by nad on 2005-04-29
What azz is saying is that the package that you need is on the dvd. Using the apt-get command or the synaptic package manager in Computer -> System Configuration will allow you to install the package without any other intervention from you. Well, you do need to configure either app to let it know that the package is available on a disk. The Linux mag is very good at describing how to do this. You just need to add a line to the file /etc/apt/sources.list to describe the location to the program.

These instructions are a little simplified. Please post back after you have checked out the stuff above. We will continue to help you.

---

### Post by pdc on 2005-04-30
thanks for this very helpful advice; I opened up Synaptic Package Manager, with the DVD in the drive, and found two kernel packages: what was called kernel-package and kernel-wedge; I installed both;

and re-tried to install the modem driver: after "make clean" I ran "make 536" and it said:

module precompile check
current running kernel is: 2.6.10-2-k7
/lib/modules ...     autoconf.h does not exist
please install kernel source
make *** [check] Error 1

would be very grateful for further advice on how to proceed please;
thanks very much for prior advice on Synaptic: very useful for much else;

you also gave advice on the etc/apt/sources.list file

I successfully opened that, and read it but would need detailed advice if it also needs editing; I can see it says to "uncomment" various lines to activate them

---

### Post by az on 2005-04-30
You need linux-headers-(yourkernelversion)

Look in synaptic.  Do a search for linux-headers.

---

### Post by pdc on 2005-04-30
thanks very much for continued guidance;
I opened Synaptic; found linux-headers-686 and installed that;
when I re-ran the intel driver programme; it ran make clean successfully; but when I again typed "make 536" it repeated the same message as before: 
[I]module precompile check
current running kernel is: 2.6.10-2-k7
/lib/modules ... autoconf.h does not exist
please install kernel source
make *** [check] Error 1[/I]
I opened Synaptic again; and note "linux-source-2.6.10"; as it is a new system, I took the liberty of asking Synaptic to install it, but "make 536" still says to install kernel source: I sense I may have to type "make config" somewhere along the lines; BUT I DO NOT KNOW; and would be grateful for continued advice;

many thanks

---

### Post by az on 2005-05-01
"current running kernel is: 2.6.10-2-k7"

That means that you need to use linux-headers-2.6.10-2-k7

You do not have an official dvd of Hoary.... Look again to see if it is there.....

---

### Post by pdc on 2005-05-01
thank you very much: the DVD did indeed have the linux-headers-2.6.10-2-k7;
Synaptic installed them, and I successfully completed the "make clean" and now successfully the "make 536" instruction; thanks for advice on installing correct headers;

(all this is to attempt create a dev/modem file apparently, for an Intel HAM modem;)

on the "make install" command, it aborted with the message:

[I]running kernel 2.6.10-2-k7
installing ham registry, used for persistant storage
installing Intel536 driver
unknown distribution, no boot scripts installed
make: *** [install] Error 1[/I]

any further advice on trying to proceed would be gratefully received;

many thanks

---

### Post by pdc on 2005-05-01
you pointed out to me that I did not have the final release of 5.04; (I see the DVD version is described as "Development Edition"; I have emailed Canonical to post me the correct CDs for 5.04; thinking ahead to their arrival; can I upgrade from the version I have installed; or would I need to reinstall; grateful for advice on how to upgrade, if that is feasible ..

---

### Post by nad on 2005-05-01
It appears that your module may have installed. No scripts were installed to automatically start the driver up, but you may not need anything special.

Please issue the command: modprobe --show-depends Intel536  as this seems to be the name of the driver. If the output is a list of ...ko files. You are all set. The output will be an error otherwise. Issue modprobe again without --show-depends to install it. Add the module name to the list in the file etc/modules and it will be automatically included at startup.

As far as upgrading, it can be done automatically once you are inline.

---

