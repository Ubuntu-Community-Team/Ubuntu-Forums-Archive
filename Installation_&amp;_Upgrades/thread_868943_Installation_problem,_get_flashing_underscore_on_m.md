---
title: "Installation problem, get flashing underscore on my laptop"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by tamfire on 2008-07-24
Hi, I trying to install ubuntu on my ibm 600e. I can boot fine and i see the menu with 
                       Run ubuntu (no install)
                       Install Ubuntu
                       look for errors on cd
                       test memory

When I install, I get the ubuntu symbal with a bar under it moving. After that my Cd-rom and hard drive running with a flashing underscore on the display.:confused:, Ran it for an hour or 2 now.

Any help

---

### Post by argail1980 on 2008-07-24
hit Ctrl+Alt+F1 or CTRL+ALT+F2. is there a screen coming saying 

'<your computer name> login:'?

If yes, maybe your graphics gard is not poperly recognized. Login with your username and password (there are no *s shown when typing the passowrd)

and enter

```
nano /var/log/Xorg.0.log
```.
search for lines starting with '(EE)', these are errors. post these lines, if any.

---

### Post by PCessna on 2008-07-24
By the looks of your laptop, google right away says this one's around 300-400MHZ, which tells me 128MB ram - 256 MB ram, if you're using Live CD with that much RAM, it won't work. Same thing happened with my ThinkPad T20 with 128MB ram.

---

### Post by PCessna on 2008-07-24
> **PCessna said:**
> By the looks of your laptop, google right away says this one's around 300-400MHZ, which tells me 128MB ram - 256 MB ram, if you're using Live CD with that much RAM, it won't work. Same thing happened with my ThinkPad T20 with 128MB ram.
Try getting alternative CD with text installer. That may work.

---

### Post by tamfire on 2008-07-24
[QUOTE=
Login with your username and password[/QUOTE]

I havent installed it yet,

I hit Control+Alt+f1 and i got...



[  0.00000] acpi: bios age (1999) fails cutoff (2000), cp=force is reuired to enable acpi
Loading, plese wait...


Now what

As you can tell im new to linux :)

---

### Post by tamfire on 2008-07-24
> **PCessna said:**
> By the looks of your laptop, google right away says this one's around 300-400MHZ, which tells me 128MB ram - 256 MB ram, if you're using Live CD with that much RAM, it won't work. Same thing happened with my ThinkPad T20 with 128MB ram.

Not using live disk trying to install to hard disk

---

### Post by tamfire on 2008-07-24
> **PCessna said:**
> Try getting alternative CD with text installer. That may work.

i'll try that later, no rush to fix it, if it comes down to it i'll do it

---

### Post by PCessna on 2008-07-24
Alright, Good luck :)

---

### Post by PCessna on 2008-07-24
> **tamfire said:**
> Not using live disk trying to install to hard disk
I believe the install method is still using the 'Live' interface.

---

### Post by tamfire on 2008-07-24
hold on, i might have figured something out, when i download

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

should i hit "64bit AMD and Intel" I have an Intel Pentium II. when i downloaded this one i hit the top button.

Is this the problem

---

### Post by tamfire on 2008-07-24
> **PCessna said:**
> I believe the install method is still using the 'Live' interface.

It might but i hit the "install Ubuntu" button

---

### Post by argail1980 on 2008-07-24
ok, it's an age problem of the BIOS. try to disable ACPI when booting. I must admit I have no idea yet how. Maybe some of the other guys know. 
I suppose there should be a boot option (noacpi or so) when booting from the install CD.

ACPI is the event control for those i.e. sound volume buttons, laptops have additionally to the keyborad.

---

### Post by PCessna on 2008-07-24
No!, Don't use 64-bit, use the Alternative installer for the Intel 86x or whatever, not 64bit.

---

### Post by tamfire on 2008-07-24
Ok not 64 bit.

Now how to turn ACPI off

---

### Post by tamfire on 2008-07-24
if it's a bios age problem, what if i try to flash it to the latesed version

---

### Post by tamfire on 2008-07-24
Im downloading alternate downlod to try now going to take a while

---

### Post by tamfire on 2008-07-24
Im installing the alternate now, seems to be working, got to installing base system or something. :popcorn: taking a while

---

