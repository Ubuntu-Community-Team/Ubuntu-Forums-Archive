---
title: "First time with ubuntu. Advise much needed."
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by albertc30 on 2011-03-14
Hello everybody.
 
I am new around here and to the Linux world as well.
 
As I have had enough really with microsoft OS and constantly instalations I have decided to give it a go with Linux.
 
I am going to use ubuntu 10.10, the latest will use previous if advised.
 
I have the following;

[LIST]
[*]Gigabyte GA-946GMX-S2 REV1.0,
[*]2x1GB DDR2 PC2-5300,
[*]Intel Pentium Dual Core 1.6GHz.
[/LIST]I have determined that the drivers I will need are as follows;
[LIST]
[*]Northbridge Intel 946GZ,
[*]Soulthbridge ICH7,
[*]Ethernet RTL8110SC,
[*]Sound ALC888
[/LIST]Now the questions are;[LIST=1]
[*]Will I have any driver problems with this setup? Well, this motherboard?
[*]What would be, if there is any, the drivers instalation order? On a windows OS I would start by installing the chipset drivers. Should I follow the same logic here?
[/LIST]Any comments are really welcome as I might be totally in the dark. I have already have ubuntu installed on another setup so that I can get a feeling of what it is like but I must confess that ultimatelly, I am clueless as to where are things like network name, etc... One thing I can't change on this first install is the screen resolution so I am guessing that the proper drivers aren't installed.
 
Again, any help well appreciated.
 
Best regards,
Albert, C

---

### Post by Vdragon on 2011-03-14
> **albertc30 said:**
> Hello everybody.
 
I am new around here and to the Linux world as well.
 
As I have had enough really with microsoft OS and constantly instalations I have decided to give it a go with Linux.
 
I am going to use ubuntu 10.10, the latest will use previous if advised.
 
I have the following;

[LIST]
[*]Gigabyte GA-946GMX-S2 REV1.0,
[*]2x1GB DDR2 PC2-5300,
[*]Intel Pentium Dual Core 1.6GHz.
[/LIST]
I have determined that the drivers I will need are as follows;
[LIST]
[*]Northbridge Intel 946GZ,
[*]Soulthbridge ICH7,
[*]Ethernet RTL8110SC,
[*]Sound ALC888
[/LIST]
Now the questions are;
[LIST=1]
[*]Will I have any driver problems with this setup? Well, this motherboard?
[*]What would be, if there is any, the drivers instalation order? On a windows OS I would start by installing the chipset drivers. Should I follow the same logic here?
[/LIST]
Any comments are really welcome as I might be totally in the dark. I have already have ubuntu installed on another setup so that I can get a feeling of what it is like but I must confess that ultimatelly, I am clueless as to where are things like network name, etc... One thing I can't change on this first install is the screen resolution so I am guessing that the proper drivers aren't installed.
 
Again, any help well appreciated.
 
Best regards,
Albert, C

--------------------------------------------
I'm newbie here, though:D

Will I have any driver problems with this setup? Well, this motherboard?
[B]Most "common" devices are supported by Linux, like graphic cards, motherboards, etc.,,
Install new driver is not needed unless you find something isn't working(Including plugging new devices)
If available, you can install not-free drivers in Administration->Hardware Drivers[/B].
**It will be difficult to solve if you find some drivers like webcams which only have Windows-only drivers. **

Sorry for my English

---

### Post by coffeecat on 2011-03-14
Welcome to the forum!

> **albertc30 said:**
> 
Now the questions are;
[LIST=1]
[*]Will I have any driver problems with this setup? Well, this motherboard?
[*]What  would be, if there is any, the drivers instalation order? On a windows  OS I would start by installing the chipset drivers. Should I follow the  same logic here?
[/LIST]
Fortunately, you can forget all your Windows habits. :) Installing motherboard drivers will be a thing of the past. Almost all the drivers you'll need come in the tin, mostly in the form of kernel modules. In fact I'm so used to installing Linux on a variety of motherboards and everything just working, that the last time I installed XP for a relative it took me a few moments to realise why ethernet, sound and a few other things were not working!

