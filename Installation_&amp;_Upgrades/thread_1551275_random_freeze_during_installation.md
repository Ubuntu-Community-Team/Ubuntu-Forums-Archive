---
title: "random freeze during installation"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by akshatverma73 on 2010-08-12
i'm using  HP dv6 pavilion 2164tx 
my  system configs are: 
processor :i7 720 Qm 1.6ghz
graphics card:nvidia gt230m 1gb
hardisk:500gb

i already have running window7 home premium version,i'm plannin to install ubuntu though dual boot via a usb.

i downloaded the ubuntu-10-04 desktop i368.iso,used universal usb installer to make my usb bootable with the iso.
when i boot my laptop from the usb,the initial screen comes where its asks me to run ubuntu or install it on  a hard disk,when i choose the install option there is this initial booting process but it freezes at random positions(i tried installin it again again)
there is a blinking underscore at the end and it doesn't proceed any further for a looooong time....
 i desperately need ubuntu ,Please help me out guys...........

---

### Post by akshatverma73 on 2010-08-12
here are some examples.....

---

### Post by mörgæs on 2010-08-12
Can you run a live Ubuntu from the USB stick without installing? 

Have you tried Ubuntu 9.10? 
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by akshatverma73 on 2010-08-12
> **mörgæs said:**
> Can you run a live Ubuntu from the USB stick without installing? 

Have you tried Ubuntu 9.10? 
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)



nope the live ubuntu behaves the same way........
i'll try 9.10 though.....

---

### Post by akshatverma73 on 2010-08-12
there are some
 more observations,
1.it detects my video as vga instead of the dedicated nvidia card,are there any compatibility issues?
2.it usually gets stuck at irq 16.

---

### Post by mörgæs on 2010-08-12
The screen shots show a USB hub, which can sometimes make trouble. Try to remove as much gear as possible before booting.

---

### Post by akshatverma73 on 2010-08-13
well i burned a cd from the iso image.
now when i boot from the cd ,i select the language ,then when i press enter on selecting the option of either run ubuntu directly or install ubuntu,the screen goes blank with a blinking cursor......

---

### Post by mörgæs on 2010-08-13
Sometimes I have a hard time understand what your posts are about. Is #7 for 9.10 or 10.04? 

Have you tried other Linux distros?

---

### Post by akshatverma73 on 2010-08-13
> **mörgæs said:**
> Sometimes I have a hard time understand what your posts are about. Is #7 for 9.10 or 10.04? 

Have you tried other Linux distros?


i'm still using 10.04.
well somehow i managed to run ubuntu from the cd,now installing it on to the hard drive....
thnx a lot for ur help :)

---

### Post by akshatverma73 on 2010-08-14
i've successfully installed ubuntu on my paltop by using a prefix "acpi=off"
now when boot it,
1.) how to make acpi=off permanent on with  the boot menu
2.) my wireless connection isn't working....can u pls help me make it work?

---

### Post by mörgæs on 2010-08-14
1) I have not tried myself, but there should be plenty of advice in these fora regarding this question. Try searching for boot parameters, grub2, startupmanager or the like. 

2) Please post the output from ```
hwinfo --netcard
```


By the way, have you applied all updates using a wired connection?

---

