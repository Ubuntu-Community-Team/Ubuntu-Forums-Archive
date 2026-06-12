---
title: "Exhausted and Confused"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Thalaen on 2007-11-28
Alright.. so, I had a copy of Fedora 8.0 laying around that I planned on using for my first Linux installation once I patched together a unit to put it on, but a friend of mine told me I should try Xubuntu instead. Turns out, he was right.

I finally finished the unit last night, installed Fedora, and the Kernel refused to start for some unknown reason - it kept erroring out, saying that something was killing it. So, I formatted the drive, (yet couldn't get rid of the grub boot manager for some reason). I fought with it until 3am and then managed to install Xubuntu 7.10; I left the installation going while I got some sleep, and it had completed when I woke up.

So, now I decided to load it up and get my first look at Linux, right? Well... it goes through grub, and then it goes through the Xubuntu loading screen all the way - and then goes to a blank, black screen. No interface. No prompt. No response.

What am I doing wrong? I'm sure I haven't given you all the information that you need to help, but just tell me what you need to know to be able to help me; I truly am confused by this.

---

### Post by PmDematagoda on 2007-11-28
Could you post the specifications of your PC.

---

### Post by Thalaen on 2007-11-28
Alright,

like I said, it's one that I patched together: Athlon 64 3200+, 512 MB DDR, 80 GB HDD (IDE), Chaintech VNF3-250 motherboard (nVidia nForce2 chipset, no onboard video), GeForce3 6300gt graphics card.

Anything else you need?

---

### Post by Znort_Ubern00b on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=625405]("http://ubuntuforums.org/showthread.php?t=625405")

Try that link seems guy had similar problems and sorted...

---

### Post by Thalaen on 2007-11-28
Thanks Znort; I ran through the same configuration process as the guy you linked me too... hopefully this works. I'll be back here if it doesn't. ^.^

---

### Post by Thalaen on 2007-11-28
Still no dice.. I'll play around with that configuration utility, though - see if I can't get it to work.

---

### Post by ericartman on 2007-11-28
OK in my experience I get this result with the 64 bit Ubuntu system. Are you trying to use 64 bit? If so I recommend using the 32 bit, it's always been a winner for me. I know some will disagree but this has been my experience.

Cart

---

### Post by Thalaen on 2007-11-28
yes, I was using 64 bit - I'll download the 32 and try it.

---

### Post by Thalaen on 2007-11-28
Okay... so, I downloaded and installed the 32-bit version of 7.10. I now have a rapidly blinking cursor which responds to nothing; any ideas? And is this typical of a linux installation - like I said, this is my first ever experience with the system...

---

### Post by PmDematagoda on 2007-11-28
Try this:-

NOTE:- You may want to do this in Recovery Mode since it does not necessitate you to give the commands sudo powers and you may have less chances of making a mistake.


1) Install the kernel source code for your kernel (e.g. If your kernel is 2.6.22 then get that source code) using:-
```

sudo apt-get install linux-source-2.6.22
```

2) Download the [Nvidia driver]("http://www.nvidia.com/object/unix.html") and install it as given on web page.

3) After you install the Nvidia driver do this:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4) After that is complete do:-
```

sudo startx
```

Then see if your GUI works properly now.

---

