---
title: "this appear in menu (at PC On/Start-Up) of what OS to boot automatically"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by lse123 on 2011-12-10
AFTER INSTALL Ubuntu, this appear in menu (at PC On/Start-Up) of what OS to boot automatically?

---

### Post by critin on 2011-12-10
Hello, lse123

Can you explain more on what problems you are having please?

---

### Post by MAFoElffen on 2011-12-10
+1

The title and the description in the first post:
> **lse123 said:**
> AFTER INSTALL Ubuntu, this appear in menu (at PC On/Start-Up) of what OS to boot automatically?
Does not describe "what" is displayed in "what" menu.

Please expand on --> > this appear in menu
Or if there is any problem.

---

### Post by lse123 on 2011-12-11
> **MAFoElffen said:**
> +1

The title and the description in the first post:

Does not describe "what" is displayed in "what" menu.

Please expand on --> 
Or if there is any problem.

I mean do appear the choice to boot from the NEW INSTALLED OS along built in OS? Either 2nd installed OS or 3rd OS and so on system detect it?

---

### Post by MAFoElffen on 2011-12-12
> **lse123 said:**
> I mean do appear the choice to boot from the NEW INSTALLED OS along built in OS? Either 2nd installed OS or 3rd OS and so on system detect it?
Sorry, I'm still trying to understand what you are saying. I'm thinking that you mean that you have 3 OS'es installed(?) and that your newly installed OS is not showing in your grub boot menu?

I'm also suspecting that English is not your primary language. I'm having trouble understanding what you are saying... As you may have trouble understanding any instructions I might have for you. Once I figure out what the problem is that you are asking, I fear that my instructions might loss something in a translation if your computer is set to your local language.... There are local language support resources that may be easier for you with this:
[http://www.ubuntu.com/support/community/locallanguage](http://www.ubuntu.com/support/community/locallanguage)

Look at the bottom half of that page for that.  Tell me if those might be easier to use for you... or if you want to continue this here.

---

### Post by lse123 on 2011-12-12
A PC to create boot menu (HDD) SEE all HDD PARTITIONS that are bootable from? So for any partition windows or linux appears one or two choices in boot menu...?

In a Netbook windows 7, may installed another OS (From usb stick since no cd drive?) like ubuntu 10.04 client?

---

### Post by MAFoElffen on 2011-12-12
> **lse123 said:**
> A PC to create boot menu (HDD) SEE all HDD PARTITIONS that are bootable from? So for any partition windows or linux appears one or two choices in boot menu...?

In a Netbook windows 7, may installed another OS (From usb stick since no cd drive?) like ubuntu 10.04 client?
The grub menu shows ubunutu (which drive /partition, ex: sda1), other distro's, then Windows and if there is a Windows recovery partition. Each Linux instance has a line below it to start in recovery mode. So yes on #1.

Yes, you can install 11.10 from USB like 10.04.

---

### Post by lse123 on 2011-12-12
lightweight atom processor netbook PCs can accept second even 3rd OS like ubuntu 10.04 and open Solaris, without problems?

grub menu what does see to create itself? boot able partitions?

---

### Post by MAFoElffen on 2011-12-12
> **lse123 said:**
> lightweight atom processor netbook PCs can accept second even 3rd OS like ubuntu 10.04 and open Solaris, without problems?

grub menu what does see to create itself? boot able partitions?
Question 1- I'm not familiar with the Atom processor.  I know Windows and Ubuntu run on it.  And I know Grub runs on it....

Question #2. During update-grub, os_prober probes all partitions of all drives connected to that device and looks for a recognised OS.  There is only so many OS'es in it's list. Grub2 seems to find a lot of OS'es.  

Having said that, I know personally that Solaris, OpenSolaris and OpenIndiana are not found by the Grub2 OS_Prober.  For me, I had to "Make" those entries manually in the /etc/grub.d/40_custom file. I know on some other distro's I have installed (they were not mainline of well known) they still showed up, but as "Unknown Linux"... I guess there is enough out there that they just can't cover them all.

---

