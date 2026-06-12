---
title: "Which download of Ubuntu on vitalASC?"
date: 2017-09-26
forum: Installation &amp; Upgrades
---

### Post by geekygirl36 on 2017-09-26
Hello!  :)

I have been waiting to get my hands on a computer that I could install Ubuntu on without worrying about warranties.  Now is the time and I am unsure which Ubuntu install I should go with.  My specs are as fallows:

vitalASC JME-2IN1-X511AS
Processor: Intel Atom Z9300 1.8 GHz Processor  (I read the newest release, 16.04.3 LTS, requires 2GHz Dual Core)
RAM: 4GB EMMC
Built-In-Storage (HD?): 32GB Nand(?) Flash

I know this tablet/laptop doesn't have a USB flash drive port, but it does have a Micro SD, Micro USB2 and Micro HDMI Type C.  I am hoping to put Ubuntu on a Micro SD or if I am lucky, be able to put the installer on my main laptop and use the Micro USB2 for install.

Thank you in advance for all your help!

---

### Post by Bucky Ball on 2017-09-26
Welcome. I'd be going for Xubuntu or Lubuntu on that for a better experience. Lighter than Ubuntu. 

Yes, you can use an SD for installing Ubuntu, no problem.

The newest release is actually 17.04 with 17.10 released end of October 2017. Both are interim releases and both have nine months support (17.04 is out of support next January). I'd stick with the long-term support release, 16.04 LTS. This release is very stable and supported until 2019 for Xubuntu and Lubuntu, 2021 for Ubuntu. An excellent place to start. :)

Here's [a link to Xubuntu]("https://xubuntu.org/getxubuntu/") and [here's a bunch of links]("https://duckduckgo.com/?q=install+ubuntu+from+sd") that will help you to install from SD. Good luck and let us know when/if you hit a brickwall! ;)

(PS: If you are going to run a 'live' install of any flavour of Ubuntu booting directly from the SD, best results using a 'Class 10' fast SD. You'll see the class number printed somewhere on the SD.)

---

### Post by geekygirl36 on 2017-09-26
Thank you SO much!  :)  I will look into Xubuntu and Lubuntu to see which one might fit my needs best and thank you for the support tip.

---

### Post by Bucky Ball on 2017-09-26
No probs. Just edited my post. Make sure there's nothing there you've missed!

Post back any further questions/issues once you've explored a bit.

(PS: Just had a further look at that device. Is that an Android tablet? Be careful if so. I'd go for trying to run it off the SD 'live' (choose 'Try *buntu' at the options) rather than installing at this point ... unless you are confident re-installing Android and have a reliable backup of you valuable data in case things go pear-shaped. I have my doubts Ubuntu will run on that device, but no harm trying and hope I'm proved wrong.)

---

### Post by geekygirl36 on 2017-09-26
The computer I am going to install has Windows 10 (and a horrid choice for that system since when it runs, it is super slow and reminds me of dial-up and AOL).  :-D

The only thing I am worried about on the machine is if it has any drivers, so I've contacted the manufacturer (since I couldn't find anything through a web search) to see if there are any.  Other then that, I've ran a few dual boot systems but want to make this system Lubuntu (that seems the best choice from what little research I've done thus far) only since the hardware is lacking to say the least.

Thank you for the tip on the Class 10 SD!

---

### Post by grahammechanical on 2017-09-26
I tried to find some Intel information on the Atom Z9300 but there is not any. So, I checked the specifications of your device. It has the Atom Z8300 which has 4 cores and 2 GB memory

