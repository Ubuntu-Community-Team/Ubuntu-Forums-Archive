---
title: "dual boot windows 7 and ubuntu 10.0.4 windows installed with raid 0"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by nima352000 on 2010-07-31
hey guys , i was trying to dual boot ubuntu on my desktop which has windows 7 already installed on it with raid 0 . i have 2 500GB hard drive and when i boot from cd and try to install ubuntu it only detect one of my hard drives and it said i only have 500GB and there is no OS installed on this machine ! i look online but i couldn't find any solution ! anybody can help me here ?
thanks in advance

---

### Post by ronparent on 2010-07-31
Installing on a raid in Ubuntu is daunting and requires extra work. What is your level of experience? Do you have an extra non raid drive (even an external drive) sitting around? I can talk you through this if you want to proceed but it is not a casual stick the cd in and proceed.

---

### Post by nima352000 on 2010-08-01
yes i have an 350GB external hard drive here , is it possible to use that instead ?

---

### Post by nima352000 on 2010-08-01
oh and yea , im not really good with linux , i've been a windows user since for ever , but i'm ok in learning new thing(EE student)

---

### Post by nima352000 on 2010-08-02
helloOooooOO!!! ok well i guess it is end of it ! as usual no one wants to say something

---

### Post by ronparent on 2010-08-02
Your external drive is your best option for a new user. With a bit of learning you might want to try the raid0 install later (less chance of destroying the win7 install).

---

### Post by nima352000 on 2010-08-02
thanks for reply ,
here is what i did last night , i have a seagate free-agent external drive 500GB , i made a partition of 50GB with windows 7 , then boot from live cd and start installation , i choose my external as where i want to install ubuntu and the select the option that use the largest empty space, and at the next windows i choose to install boot loader on /dev/sdc (it was in my case because i have sda and sdb which is my two 500GB internal drive raid 0, but after selecting that i still got an error "faild to unmount partition" 

screenshots are below . i hope i was clear

---

### Post by nima352000 on 2010-08-02
and i should mention i have tried the same method installing on USB flash drive , and then select boot from CD/DVD>USB>hard drive in bios and it worked just fine , i was able to boot and use ubuntu from USB flash drive , but it is only 8GB and it is kind of slow , i was hopping that external hard drive will be faster right ? (just like internal HDD ??)

---

### Post by ronparent on 2010-08-03
I don't see anything in the screen shots that would be or any help - very good way to clearly illustrate your situation by the way. 

The only thing I can think of is to do the installation with the raid unplugged (be sure to mark which cable belong to which drive/port). The boot loader would then be installed automatically to the external drive - with the raid connected and the external drive as boot you would only need an update-grub (see [http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html)) to get windows on the raid into the grub menu.

---

### Post by nima352000 on 2010-08-03
thanks for your suggestion , i ended up buying a new 320GB external USB HDD, and the installation was a breeze. i guess there is a problem when i was trying to install it on the partition on external drive , but if i use the whole drive , it was no problem , so now every time i wanna boot to ubuntu i have to plug my external drive and then restart my pc. it works great . very fast and smooth. i was able to get everything to  work including my mx5500 mouse and keyboard, printer , and all the desktop effects. work like a charm :-)
thanks for all your help guys

---

### Post by ronparent on 2010-08-03
Glad to hear your solution. Have fun.

---

