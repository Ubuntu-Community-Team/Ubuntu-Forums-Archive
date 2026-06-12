---
title: "im stuck at #4 of the tutorial &quot;Partition scheme and ISO selection&quot;"
date: 2018-02-23
forum: Installation &amp; Upgrades
---

### Post by fixlaptop on 2018-02-23
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#3](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#3)

am i suppose to change anything?

also what is this doing, is this 'transferring' the iso to the usb?

or is this 'flashing' to the usb? or what?

do you need to select anything or can it just auto-transfer? by itsefl?

--

im not technical 

please use simple words so i understand

---

### Post by kerry_s on 2018-02-23
if your on windows 10 you want the uefi boot.
you should just be selecting the iso to put on the usb.

---

### Post by sudodus on 2018-02-23
The default settings are probably good but ...

Please tell us about your computer, brand name and model (or if a custom built system, brand name and model of the motherboard). Please tell us also when the computer or motherboard was manufactured (approximately which year).

Which version of Windows are you running in the computer? Was Windows installed by the manufacturer/vendor, or by you? Do you know if you are booting in UEFI mode or BIOS mode (alias CSM alias legacy mode)?

When we know this, it will be easier to give you relevant advice.

---

### Post by fixlaptop on 2018-02-23
> **sudodus said:**
> UEFI mode

i dunno, i dont understand this

dell inspiron n7110 

win10

[https://ubuntuforums.org/showthread.php?t=2385584&p=13742121](https://ubuntuforums.org/showthread.php?t=2385584&p=13742121) 

are some options better to pick for this os 

and this hardware?

do they affect anything significantly

im not installing it right now, im just following the steps on a usb

---

### Post by kerry_s on 2018-02-23
another program that can create the usb boot device is unetbootin-> [http://unetbootin.github.io/](http://unetbootin.github.io/)

---

### Post by kerry_s on 2018-02-23
just make sure the only drive your selecting is the usb drive.

---

### Post by fixlaptop on 2018-02-23
> **kerry_s said:**
> [http://unetbootin.github.io/](http://unetbootin.github.io/)

im confused, am i suppoed to use this??

is there a link for the steps for this thing?

is this better? 

is this better for win10 computers?

---

### Post by kerry_s on 2018-02-23
no, its only an option if rufus fails you.just continue with what your doing

---

### Post by sudodus on 2018-02-23
> **fixlaptop said:**
> i dunno, i dont understand this

dell inspiron n7110 

win10

[https://ubuntuforums.org/showthread.php?t=2385584&p=13742121](https://ubuntuforums.org/showthread.php?t=2385584&p=13742121) 

are some options better to pick for this os 

and this hardware?

do they affect anything significantly

im not installing it right now, im just following the steps on a usb

It should be possible to run any of standard Ubuntu and the Ubuntu community flavours in a dell inspiron n7110, but if you have an Intel i3 processor, it is is rather weak. Do you know about the graphics? Is there Intel graphics, nvidia graphics or amd/ati/radeon graphics? This makes a difference too. (I saw a web page showing the specs of a dell inspiron n7110 with nvidia graphics.)

If there is nvidia graphics, you need a proprietary driver, to take full advantage of it, and then it will probably perform much better than with the built-in free linux driver.

Anyway, it might work better with a light desktop environment, and you can get that from some of the following iso files: Lubuntu, Ubuntu Budgie, Ubuntu MATE, Xubuntu. You can **try** these systems live (booted from the USB pendrive) without installing. See

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by fixlaptop on 2018-02-23
> **sudodus said:**
> work better


yea it does look like there's a lot of difference in components

how about just what is the best performance analysis tool and i'll just run it on a couple of the 'versions'?

it has win10 so im guessing it can run any of them, 

 but some of them may be 'faster' - i dunno why or how that can be, that it runs faster (i guess that is what is meant by 'work better')

this is more about if the linux version would work well with the hardware

its intel hd graphics something

---

### Post by fixlaptop on 2018-02-23
that link is very very long, could you just make a new concise one?

the steps in the tutorial is kinda easier? to understand

is there just a bullet point list of what's suppose to be change or anything, and the original questions at the top?

---

### Post by sudodus on 2018-02-23
Instead of performance analysis tools, you can simply *run the application programs, that you intend to use*, for example browse the internet, and play video, and get a feeling of how it works with the different flavours of Ubuntu. (This is the basic test, and probably more relevant than the result of performance analysis tools.)

Intel graphics will usually work well with the built-in linux drivers. But it also means that you have no high-performance graphics.

---

### Post by sudodus on 2018-02-23
> **fixlaptop said:**
> that link is very very long, could you just make a new concise one?

the steps in the tutorial is kinda easier? to understand

is there just a bullet point list of what's suppose to be change or anything, and the original questions at the top?

1. Just continue with the default settings in Rufus according to the tutorial and the dialogue in Rufus.

2. Boot from the USB pendrive and check how it works.

- If it works well, fine :-)

- Otherwise, please tell us what happens (with as many details as possible), and we can suggest what to do.

---

### Post by fixlaptop on 2018-02-23
> **sudodus said:**
> a feeling of 

* without the performance analysis tool, they'll all 'feel' pretty much the same, none of this would matter then, it wont matter verison or anything that is the dual boot

* its if thigns are buggy on the hardware or not, but i wont be able to tell which is better now, and that means the w/e is picked would be insignficant without the performance analysis tool



> **sudodus said:**
> default settings

then it or anything should not be complciated

they should not show anything else besides the 'show advanced optoins/features for experienced users'


every single thinig has been complicated up to this point

if nothing matters, why is the tutorial so complciated?

if nothing matters, why do ppl make comment that are not need or helpful and confues me?

just click/tap ok ok ok ok then

why do they make everythign so diffciutl for when they dont need to be?

needlessly compicated


---

well it looks there's only 1 thing to know here, which is one of the many helpful thigns the tutorial never says as well

after you press all the oks, you just restart, and the computer autoamtically boots from the usb, i guess? nothing needs to be done?

---

### Post by sudodus on 2018-02-23
> **fixlaptop said:**
> * without the performance analysis tool, they'll all 'feel' pretty much the same, none of this would matter then, it wont matter verison or anything that is the dual boot

* its if thigns are buggy on the hardware or not, but i wont be able to tell which is better now, and that means the w/e is picked would be insignficant without the performance analysis tool

If you notice no difference in performance, you should pick the desktop environment that you like best. But sometimes there are really big differences in performance (that are easy to notice), particularly with weak and/or old hardware.
> 
well it looks there's only 1 thing to know here, which is one of the many helpful thigns the tutorial never says as well

after you press all the oks, you just restart, and the computer autoamtically boots from the usb, i guess? nothing needs to be done?
This is different between computers and their UEFI/BIOS systems. Sometimes it is easy to make the computer boot from USB, sometimes more complicated.

I have a Dell Latitude E7240, and I make it boot from USB by pressing the hotkey F12 directly after booting. Then I arrive at a boot menu with several options. Maybe it is the same hotkey in your computer, maybe another one. You can probably find out via the internet (or simply by trial and error with some other hotkeys).

---

### Post by fixlaptop on 2018-02-24
'If you notice no difference in performance'

yea ur right performance doesnt matter

performance is not in the top 2 or 3

perfroamnce doesnt matter compared to more important thing

---

### Post by kerry_s on 2018-02-24
alright enough of that.

how did it go? did you get a working usb to play with?

---

### Post by coffeecat on 2018-02-24
As the OP has now left the building, I've closed this thread.

Thanks to all for your time and patience.

---

