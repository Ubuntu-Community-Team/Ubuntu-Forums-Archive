---
title: "Installation Fail to Load X"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by giannisapatis on 2006-11-26
Hi and thanks in advance,

I am trying to install ubuntu 6.10 in my pc.

I have got and AMD64 3000+ (am trying to install i386)
                Nvidia 6200 256 ram
                2gb RAM.

When i choose start or install UBUNTU the kernel boots,
it loads everything i suppose and then it takes me in a black screen where it loads my mouse , then an orange scrren appears (my mouse works fine) but the window which shows the components to be loaded never comes up. 
  After some seconds i hear a bip sound from inside my pc (bios i suppose).

I try to do CTRL + ALT + F1 but a scrren with lots of meaningfull orange characters comes up and is not going to let me right,

It did let me once to issue commands on the command line and i tryied sudo dpkg-reconfigure xserver-xorg and then sudo /init.d/gdm restart.

Then i would get a message something like: Restart gnome [fail].

Could you please help me to solve this problem!!!!

Sorry for the long post and thanks in advance again.

Giannis

---

### Post by taurus on 2006-11-26
Maybe you want to use the alternate CD and make sure you burn it at a slow speed like 4x if you can...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by giannisapatis on 2006-11-26
Ok I will try that an update as soon as possible.

Thanks a lot,
Giannis

---

### Post by giannisapatis on 2006-11-26
Hi,

I tried the alternate cd. 
It takes me up to the point to configure my wireless card(d-link atheros) i configure it successfully and then the screen "detectind hard disk and other hardware components" appears . after that i can  only see a blue screen and nothing else thats it.

I think it will be something with my hardware probably about my motherboard.

Do you have any ideas what it would be ???

Thanks in advance,
Giannis

---

### Post by taurus on 2006-11-26
What type of harddrive do you have:  PATA or SATA?

---

### Post by giannisapatis on 2006-11-26
Hi,
I dont really know to be honest with you ,
In windows in device manager it says 
IDE ATA/ATAPI controllers
Standard IDE ATA/ATAPI controllers)

Does it make any defference?

I think its just a normal hard drive its a maxtor 80gb one.

If you could tell me what i should do in each case it would be great mate.

Thanks a lot,
Giannis

---

### Post by taurus on 2006-11-26
That would be PATA (or EIDE).  Do you have an empty partition on your harddrive to install Ubuntu?  If not, you need to use the GParted LiveCD (since the Ubuntu LiveCD won't boot with your machine) and resize your harddrive first, leaving some free space at the end to install Ubuntu.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

And of course, _always_ backup your important files on your XP in case something goes terribly wrong...

---

### Post by giannisapatis on 2006-11-26
Hi again,
 my hard disk is maxtor 6Y080P0  bu ti dont really know how to find this out.
This a link with the hard disk specification
[http://www.digit-life.com/articles2/maxtor-6y080p0/index.html](http://www.digit-life.com/articles2/maxtor-6y080p0/index.html)

Thanks a lot,
Giannis

---

### Post by giannisapatis on 2006-11-26
Hi, yes i do have an empty partition in my hard disk.

I have partitioned my hard disk using partition magicas follows:

Parttion 1: Windows
Partition 2: Swap
Partition 3 : Ext3

Thanks a lot,
Giannis

---

### Post by taurus on 2006-11-26
Well, use the GParted from the link that I included from above.  Then, you can view and resize your harddrive.

---

### Post by giannisapatis on 2006-11-26
Ok thanks  a lot i will do that as soon as possible and then update what happened,

Thanks a lot,
Giannis

---

### Post by taurus on 2006-11-26
Good luck.

---

### Post by giannisapatis on 2006-11-27
Hi,

I format my hard disk with GParted as:

Partition 1: NTFS - Windows
Partition 2: Swap
Partition 3: Ext3

The same thing it will be stack in the same place again as before.

I dont understand because debian installs ok (but its too difficult for me to configure it)
Do you think it could be because of my motherboard (its a gigabyte K8Triton series Agp8x/ddr400)?

Or could it be a problem because amtrying to install i386 in a AMD64?

Do you have any other idea please?

Thanks a lot for your help,
Giannis

---

### Post by giannisapatis on 2006-11-27
Hi again,

this is a link to my motherboard specification,


[http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1876](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1876)

Thanks again,
Giannis

---

