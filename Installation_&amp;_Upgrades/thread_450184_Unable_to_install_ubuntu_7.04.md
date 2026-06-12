---
title: "Unable to install ubuntu 7.04"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by nagoo on 2007-05-21
I am unable to install ubuntu 7.04 in my new system, i am getting the fallowing probl'm

1. when i insert the install CD everything seems fine , when i try to install my monitor resolution/color will starts flickering and eventually i can't see anything , entire screen will be filled with some green , blue distorted color 

plz help me in this 

system config:-

Processor=AMD X2 4600
hard disk = seagate SATA 160GB
RAM = 1GB [Transend]
motherboard = Asus nvidea M2N-MX
monitor = LG 700E 17" [CRT]

Thanks in advance

---

### Post by vikramsharma on 2007-05-21
> **nagoo said:**
> I am unable to install ubuntu 7.04 in my new system, i am getting the fallowing probl'm

1. when i insert the install CD everything seems fine , when i try to install my monitor resolution/color will starts flickering and eventually i can't see anything , entire screen will be filled with some green , blue distorted color 

plz help me in this 

system config:-

Processor=AMD X2 4600
hard disk = seagate SATA 160GB
RAM = 1GB [Transend]
motherboard = Asus nvidea M2N-MX
monitor = LG 700E 17" [CRT]

Thanks in advance

It looks like driver for Graphics Card is not installed, install the graphics card using the "Restricted Driver Manager ",  you can go there via System->Administration->Restricted Driver Manager.  Hope this helps

---

### Post by nagoo on 2007-05-21
i haven't installed any additional Graphics card

but the mother board has [Asus nvidea M2N-MX] the fallowing

NVIDIA GeForce 6100 /NVIDIA nForce 430  
NVIDIA nForce 430 =chipset

---

### Post by vikramsharma on 2007-05-21
Please install the driver for Nvidia, inthe System menu go to Administartion section and choose Restricted Drivers Manager and install the driver for Nvidia.

---

### Post by nagoo on 2007-05-21
I think i have installed all the drivers from the CD given with the motherboard.
Is restricted drivers will be available in the motherboard CD ?

I have tried with other unix flavours also like , Fedora core 5, there aslo same probl'm and here i can see the msg monotor type = unknown, is it probl'm with the monitor ?

plz , help in clarifying this issue

Thanks

---

### Post by vikramsharma on 2007-05-21
The drivers for Linux are not shipped with motherboard cd.  You would have to install Linux driver separately, after booting into Linux.  Once you install Ubuntu, the drivers are there in the system all you would have to do is install them.  I have explained the method of installing drivers in my previous message.  Also try this [link]("http://lunapark6.com/ubuntu-704-feisty-fawn.html") .  Hope this helps

---

