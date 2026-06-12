---
title: "Trying to install an ASUS AC53 Nano w/o wifi card."
date: 2017-10-24
forum: MINT
---

### Post by pitdoug1998 on 2017-10-24
SUPER new to 'all this' (high level iMac/Apple and MS user) so please answer with the 'how to' as opposed to simply 'do _____'. 

Okay I've gotten so far as to get the machine to recognize the adapter using lsusb but that's it. I need an A-Z walk through on installation please. This old Dell OptiPlex 745 does not have a wifi card and I'm not dual booting. 

Thanks,
Doug

---

### Post by wildmanne39 on 2017-10-24
*Thread moved to **Networking & Wireless for better a better fit **.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by QIII on 2017-10-24
Hello!

Please use the default font and weight unless you need to draw attention to a specific part of your post.

Also "** Please Help! **" in a title is generally perceived as demanding.  It is assumed that if you are posting in a help forum that you need help.

Cheers!

---

### Post by pitdoug1998 on 2017-10-24
Thank you!

[https://pastebin.com/q5ff8ydU](https://pastebin.com/q5ff8ydU)

---

### Post by jeremy31 on 2017-10-24
Did you have issues following [https://forums.linuxmint.com/viewtopic.php?f=90&t=255594](https://forums.linuxmint.com/viewtopic.php?f=90&t=255594)

---

### Post by pitdoug1998 on 2017-10-24
My ex was demanding...... Gotcha' though and thank you.

---

### Post by jeremy31 on 2017-10-24
Post any issues you had, either here or on the Linux Mint forums or both

---

### Post by wildmanne39 on 2017-10-24
Jeremy I will let you handle this one since you have already helped him and the answer is in the thread on the other forum, if you want you can move this to our linux mint forum since it is about mint but I just moved it here before I knew it was about mint so I am going to leave it so things do not get confusing for the user.

---

### Post by pitdoug1998 on 2017-10-24
Well that post got to me to the point of the adapter showing in terminal but that was as far as I got. Hence just starting from scratch here. Lord knows I'm missing something obvious.

More confusion I'll kindly pass on!! Thank you though.

I read the whole thread several times on the Mint forum page and I didn't get an answer that allowed me to connect to my wifi.

---

### Post by jeremy31 on 2017-10-24
Post new wireless script results

---

### Post by pitdoug1998 on 2017-10-24
[https://pastebin.com/q5ff8ydU](https://pastebin.com/q5ff8ydU)

---

### Post by jeremy31 on 2017-10-24
Lets try a different approach
```
sudo apt-get install git build-essential linux-headers-generic
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu
make
sudo make install
```
Reboot

---

### Post by pitdoug1998 on 2017-10-24
I've rebooted. Rerun the and post wireless scripts?

[https://pastebin.com/5uFfJUcs](https://pastebin.com/5uFfJUcs)

---

### Post by jeremy31 on 2017-10-24
Go into BIOS and see if Secure Boot is enabled, that will prevent the module from loading

---

### Post by pitdoug1998 on 2017-10-24
No feature on these Win 8 machines for secure boot disable/enable.

At least not these Dell OptiPlex machines.

---

### Post by jeremy31 on 2017-10-24
What happens when you ```
sudo modprobe -v 8822bu.ko
```
With the USB wifi card inserted?

---

### Post by pitdoug1998 on 2017-10-24
Is there a better distro to enable the use of a wifi adapter? I'm really a little lost with all this and I have to either scrap the Linux idea and go back the MS which I don't want to do or buy an iMac for work. ALL this is about having to have a pc at work that is wifi friendly and frankly my time is up this week on this Linux project because I have to have something Monday.

modprobe: FATAL: Module 8822bu.ko not found in directory /lib/modules/4.4.0-97-generic


I feel a little ridiculous now but was the adapter supposed to be out this whole time?

---

### Post by jeremy31 on 2017-10-24
It shouldn't matter if the adapter was plugged in or not, what does
```
locate 8822bu.ko
``` 
result with

---

### Post by pitdoug1998 on 2017-10-24
Not a thing sir.

---

### Post by pitdoug1998 on 2017-10-24
Jeremy is there an adapter that works pretty much straight out of the box? I'm on a strict time frame on getting this thing up and running and I'd hate having to buy a machine for work when I have a perfectly good one here.

---

### Post by pitdoug1998 on 2017-10-25
Also is this an issue with the current distro I have installed? 

And I have an N300/WNA3100 with the Windows driver CD but couldn't figure out how to download then use the drivers. As I stated I need to either have wifi on this ready for work Monday or I need to buy another machine that has a wifi card installed but that seems like a waste of money and I really want to learn the Linux OS!!!

---

### Post by jeremy31 on 2017-10-25
pitdoug1998, the Tp Link Wn722n version 1 works without issues in Linux, it is a 150 Mbps but it works

---

### Post by pitdoug1998 on 2017-10-26
I'm currently trying to install and use WINE so I can install Brother printer and these adapters. Am I even remotely on the right path? As I read over the comments I didn't see anything about installing drivers but I'm obviously clueless in this enviroment but I refuse to give up and use crap MS products.

---

### Post by praseodym on 2017-10-27
[https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

Try this one

---

### Post by rdiaz75 on 2018-05-10
Hello, I got here because I upgrade to Ubuntu 18.04 LTS from Ubuntu 17.10 and needed the driver for the Asus USB-AC53 Nano. I tried the one made by jeremy31 that worked befor but not with the new kernel. But I found the necessary changes I needed to make to the code [here]("https://github.com/aircrack-ng/rtl8812au/commit/f221a169f281dab9756a176ec2abd91e0eba7d19").
Thanks for the driver jeremy31!

---

### Post by rdiaz75 on 2018-05-10
> **rdiaz75 said:**
> Hello, I got here because I upgrade to Ubuntu 18.04 LTS from Ubuntu 17.10 and needed the driver for the Asus USB-AC53 Nano. I tried the one made by jeremy31 that worked befor but not with the new kernel. But I found the necessary changes I needed to make to the code [here]("https://github.com/aircrack-ng/rtl8812au/commit/f221a169f281dab9756a176ec2abd91e0eba7d19").
Thanks for the driver jeremy31!
Unfortunately the driver compiled but it didn't worked :-/

---

### Post by jeremy31 on 2018-05-10
Doesn't ```
sudo apt-get install rtl8812au-dkms
```
Work anymore?

---

### Post by rdiaz75 on 2018-05-10
> **jeremy31 said:**
> Doesn't ```
sudo apt-get install rtl8812au-dkms
```
Work anymore?

I had already installed this one and it worked :
[https://github.com/MeissnerEffect/rtl8822bu](https://github.com/MeissnerEffect/rtl8822bu)

But thanks for answering, also your previous posts helped me a lot :guitar:

---

