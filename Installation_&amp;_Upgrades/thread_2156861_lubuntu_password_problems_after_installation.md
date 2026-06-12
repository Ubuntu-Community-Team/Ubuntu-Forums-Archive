---
title: "lubuntu password problems after installation"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by sisqonrw on 2013-06-23
Hi i have the newest lubuntu version two times. but after restart there is a black field in the bottom of the display. i type there the password  but lubuntu is trying to boot and goes later in the shell view. there is something like

gave up waiting for root device common problems
boot args ....
check rootdelay....
check root....
missing modules
allert!..... does not exist dropping shell
(initramfs)

what is the problem here?

---

### Post by sudodus on 2013-06-23
Please describe your computer, at least cpu, ram and graphics chip/card

And please tell how you are running it: Installed or live? I guess installed, if so, how did you install it?

---

### Post by sisqonrw on 2013-06-23
> **sudodus said:**
> Please describe your computer, at least cpu, ram and graphics chip/card

And please tell how you are running it: Installed or live? I guess installed, if so, how did you install it?

it is an acer aspire 5672WLMI
Intel Core Duo T2300
ATI Radeon X1400 512MB
80GB HDD
1GB DDR2

i have try it before i installed. and it has worked.

---

### Post by sudodus on 2013-06-23
I think you have problems with the graphics driver. Unfortunately some drivers for aging hardware are lost in new versions of the Ubuntu kernel, which is used in all flavours of Ubuntu.

You will probably have better luck with the earlier version 12.04 which has also long time support, so it is well debugged and polished. Unfortunately Lubuntu 12.04 is excluded from that, and will reach end of life in October this year. But the specs of your computer indicate, that it should work also with a little more demanding (but still light-weight) desktop environment, XFCE of Xubuntu.

So I would recommend that you try ***Xubuntu 12.04 LTS***, which is supported until April 2015.

---

### Post by sisqonrw on 2013-06-23
> **sudodus said:**
> I think you have problems with the graphics driver. Unfortunately some drivers for aging hardware are lost in new versions of the Ubuntu kernel, which is used in all flavours of Ubuntu.

You will probably have better luck with the earlier version 12.04 which has also long time support, so it is well debugged and polished. Unfortunately Lubuntu 12.04 is excluded from that, and will reach end of life in October this year. But the specs of your computer indicate, that it should work also with a little more demanding (but still light-weight) desktop environment, XFCE of Xubuntu.

So I would recommend that you try ***Xubuntu 12.04 LTS***, which is supported until April 2015.

can i see in a report file where the problem is? 

why does the live version works and the installed not. i thing it is a other problem. maybe something with password, etc.

---

### Post by sudodus on 2013-06-23
Your decription of the problem made me think of the graphics driver.

It is usually but not always as you write. Sometimes the drivers are initiated differently between the live session and the installed system. Often there are problems with the graphics chip, sometimes also with the wifi chip, if there is one. So it could make a difference if the wifi is connected/switched on or not.

I know no report file about this. But someone else might know.

But maybe it is not the graphics. I'm running Lubuntu too, so I know what it should look like.

Which version are you running? 13.04 or the new Saucy (not yet released)?

Please describe (more details) what it looks like and what happens, when you intend to log in!

---

### Post by sisqonrw on 2013-06-24
i have installed again and choose auto login. now it works. but i didnt choose crypt my files and folders. maybe that is the reason.

---

### Post by sudodus on 2013-06-24
We will never know the reason, but the important thing is that Lubuntu is working for you now :-)

I have a Lubuntu + xubuntu-desktop 12.04 system with encrypted home. It works for me.

---

### Post by sisqonrw on 2013-06-24
i havent use hdd cryption. with cryption it will not works. only with user folder cryption it will be work.

---

