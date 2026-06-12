---
title: "ubuntu 10.10 installation problem"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by malaysian on 2010-11-25
Hi,I,m new in ubuntu.During my installation with ubuntu 10.10 with live cd ,my computer hangs when the colour splash screen is displayed.Tried several times but still cannot get it to install.

The computer i'm using:
Pentium 4 with 1 GHz
128mb RAM
NVidia GEforce FX5500

---

### Post by SteveDee on 2010-11-26
> **malaysian said:**
> 
The computer i'm using:
Pentium 4 with 1 GHz
128mb RAM....

I don't think you have enough RAM for Ubuntu (you need at least 512MB).

You should try Lubuntu which will run (slowly) on 128MB, or Puppy Linux.

---

### Post by Hippytaff on 2010-11-26
An alternative would be to boot into recovery mode (in the boot screen where you have kernel/os options).
 
Then drop into terminal with networking and do
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install lubuntu-desktop

```
reboot.
If the pc still struggles, open a terminal and try
```

sudo apt-get fluxbox

```
reboot and on start up choose fluxbox on the desktop option before logging in... if you decide to give this a bash, let me know how it goes :-)

---

### Post by malaysian on 2010-11-26
But i don't know how to boot into recovery mode.(Sorry,i'm still new to this.)

---

### Post by Hippytaff on 2010-11-27
Sorry, when you boot your pc if your dual booting with windows you get the option to choose os's and kernels. choose the (usually) second kernel on the list...then you will see another box with options you can select using the up and down arrows...choose terminal with networking then type the command I posted.

:-)

---

### Post by Rubi1200 on 2010-11-27
Hi,
128 MB of RAM is definitely not enough; especially during the installation process as the installer requires at least 512 MB at that point.

Hippytaff has offered some good alternatives.

Additionally, you may want to consider some lighter alternatives such as Lubuntu, Puppy Linux, SliTaz, or antiX.

---

### Post by Hippytaff on 2010-11-27
I should also have mentioned to reboot from the terminal (command line) do
```

shutdown -r now

```

---

### Post by malaysian on 2010-11-27
Are there  boot screen that have kernel/os options?I'm now only booting from the live cd and what i can get is this menu only(correct me if i am wrong).Until now there is only windows xp installed in my computer only.

---

### Post by Hippytaff on 2010-11-27
Not sure, it might be in modes or other options, if you haven't installed ubuntu yet you can download a Lubuntu CD to make life easier :-)

---

### Post by malaysian on 2010-11-29
I'll try the puppy linux in this computer.Will try ubuntu in my laptop.Thanks everyone for helping me to understand linux.

---

