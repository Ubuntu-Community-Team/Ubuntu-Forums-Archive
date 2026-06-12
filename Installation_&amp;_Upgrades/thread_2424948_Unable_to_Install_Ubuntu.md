---
title: "Unable to Install Ubuntu"
date: 2019-08-17
forum: Installation &amp; Upgrades
---

### Post by shubham10200 on 2019-08-17
I  am currently running on windows 10 , and I want my computer to be dual boot with Ubuntu . So yesterday I downloaded Ubuntu latest version and booted into my usb drive when I tried to install it through boot menu , for few seconds there was a logo of Ubuntu and then a some codes keep blinking on the screen and nothing is happening   Please help me :( I am too worried , I downloaded Ubuntu two times I thought there is some error while downloading .
Here are thinga what I did :
Here are things which I did (I was following instructions from a you tube video)
1 . I downloaded Ubuntu 9.04 ISO file.
2 . I downloaded ether ( a software which helps to boot ISO into usb drive ) .
3 . I formatted my usb drive , and flashed it with Ubuntu ISO file .
6 . I created 100 GB unallocated for Ubuntu installation .
7 . I restarted the computer into boot menu .
8 . Selected External drive .
9 . After few seconds of loading Ubuntu icon was there for few seconds .
10 . Then a error came 'Can not find Trocbone , database may be currupt ’ , then a screen came where Ubuntu icon was in background and some codes were blinking there ( I’ll add that photo below).
11. I thought it is a part of installtion process , I waited for 30 minutes , nothing happened just codes blinking .
13 . I restarted my computer to windows by pressing power key for 10 seconds .
14 . I thought my ISO file was currupted . so I downloaded again Unbuntu18.04 from Ubuntu.com , and repeated the same process and the same thing happened , same error came .
15 . I tried to change the booting software I used universal usb , rufus instead of etcher .
16 . I thought there is some error in my pendrive , so I changed my usb drive .
17 . Noting worked :(

---

### Post by crip720 on 2019-08-17
You seemed to have have everything right in toubleshooting.  You can give us details for your computer, make model, cpu and ram.  The line #1, am hoping that is typo and you meant 19.04. Can you also check trocbone or translate.  Also make sure windows fast boot is turned off.

---

### Post by shubham10200 on 2019-08-17
I'm using dell inspiration 3558 which has 4GB of Ram intel i3 1.7GHZ processor . It came with ubuntu from manufacturer . It's been 3 years since I bought this computer . On more thing in line #10 that is Tocblock not trocbone , it was a typing mistake . And here are few images of the error . Please help me I am too worried :(
[https://ibb.co/R642v6M](https://ibb.co/R642v6M)[URL="https://ibb.co/Vjnmsv3https://ibb.co/511s4KD"]
[/URL]h[ttps://ibb.co/8X9qCzj]("https://ibb.co/8X9qCzj")
[https://ibb.co/6vnsCJj](https://ibb.co/6vnsCJj)

---

### Post by yancek on 2019-08-18
When you download the Ubuntu iso, you should do an md5 or other checksum on the iso to verify that it is good.  See the link below.

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

One of the images you posted shows an ntfs filesystem on :(hd0,2).  You aren't trying to install Ubuntu on ntfs?

The link below is the Ubuntu documentation on dual booting with windows 10, hopefully something on that page will help.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by crip720 on 2019-08-18
Tocblock helps a lot, it might be as simple as disabling secure boot from a google search for tocblock. Suggest you do a google search also and see if anything is more helpful.

---

