---
title: "Getting Kernel Alive on screen when trying to install"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by garydevitt on 2007-04-23
Hey,

Just got the Feisty Fawn cd and im trying to install it on this machine : 

Dual Core AMD 64 4600+ 2.41ghz
2gb RAM
Nvidia Geforce 7900 GS
500gb sata II hd

When I boot to Cd, it unpacks the data then hits this screen : 

```

Kernel Alive
kernel direct mapping table up to 100000000 @ 8000 - d00

```

Stops at this screen and doesn't go any further

Any ideas?

---

### Post by diegolaz on 2007-04-26
Exactly the same problem. Did you solve it?
Also tried 32bits, and 64bits alternative CD.....both faild (aldo not always with that messege)

System:
AMD X2 5600+ socket AM2 chipset NFORCE 590
ATI 800PRO
500GB SATAII
Viewsonic VX2025wm 20.1 screen  ---> also source of problems I think... problems since ubuntu 6.06

---

### Post by trill on 2007-05-28
BUMP...... I get this too on my ATI x800xl machine. I've tried every disk from 6.06 to 7.04 and the same thing happens everytime.

---

### Post by PizzaWhore on 2007-06-08
I'm receiving the same exact error. I tried both v7.04 32-bit Desktop and v7.04 AMD64 Desktop with no luck. Can we please get some help on this issue?

**MB:** [Gigabyte GA-M59SLI-S5]("http://www.giga-byte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2302&ModelName=GA-M59SLI-S5") (latest Bios: Award F7)
**CPU:** AMD Athlon 64 X2 Dual Core Processor 5200+
**RAM:** 2 GB
**HDD:** 80 GB SATA
**GPU:** NVIDIA GeForce 7600 GT (512 MB)

Thank you!

---

### Post by geedew on 2007-06-09
Ok, I'm getting more and more used to Ubuntu... been using since 6.06...

I did a bit of googling, and while I did not find any issues to correct this out there, I did happen to find out how I could get past this very same issue.

My 7.04 disk was causing this.. so I dropped in my 6.06 32 bit on... and it spit out the error that the IO-acpi timer was not connected.  

In the help of the 7.04 it gave the exameple  acpi=off  as a login option.

1.  put in your CD
2. when you get to the ubuntu install menu, put your menu select over the first item (start/install ubuntu)
3.  hit f6
4. press the 'home' key, you should be able to see a line that you are able to type commands into under the menu.
5. at the begginning of the line, put in acpi=off and make sure there are spaces between it and the others.
6. Load ubuntu and happy landing... Now anyone that can tell my how to get around gigabyte hardware raid 1?

---

### Post by Sconts on 2007-06-11
> **geedew said:**
> Ok, I'm getting more and more used to Ubuntu... been using since 6.06...

I did a bit of googling, and while I did not find any issues to correct this out there, I did happen to find out how I could get past this very same issue.

My 7.04 disk was causing this.. so I dropped in my 6.06 32 bit on... and it spit out the error that the IO-acpi timer was not connected.  

In the help of the 7.04 it gave the exameple  acpi=off  as a login option.

1.  put in your CD
2. when you get to the ubuntu install menu, put your menu select over the first item (start/install ubuntu)
3.  hit f6
4. press the 'home' key, you should be able to see a line that you are able to type commands into under the menu.
5. at the begginning of the line, put in acpi=off and make sure there are spaces between it and the others.
6. Load ubuntu and happy landing... Now anyone that can tell my how to get around gigabyte hardware raid 1?

Thank you so much!!!! I was having the same problem and your solution worked perfectly :)
<3

---

### Post by kryptik on 2007-07-04
> **geedew said:**
> Ok, I'm getting more and more used to Ubuntu... been using since 6.06...

I did a bit of googling, and while I did not find any issues to correct this out there, I did happen to find out how I could get past this very same issue.

My 7.04 disk was causing this.. so I dropped in my 6.06 32 bit on... and it spit out the error that the IO-acpi timer was not connected.  

In the help of the 7.04 it gave the exameple  acpi=off  as a login option.

1.  put in your CD
2. when you get to the ubuntu install menu, put your menu select over the first item (start/install ubuntu)
3.  hit f6
4. press the 'home' key, you should be able to see a line that you are able to type commands into under the menu.
5. at the begginning of the line, put in acpi=off and make sure there are spaces between it and the others.
6. Load ubuntu and happy landing... Now anyone that can tell my how to get around gigabyte hardware raid 1?

Thanks, I have been having this problem, I will give this a shot and see if it works!

---

### Post by jamo88 on 2007-07-31
well if anyone is interested: i could get the live cd to run and get me to the desktop with  apic=off and changing with f4 the resolution to 640x480-16 (at the ubuntu live cd menu) .

I tried this, but i didn't re-install , so i still dont get pass the "kernel alive  and keyboard leds blinking" thing when NOT booting on recovery mode. Many ppl have said that its a video car issue. so ill install the drivers first :P. but that wont happen today i rather have my media playing first :D :D:D

And well  i would really like know if there's no problem with booting on recovery mode and then exiting,  i mean is that just like booting on normal mode? cuz if it is so then i don;t have a problem with doing that every time a boot up linux  :wink:

---

### Post by jamo88 on 2007-07-31
hey  i got playing with the grub loader and found a way to load on normal boot mode :P
so yeah:
```

sudo gedit /bootgrub/menu.lst
```

and edit your default OS entry  removing splash from the kernel  parameters

so it should look like this :

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0136ebb9-b09b-4907-89c1-9ff8cff979ff ro quiet 
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

save and close, thats how i did it and it worked for me

It looks like my ati x800xl card has fglrx drivers installed properly (something i thought to have installed not in the right way but ubuntu knows its a x800xl, so it must be well installed)  but it wouldnt boot on normal mode. But it is because of the splash screen :P (please do correct me if im wrong)

i hope this helps others :D

---

### Post by acidblue on 2007-08-23
> **geedew said:**
> Ok, I'm getting more and more used to Ubuntu... been using since 6.06...

I did a bit of googling, and while I did not find any issues to correct this out there, I did happen to find out how I could get past this very same issue.

My 7.04 disk was causing this.. so I dropped in my 6.06 32 bit on... and it spit out the error that the IO-acpi timer was not connected.  

In the help of the 7.04 it gave the exameple  acpi=off  as a login option.

1.  put in your CD
2. when you get to the ubuntu install menu, put your menu select over the first item (start/install ubuntu)
3.  hit f6
4. press the 'home' key, you should be able to see a line that you are able to type commands into under the menu.
5. at the begginning of the line, put in acpi=off and make sure there are spaces between it and the others.
6. Load ubuntu and happy landing... Now anyone that can tell my how to get around gigabyte hardware raid 1?







Ok I tried that and it still shuts off my monitor.
Can i drop down to a cmd line before booting and try
 'sudo gedit' my grub.conf file ?
Is that possible with a live cd?
 

amd64 3500+
ECS nForce4m-a motherboard
Gforce 8400GS

---

### Post by cj100570 on 2007-09-01
I have the Gigabyte GA-M59SLI-S5 board also and I've found that in order to install with no problems I have to choose safe graphics mode, hit F6 and type in noapic. That forces the video mode into vesa and disables the interrupt controller which seems to cause a kernel panic while booting.

---

