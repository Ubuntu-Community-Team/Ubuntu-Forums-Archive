---
title: "Which laptops are compatible with Ubuntu?"
date: 2017-10-22
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2017-10-22
I have, over the years, installed Ubuntu onto three different makes and models of laptops: an Eee PC, Samsung, and one other. I never had a problem.

I have spent over 20 hours trying to install from a USB onto a HP with zero success. I cannot even get Grub to install. Executing grub-install /dev/sda failed. This is a fatal error.

Moreover, the installation did not discover any wireless networks. Perhaps it does not like the Realtek wireless card?

Is there a way to learn in advance which laptops actually support Ubuntu? Which chipsets do and do not work? I am prepared to buy a new laptop but am now worried that I won't be able to install 16.04. 

I cannot believe that almost ten years ago I simply installed 10.04 (or whatever it was) and it just worked. Now with a far more modern computer I cannot install Grub and Ubuntu does not find my wireless networks. I have spent all my spare time of the past few days on this matter.

---

### Post by ubfan1 on 2017-10-22
I have found the linlap.com site useful.  In your case, I'd read up on UEFI, then google HP UEFI, to see how the vendor messed up the standard, and requires things like specific names on the bootloaders.

---

### Post by ajgreeny on 2017-10-23
See the **Systems that only boot Windows from UEFI.** section of [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) which may help you out.

HP is not the only problem make as you will see, but as I have said before **DO NOT PANIC,** there are workarounds that can get Ubuntu installed after a bit of editing of file names, etc etc.

---

### Post by sudodus on 2017-10-23
I have noticed that computers that are a couple of years old usually work well with linux (the linux kernel and its drivers), which means that they work well with standard Ubuntu and the Ubuntu community flavours too (Kubuntu, Lubuntu, ... Xubuntu).

New computers often need new versions of linux that provide hardware drivers for new hardware. Sometimes it takes longer time to find out how to manage some particular hardware or UEFI/BIOS system, particularly when the hardware manufacturer or vendor is not interrested in linux.

That said, I have good experience of middle-aged enterprise class HP computers (reconditioned Elitebooks with Intel i5 of second and third generation), that can be bought second-hand for a competitive price compared to new consumer class computers. Such computers can work several years with Ubuntu and Kubuntu and after that with a lighter desktop environment (Lubuntu, Ubuntu Budgie, Ubuntu MATE, Xubuntu) for still more years.

I don't know about Elitebooks with Intel i5 of fourth generation, but I have a Dell Latitude E7240 with Intel i5 of fourth generation, and it works very well for me with Ubuntu 16.04.1 LTS as well as with newer versions of Ubuntu.

[hr][/hr]
If you have problems with a particular computer, you can start a new thread and get help to make Ubuntu work with it. In that case, please write a good descriptive title and please specify your computer

- Brand name and model
- CPU
- RAM (size)
- internal drive (size)
- graphics chip/card
- wifi chip/card

---

### Post by mastablasta on 2017-10-23
System76, Zareason (ubuntu preinstalled), HP business models ([https://www.suse.com/products/desktop/hp/](https://www.suse.com/products/desktop/hp/)), Dell Business models (Vostro), some home models (inspiron, Latitude), developer (XPS13) , Lenovo Thinkpads...

---

### Post by Tadaen_Sylvermane on 2017-10-23
Dell consumer models are good. Mine is a 2013 and I was able to install as soon as I bought it, never even booted the pre-installed Windows. Swapped in an ssd and away I went, no problems. Dell is on my list of good to go oems

---

### Post by yoshii on 2017-10-23
I only use used HP computers, but I admit that from time to time sometimes I can't get the DVD-ROMs to work at all.  It depends upon the distribution version, I think.  For example, 14.04 LTS worked just fine, but the versions after were kinda tricky.  Eventually I just gave up and started using flash drives instead.  uNetBootin has been known to not work all the time, so I changed to Rufus Portable (Windows) and Etcher (Linux) to create bootable .ISOs.  Some other distros I tried wouldn't boot at all either, and it might be because of some NVIDIA hardware even though I try to only have Intel.  A few of the HP models have both Intel and NVIDIA hardware and NVIDIA used to have a bad reputation for compatibility issues within the recording engineering community.  

I don't buy Dells anymore at all because a few of them that I used to own died of overheating.  When I took them apart to investigate, I saw that they weren't designed to dissipate heat very well at all.  

But I do find that if a laptop can boot a decent version of Puppy Linux or TahrPup, then it can be made to boot up SOME type of Linux eventually.  I've never had any problems with Puppy Linux or TahrPup, and those downloads are only about 200 MB, which is a lot more manageable.  You just have to make sure you get a type of Puppy Linux which has the wifi drivers.  Luckily TahrPup is pretty good about that.

---

