---
title: "ubuntu mate won't boot"
date: 2015-01-29
forum: Installation &amp; Upgrades
---

### Post by lemured on 2015-01-29
hi everyone,

i'm trying to install Ubuntu Mate on my new laptop, which is currently cursed with windows8. 
i'm driving stick and successfully used USB installer. 
according to the manual it should now boot and present me with a 'welcome/choose language'-screen, but nope.
i'm advised to use f12, problem is, this comp's got an 'airplane-function' for using wireless on flights, and f12 does
nothing but turning this on and off - by which i loose net connection every time, and, ofc, the welcome screen doesn't
pop up, either.


any help, suggestions, paper tissues?

please be advised that i'm an IT-virgin, i'm really crap the moment a problem emerges :)

thanks

 lemured

---

### Post by yancek on 2015-01-29
You need to find some way to enter the BIOS.  On boot, you should see a message at the bottom of the screen informing you which key to presse to "enter setup" where you should see a Boot tab or something allowing you to change the boot priority to the flash drive you are using.  Maybe if you mentioned the manufacturer, someone might be familiar with it and be able to suggest something.

---

### Post by lemured on 2015-01-29
> **yancek said:**
> You need to find some way to enter the BIOS.  On boot, you should see a message at the bottom of the screen informing you which key to presse to "enter setup" where you should see a Boot tab or something allowing you to change the boot priority to the flash drive you are using.  Maybe if you mentioned the manufacturer, someone might be familiar with it and be able to suggest something.

hi yancek,
thanks. yes, i'm trying that, and fail. none of the keys work. also went into UEFi firmware settings, but am lost there.
manufacturer/model:

toshiba satellite pro nb 10t-A-108

---

### Post by lemured on 2015-01-29
p.s. in other words, if there's a way to enter bios in the UEFI settings, i don't know it.

---

### Post by lemured on 2015-01-29
p.p.s.
i should add that i'm going through a series of troubles, each day a new one. the current is that i'm deprived of my cursor, have to do everything by touch screen.

---

### Post by lemured on 2015-01-29
ok, finally managed to change boot order :)
but nothing :(

---

### Post by lemured on 2015-01-29
right, meanwhile i learned that i have to create a partition 1st

[http://askubuntu.com/questions/315242/ubuntu-13-04-alongside-windows-8-how-to-partition-from-windows](http://askubuntu.com/questions/315242/ubuntu-13-04-alongside-windows-8-how-to-partition-from-windows)

but with the current ticks - no cursor [no, no freeze, just no cursor] - this is going to be a hassle, and i'll have to continue tomorrow

the above link is quite helpful

here's another one for general installing:
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

seems like windows8 has been designed for making these problems...

---

### Post by lemured on 2015-01-30
ok, if anyone still reads this....

btw, the 'lost cursor' issue: although i am stupid in general, the problem was not the thing having been disabled while trying var. keys - or it had initially - but enabling it again this way didn't work. a restart did the trick. it was definitely the day's micros**t-tick.

the main problem remains:
i've been following the steps detailed in the [very helpful] manual, 2nd link in the previous post, by the letter.
partitioning was a limited option as w8 does allow me to shrink C, but not to expand. it has enough space, though.

done everything as advised in the UEFI Firmware settings, order is correct and enabled. next thing that should happen:
'[COLOR=#333333][FONT=UbuntuRegular]The system will reboot and you will be allowed to go to the [/FONT][/COLOR]**BIOS**[COLOR=#333333][FONT=UbuntuRegular] (If not press the appropriate key, some common are [/FONT][/COLOR]DEL[COLOR=#333333][FONT=UbuntuRegular],[/FONT][/COLOR]F2[COLOR=#333333][FONT=UbuntuRegular] or [/FONT][/COLOR]F10[COLOR=#333333][FONT=UbuntuRegular])'

system did reboot, ofc, but nada, am not allowed to go anywhere, nothing. key-issue the same. and that means basically i have no idea how to continue from here.
in general i have the distinct feeling that windows has been prepared to do anything in its might to prevent having an alternative installed, which would simply be unethical.

anyone? help me?  :)[/FONT][/COLOR]

---

### Post by lemured on 2015-01-30
also tried with disabled SecureBoot. nothing

---

