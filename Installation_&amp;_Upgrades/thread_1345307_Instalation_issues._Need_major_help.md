---
title: "Instalation issues. Need major help"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by soundout on 2009-12-03
Alright so i'm new to the whole linux thing but i'm experienced with computers. pretty easy to install this OS i mean shoot you read directions and bam there you go. Right well not for me. 

lets start off with i have an asus motherboard
Cpu: pentium D 3 GHz 
Graphics card: Nvidia geforce 7800 Gt
if that helps

ok so first i started to install it in windows using the disk on a partition i made on my second hard drive. worked just fine install wise. reboot and i select ubuntu and it goes through and installed to the checking partitions and it went to 128% or something. and then a messed up box with the same info came up on the top left side of the original. it looked kinda like someone toook a hammer to that part of the screen if you know what i'm talking about (sorry i'm describing it best i can). but my monitor is just fine. 

ok second was to just wipe my second hard drive and install it clean on that. did that went through every part just fine. but when i went to log in the first time i click my name and boom that same hammer to the screen thing came up on the login box. and it froze. 

third i tried the live disk. when it was booting up it did get ONE fail message. synch clock 
temporary fail in name resolution. alright and so it kept going though but when it went to actually start up my monitor said something to the effect of not recommended settings. and just left that message up. 

Possible issue? main harddrive is sata and second hard drive is ide issue?
video card not supported?

i mean would trying a different monitor work?

please give me suggestions and feedback
yes i know i spelled  installation wrong

---

### Post by earthpigg on 2009-12-03
can you take a picture of the 'hammer screen' with your cell phone or a digital camera... or find some better way to describe it....?

---

### Post by presence1960 on 2009-12-03
If it is your vid card try hitting F4 when you boot the Live Cd and get to the menu screen. Then choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions").

I would scrutinize your CD too. Start at the beginning. After downloading the iso did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso?

Did you burn the iso as an image to CD at 4x-8x speed? Higher speeds are ok for data but with an image if one little piece is messed up your iso image will be no good. If you need burning software that allows you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

When you boot from the Live CD select "check disk for defects" before doing anything.

---

### Post by soundout on 2009-12-04
> **presence1960 said:**
> If it is your vid card try hitting F4 when you boot the Live Cd and get to the menu screen. Then choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions").

I would scrutinize your CD too. Start at the beginning. After downloading the iso did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso?

Did you burn the iso as an image to CD at 4x-8x speed? Higher speeds are ok for data but with an image if one little piece is messed up your iso image will be no good. If you need burning software that allows you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

When you boot from the Live CD select "check disk for defects" before doing anything.
i did not md5sum the iso.

i did burn the imag as an iso but at 16x speed is what it was telling me. 

i dont think its the disk honestly after lookin at another thread. i think its the nvidea card i have i think there is something wrong with the way ubuntu loads the drivers and what not with nvidea cards. but i'll try re burning the disk. 

and the hammer to the screen thing. its like the one image thats on the screen just like all the lines are crooked and wrong colors are there and its just a mess.

---

### Post by lidex on 2009-12-04
> Originally Posted by presence1960
If it is your vid card try hitting F4 when you boot the Live Cd and get to the menu screen. Then choose safe graphics mode. See here.

Try that and see what you get. Once you get setup you'll be able to get your drivers sorted out. nVidia graphics are pretty linux-friendly, sometimes just needs a little tweaking.

---

### Post by soundout on 2009-12-04
the ultimate goal is to install in though. What will i have to tweak in order for me to install it.

---

### Post by presence1960 on 2009-12-04
> **soundout said:**
> the ultimate goal is to install in though. What will i have to tweak in order for me to install it.

Once installed using safe graphics mode you can install Nvidia drivers using System > Administration > Hardware Drivers.

You can also install ENVYNG and use that to install Nvidia drivers. From terminal run one at a time:

```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk
```

Then run envyng from Appplications > System Tools > EnvyNG or open a terminal and run ```
envyng -t
``` Follow the prompts to install Nvidia driver.

---

### Post by mozkill on 2009-12-04
If the safe mode video thing doesn't work, this also sounds a little bit like the kind of thing that could occur with a bad stick of ram also.

---

### Post by presence1960 on 2009-12-04
> **mozkill said:**
> If the safe mode video thing doesn't work, this also sounds a little bit like the kind of thing that could occur with a bad stick of ram also.

could be- so the OP should try troubleshooting with the simplest solution first then work up. I would try F4 safe graphics mode, then the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") then look at the RAM.

---

### Post by Dionysian on 2009-12-04
yeah, i've been having trouble loading 9.10 and have just successfully loaded it using the safe graphics mode.

my problem sounds similar to this gentleman's:  i have a nvidia 8800 gtx and i can't get it to load a driver.  so, i went into the terminal (while on safe graphics mode, obviously) and tried installing the "envyng" code - but it says that it can't find the package.  ???

---

### Post by darkod on 2009-12-04
> **Dionysian said:**
> yeah, i've been having trouble loading 9.10 and have just successfully loaded it using the safe graphics mode.

my problem sounds similar to this gentleman's:  i have a nvidia 8800 gtx and i can't get it to load a driver.  so, i went into the terminal (while on safe graphics mode, obviously) and tried installing the "envyng" code - but it says that it can't find the package.  ???

In the grub 2 menu select the recovery entry, not the normal one. Then I think it was the first next menu something like "root with networking", thatwill give you internet and a text command prompt. Install it with the command presence gave, it will work like that.

---

### Post by presence1960 on 2009-12-04
> **darkod said:**
> in the grub 2 menu select the recovery entry, not the normal one. Then i think it was the first next menu something like "root with networking", thatwill give you internet and a text command prompt. Install it with the command presence gave, it will work like that.

+1

You want netroot which is command prompt with networking

---

### Post by Dionysian on 2009-12-04
> **darkod said:**
> In the grub 2 menu select the recovery entry, not the normal one. Then I think it was the first next menu something like "root with networking", thatwill give you internet and a text command prompt. Install it with the command presence gave, it will work like that.

i'm running 100 percent 9.10, so i don't have a grub come up.

---

### Post by presence1960 on 2009-12-04
> **Dionysian said:**
> i'm running 100 percent 9.10, so i don't have a grub come up.

Hit shift to bring up the menu and choose recovery mode.

---

### Post by Dionysian on 2009-12-04
> **presence1960 said:**
> Hit shift to bring up the menu and choose recovery mode.

i restart the machine and constantly keep pressing shift but all it does is bring up the login screen.

i've installed it in graphics safe mode because when i installed it normally, it would crash about every five minutes.

---

### Post by soundout on 2009-12-04
i've hit f4 but didnt see a safe graphics mode option. when do i hit f4?

---

### Post by soundout on 2009-12-04
> **soundout said:**
> i've hit f4 but didnt see a safe graphics mode option. when do i hit f4?

just kidding wrong disk

---

### Post by presence1960 on 2009-12-05
> **Dionysian said:**
> i restart the machine and constantly keep pressing shift but all it does is bring up the login screen.

i've installed it in graphics safe mode because when i installed it normally, it would crash about every five minutes.

Try Esc then.

---