[http://www.vitalasc.com/product/JME-2IN1-X511AS.html](http://www.vitalasc.com/product/JME-2IN1-X511AS.html)

[https://ark.intel.com/products/87383/Intel-Atom-x5-Z8300-Processor-2M-Cache-up-to-1_84-GHz](https://ark.intel.com/products/87383/Intel-Atom-x5-Z8300-Processor-2M-Cache-up-to-1_84-GHz)

Whether you install Xubuntu, Lubuntu or Ubuntu is up to you but you might need to upgrade from the 16,04 version on to 17.10 (released end of October) or 18.04 (released end of April) in order to get all the hardware working.

[https://liliputing.com/2017/03/linux-4-11-brings-improvements-intel-atom-pcs-bay-trail-cherry-trail.html](https://liliputing.com/2017/03/linux-4-11-brings-improvements-intel-atom-pcs-bay-trail-cherry-trail.html)

The 16.04 version is kept up to date with what are called point releases and they bring in the latest Linux kernels and hardware (firmware) support but that happens about six months after a new version of Ubuntu is released. So, Ubuntu 16.04.3 (Recently released) should have the same Linux kernel as Ubuntu 17.04 (released last April). It is Linux kernel 4.10.

[http://www.omgubuntu.co.uk/2017/08/ubuntu-16-04-3-lts-released](http://www.omgubuntu.co.uk/2017/08/ubuntu-16-04-3-lts-released)

Regards

---

### Post by geekygirl36 on 2017-09-26
Thank you SO much!  :)

I think I am going to go with Lubuntu (17.04 if I am understanding the support correctly until I become more comfortable with the sytem) because, at least with Windows 10 running, it is wanting to throw it across the room slow.  lol  Since it is so close to October and I have to check my Micro SDs to see if they are Class 10.

---

### Post by Bucky Ball on 2017-09-26
Well, a plan would be to download create a bootable SD then 'Try Lubuntu' 'live' directly from the SD. This won't change the eMMC in anyway or install anything. You can 'test drive', see it they runs. You will get a possibly noticeable speed improvement when installed to the eMMC as they are pretty fast.

All the *buntu flavours have a live session option, so you could try other flavours and see how they run. I much prefer Xubuntu and not that much heavier than Lubuntu. ;)

---

### Post by geekygirl36 on 2017-09-26
So running the live Ubuntu (any flavor) from a bootable SD will be just like running it fully installed?  I thought with Windows still running would keep that system hog going.  lol  I guess it's like running a dual boot then?

---

### Post by ajgreeny on 2017-09-26
When you run Lubuntu live OS, the system will not have any Windows processes running at all; the two OSs are completely separate so only Lubuntu will be running, nothing else.

---

### Post by geekygirl36 on 2017-09-26
Thank you!  That will be perfect for testing and I can't wait to see if I can do so tonight.  :)

---

### Post by Bucky Ball on 2017-09-26
You will need to boot to the BIOS and tell that to boot from the SD card, NOT the eMMC where you have Windows installed. As mentioned, Ubuntu and Windows don't run at the same time, even when fully installed. They are installed on separate partitions and you boot one or the other.

Something to take into consideration is where you are going to actually install Ubuntu if you go there. Have you got enough free space to install Ubuntu to? An existing partition that you can use for the install? My guess is Win is using it all on one big partition.

---

### Post by geekygirl36 on 2017-09-27
When I got home I checked the computer and it doesn't have a Micro SD slot, so I'm going to get a USB to Mini(?) USB converter.  Unless Windows 10 is different from previous releases, it's F4 I think to get to the BIOS where I can select where to boot from.  (It's been a while since I've had a dual boot or booted anything other than the hard drive.)  I will do a full hard drive wipe for the Ubuntu as soon as I know which flavor I want, so I won't partition anything and as far as I can see, it should have enough space for Lubuntu or Xubuntu.  

As far as IF I get there, don't worry, I will.  lol  It might have taken me over five years to get this far, but I am here.  :)

---

### Post by Bucky Ball on 2017-09-27
Lots of micro SDs come with an adapter as part of the deal. You probably won't need to buy one separately. But if you already have the SD and no adapter ... guess you will. 

The key used to get to the BIOS isn't a Win thing. That's a BIOS thing. (I have Win 10 installed and the BIOS key is F2 from memory.)

Yes, wiping the drive and installing just Lubuntu will make you life easier. More straightforward than a dual-boot. ;)

---

### Post by geekygirl36 on 2017-09-27
I picked up a Micro 16GB thumb drive because finding an adapter was harder and I didn't want to wait two days for Amazon.  LOL!  

Thank you for your help, all of you!!!  (I'm not sure if I should solve this post or save it for when I finally get an Ubuntu flavor running.)  :-D

---

### Post by Bucky Ball on 2017-09-28
You could probably mark as solved, as the original question is solved, and start a new thread with a descriptive title for any further questions/problems with installing. You can post a link to that here when you mark this as solved if you like. ;) 

Good luck. :)

---

### Post by geekygirl36 on 2017-09-28
Thank you Bucky and all the others that helped!!!  :)

(Marking as solved.)

---