Install and if anything doesn't work, come back and ask. In fact, you don't even need to install to try your motherboard out. You can run a live CD session by choosing "try Ubuntu" instead of "install Ubuntu" when you boot the CD up. It will be very slow but you get to try the hardware.

One possible complication - the graphics card.

> **albertc30 said:**
> 

[LIST]
[*]Gigabyte GA-946GMX-S2 REV1.0
[/LIST]
Google has let me down. When I searched for that, all google served me up were sites to download drivers - which is ironic! I couldn't find the specifications. What is the graphics chipset, or are you using a PCIe graphics card? If so, which one?

---

### Post by albertc30 on 2011-03-14
> **coffeecat said:**
> Welcome to the forum!

Fortunately, you can forget all your Windows habits. :) Installing motherboard drivers will be a thing of the past. Almost all the drivers you'll need come in the tin, mostly in the form of kernel modules. In fact I'm so used to installing Linux on a variety of motherboards and everything just working, that the last time I installed XP for a relative it took me a few moments to realise why ethernet, sound and a few other things were not working!

Install and if anything doesn't work, come back and ask. In fact, you don't even need to install to try your motherboard out. You can run a live CD session by choosing "try Ubuntu" instead of "install Ubuntu" when you boot the CD up. It will be very slow but you get to try the hardware.

One possible complication - the graphics card.

Google has let me down. When I searched for that, all google served me up were sites to download drivers - which is ironic! I couldn't find the specifications. What is the graphics chipset, or are you using a PCIe graphics card? If so, which one?

Hello.

I believe it to be an [Integrated Intel® Graphics Media Accelerator 3000]("http://www.gigabyte.lv/products/page/mb/ga-946gmx-s2/advantage/") accordingly to Gigabytes website.

Thanks for your much appreciated advice.

Kind regards,
Albert,C

---

### Post by Dutch70 on 2011-03-15
The best way to find out is to run the live cd or usb. The usb is easier & faster if you have one. Also, using Ubuntu's "start-up disk creator" is a very simple way to make the live usb stick. 

Alternatively, you can use the "universal usb installer" found here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")
On step 2, just tick usb stick & click "show me how" 

or you can use Unetbootin, also very simple.
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Be sure to select "Try Ubuntu" and you can run it from the usb stick. If all goes well, you can install it from there.

---

### Post by coffeecat on 2011-03-15
> **albertc30 said:**
> I believe it to be an [Integrated Intel® Graphics Media Accelerator 3000]("http://www.gigabyte.lv/products/page/mb/ga-946gmx-s2/advantage/") accordingly to Gigabytes website.

You should be fine with that. With the exception of the dreaded Poulsbo and early chipsets, Intel graphics tend to just work.

---

### Post by mörgæs on 2011-03-15
Welcome aboard. 

I agree with the other posters: If you just install having wired internet access in the process, then chances are good that everything works in first attempt.

There is a link to a good Ubuntu handbook in my signature.

---

### Post by albertc30 on 2011-03-20
OK everybody.
 
Firstly thank you all for all the help and advice, very helpfull indeed.
 
Everything went smooth appart from swapp partition ????????? I was like OMG what the hell?????? but managed to do it. Even though I have 2GB DDR2 800 I created a 5GB swapp partition. Any comments on this is welcome.
 
On another note, I managed to remove the bar that controls you desktops, the one that you can togle between desktops and consectuvelly the one where you can see your open windows that have been minimized.
 
I have looked everywhere and can't get it back. I am desperate.
 
Another thing is, I have setup this pc to connect to my local network, I can get e-mails and surf the net. However, how can I share and view shared folders here on this ubuntu machine, on my windows OS pcs and viceversa?
 
How can I give the network a name just as I have under windows?
 
This pc will serve me for all my e-mail, business and maybe private and will be used to do all the online surfing and shearching.
 
Again, any comments and help are most appreciated.
 
Cheers.
Carlos

---

