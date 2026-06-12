---
title: "Ubuntu Studio Upgrade from Ubuntu Karmic"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by EnergyEruption on 2010-01-21
Hi everyone, 

       I had v. 9.10 of Ubuntu installed, and tried to upgrade to Ubuntu studio, by typing 
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

in the terminal. When I tried to run the JACK Control Panel, I then noticed that the real time kernel wasn't working, so I typed

uname -a

into the terminal, which came up with

Linux energyeruption-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

which I think means that the real time kernel isn't installed. So, I downloaded the linux-rt_2.6.31.9.10_i386.deb package (the real time kernel installation package), and when I tried to install it, it said that it's already installed!

Any suggestions? 

Thanks guys and girls, and sorry for the length of this.

EnergyEruption

---

### Post by snowpine on 2010-01-21
> **EnergyEruption said:**
> Hi everyone, 

       I had v. 9.10 of Ubuntu installed, and tried to upgrade to Ubuntu studio, by typing 
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

in the terminal. When I tried to run the JACK Control Panel, I then noticed that the real time kernel wasn't working, so I typed

uname -a

into the terminal, which came up with

Linux energyeruption-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

which I think means that the real time kernel isn't installed. So, I downloaded the linux-rt_2.6.31.9.10_i386.deb package (the real time kernel installation package), and when I tried to install it, it said that it's already installed!

Any suggestions? 

Thanks guys and girls, and sorry for the length of this.

EnergyEruption

Reboot and choose the new linux-rt kernel from GRUB.

---

### Post by EnergyEruption on 2010-01-21
Nice one snowpine, that worked perfectly, thanks for that. 

I didn't know I could choose between the 2 kernels. Next time I start the computer, will it be on the real time kernel or the generic one? In other words, do I have to keep choosing the real time kernel, or does grub remember my last choice?

EnergyEruption

---

### Post by snowpine on 2010-01-21
Assuming you're using the new Grub 2, you should be able to figure out how to set the default boot option with these directions:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

