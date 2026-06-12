---
title: "Help with Installation"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by denisvj on 2006-07-02
ok here is my problem :

I have 2 sata drives  and yesterday I installed ubuntu 6.06 server and the installation was ok. dual boot : in the first disk is xp and in the second is ubuntu and today I deleted the second hard disk  and begin to install ubuntu desktop instead but know i have a problem , when i try to boot from de cd to install ubuntu   ( ubuntu-6.06-desktop-i386.iso ) and select the option "start or install" ( it does not give me an "install in OEM mode" option ) it tries to boot in a live way i think because it loads drivers and other options and stop with an error that can`t load the graphical interfase... so here i am asking for help :)

:? Thanks for the help..

BTW: spanish here so sorry for the errors

---

### Post by John.Michael.Kane on 2006-07-02
You downloaded the wrong iso for oem installs. you need [**Alternate install CD**]("http://ubuntu.cs.utah.edu/releases/6.06/ubuntu-6.06-alternate-i386.iso") linked to here.

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems; 
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM.

---

### Post by tonyr on 2006-07-02
The release 6.0.6 has three different uinstallation CDs.  The **Desktop CD** is what
used to be called the **LiveCD**, and does exactly wha you saw, boots into a live Ubuntu session from which you can a basic installation.  **The Alternate CD**
uses the old the based interface, and the **Server CD** does, too.  The release
**Server CD** has the 'install OEM option' (and others).  The **Alternate CD**
is for other **special needs** installations.

Get the **Server CD** or **Alternate CD**

---

### Post by denisvj on 2006-07-02
ooppss thanks :) ok here i go again :( 
:oops:

---

### Post by John.Michael.Kane on 2006-07-02
denisvj also please when burning the iso use a slower speed say 8x or 10x this will cut down on you having cd reading issues.

---

### Post by rcarring on 2006-07-02
[QUOTE=SD-Plissken]denisvj also please when burning the iso use a slower speed say 8x or 10x this will cut down on you having cd reading issues.[/QUOTE]

From a hard drive source use 50% of maximum. From a source on a usb 2.0 external drive use 25% of maximum speed. Enable burnproof and check to verify data after burn.

---

### Post by John.Michael.Kane on 2006-07-02
rcarring was there a problem with what i posted as to using a slower speed??

---

### Post by rcarring on 2006-07-02
Not at all, I was figuring that the user might have a very fast cd rom writer and a large cache.

My percentages are based on personal experience. 

If you have a 16x writer then 8x from the hard disk and 4x from the usb hard disk are safe and will give consistently good results.

Likewise a 32x writer should be able to pull through data without a buffer underrun at 16x and 8x respectively.

Other factors can influence a good burn:

location of temp folder used
caching of image
fragmentation of file system on which iso resides
quality of burn program (by that I mean how it handles caching and buffer usage)

(I quoted your post to keep the suggestions together)

---

### Post by John.Michael.Kane on 2006-07-02
rcarring i see where you was going with it now. thanks for clearing it up.

---

