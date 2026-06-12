---
title: "Can I install Ubuntu on 4Gb USB drive?"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by Triple-H on 2008-07-25
Hi UBUNTU users!

I am new to Linux and I use Puppy linux because i can run it completely from USB drive

However, i am very dis-satisfied because it supports its own software only, and most software on the net is for UBUNTU

and i am a webdesigner so i need some software and i love the default UBUNTU theme ( also i like UBUNTU STUDIO )

I need a linux version that runs totally from usb 4gig stick, i found out that fedora can run like this very easily and i can save changes to it also

**But i am in love with UBUNTU **{although i never used it }, i searched for a way to install Ubuntu on 4gig usb but i found very hard ways that include scripting and weird symbols, 

SO IS THERE A WAY TO INSTALL UBUNTU ON 4GB USB _EASILY _? I WANT IT TO BE INSTALLED JUST LIKE NORMAL HDD INSTALLS, I WANT TO BE ABLE TO SAVE MY SETTINGS AND PROGRAMS , 

if not, IS FEDORA 9 SIMILAR TO UBUNTU?

IS UBUNTU or FEDORA FASTER THAN WINDOWS ON SLOW PCs?

HELP ME PLEASE and sorry for mentioning Fedora here but i had to

Thank you

---

### Post by tamoneya on 2008-07-25
if you dont want to have to mess around with command line and optimizing what programs and such you have installed and which are necessary and which are not you should go with xubuntu instead of ubuntu.  It is the lightweight version of ubuntu.  Should work fine with your drive and still leave space for your documents.

---

### Post by Rhubarb on 2008-07-25
This will allow you to install Ubuntu (with persistancy, so you can save documents etc and it'll be there when you boot up from it next time):
From the Ubuntu live CD: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)
From a linux environment: [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

---

### Post by Pumalite on 2008-07-25
You can install to your USB as if it were a hard drive.
Search post by Herman

---

### Post by jimv on 2008-07-25
I just did this last week.  You can install Ubuntu to a USB thumbdrive the same as a regular harddrive.  No need for that persistence stuff that the other guy was posting.

Boot from the CD, plug in yoru USB drive, and run the installer.  During the install, select your USB drive to do the install to.  Then, on the last screen before the actual installation, there is a button that says "Advanced".  Click that and you'll see a spot where you can tell it which drive to install Grub on.  Set that to the USB drive and then do the install.

Also, you don't need to use Xubuntu like someone suggested.  Ubuntu will install just fine on a 4 gig thumbdrive, and leave you with about 1.5 gigs of free space.

---

### Post by Triple-H on 2008-07-25
Hi all

Thank you very much for this support! I am really surprized by the number of posts!

Thank you :

tamoneya: I will search for Xubuntu, but i believe that Ubuntu is fine for me, see the post by jimv
 
Rhubarb:Thank you for help, but this is exactly what i DONT want, take a look at it, it is very hard. Thank you for searching for the links.

Pumalite: Thank you, I will search for the guy.

jimv: I am interested the most in your post, I read a similar method but it was the only one i found and the guy who wrote it gave too much cautions about data corruptions and stuff, so i was pretty scared of this method. You mentioned that I will have 1.5 gigs free, do i need to do a partition for them in order to make them usable?

Also i need to run Ubuntu on a 128 ram, so is Xubuntu better in this case? is it similar to Ubuntu or what? I want to install two graphics softwares as well as some html and code editors, so which is better?

Also is there any risk of data loss on the main hard drive? I will be killed if i mess the data on the main hard disk

Please let me know if Ubuntu runs well on a 128 RAM, i hate windows because it is really slow on this machine

THANK YOU ALL GUYS, please help me with the rest of my questions

THANK YOU AGAIN

---

### Post by Pumalite on 2008-07-25
Yes. Try try the Alternate Xubuntu. If not do a Minimal install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Triple-H on 2008-07-25
Hi
thank you for your reply 

i will see the link and i will try to understand what a minimal install is

i will tell you what happens

thank you again

---

### Post by Triple-H on 2008-07-25
Hi again 

i viewed the post

it is made for too light versions, also it will take time and it is hard, i wrote this topic because i dont want hard ways

by the way, i have Puppy Linux and it is very very fast, but i dislike one thing about it, it has its own software, while UBUNTU has much software available

that is why i want UBUNTU

thank you

---

### Post by Triple-H on 2008-07-25
I forgot to ask:
does ubuntu software work on fedora? If so, I can save myself alot of pain, fedora has a nice usb installer directly from windows

please answer this,

Thank you for help

---

### Post by tamoneya on 2008-07-25
ubuntu binaries are debs while fedora uses rpm so while most programs are packaged as both deb or rpm the installers themselves wont work.  Probably not a good idea to use that fedora install.  Unless of course you want fedora which is fine as well.

---

### Post by Triple-H on 2008-07-25
Hi

thank you for reply, but to be honest, i understood nothing

sorry guys but i am absolute begginer, so speak english please :)

I dont understand the installers thing, i just wanna know if Ubuntu works well on slow PCs, and i want to make sure that it gets installed properly, so i email Herman

I could understand one thing from your reply, i understood that fedora software is different from Ubuntu, correct me if i am wrong

thank you for help, and by the way
NOW i am completely lost :lolflag: 

HELP!

---

### Post by tamoneya on 2008-07-25
basically the fedora installer installs fedora.  If you want fedora go ahead and use it otherwise follow the guides in the above posts to install ubuntu.

---

### Post by jimv on 2008-07-26
I use an old PC with 1ghz processor and 384mb of RAM and Ubuntu as a media server.  It works great.

Also, I've installed Ubuntu on an old laptop with 256 mb of RAM is it ran great.

Now about the USB/Install thing.  When you boot from the Ubuntu CD, it boots up to the Ubuntu desktop, and you can pretty much use everything like it's already installed...kind of like a test drive.  There's an icon on the desktop that starts the actual installer, and it's fairly simple to go through.


The Fedora/Ubuntu thing that the guy above was talking about was that Ubuntu programs come packaged in files called DEBs, and Fedora programs come packaged in files called RPMs.  Now while the programs are the same, the packages are not compatible...so Ubuntu won't install a program packaged as an RPM, nor will Fedora install a program packaged as a DEB.

---

### Post by Rhubarb on 2008-07-27
I'm not sure Ubuntu (or even Xubuntu) will run on 128MB of RAM.
Have a look here in the "Minimum system requirements" section:
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)
> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

