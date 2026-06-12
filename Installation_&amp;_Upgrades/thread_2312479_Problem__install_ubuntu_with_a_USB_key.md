---
title: "Problem : install ubuntu with a USB key"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by Agouha on 2016-02-04
Hello,

I'm trying to install Ubuntu on my computer with a dual boot with Windows 10.

I have downloaded the Ubuntu ISO.
I have formated my USB key then I putted the ISO in the key with the unetbootin software.
I have formated my hard disk like it : 25 Go free, 200 Go with Windows in it, 235 Go for the Linux installation and 5Go for the swap.
I have rebooted my computer and booted on the USB key. I have installed Ubuntu.

The installation finished, I rebooted the computer.

Now I can click on unbuntu, options for Ubuntu, memory test (x2) and Windows Recovery.
When I click on unbuntu, it launch then black screen.
When I click on options for Ubuntu, I have the first choice normal and the second choice recovery. The first choice do the same as when I click on Ubuntu.

I think the problem is with the hard disk because I tried to install the ISO two times and install it on the USB key two times.

If you need more information or have an idea of what I can try, I will be thankfull.

---

### Post by yancek on 2016-02-04
You neglected to mention "which" windows version you have installed.  Sicne microsoft has been selling operating systems for over 30 years, that's important.  Major changes have also been made with windows 8 and newer.   If you are using windows 8 or newer, take a look at the Ubuntu documentation at the site below and post back as to the type of installation you have done, UEFI or MBR.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2016-02-04
I would like to know the hardware specification of this machine. Especially, information about the video adapter. And also to know the version of Ubuntu installed. Is it Ubuntu 14.04.3 or Ubuntu 15.10.

Does Windows still load? What happens when you try Advanced options for Ubuntu and then select Resume at the recovery menu? When you used Try Ubuntu before installing, did you get a black screen then?

Regards

---

### Post by Agouha on 2016-02-05
Thank you for your answers yancek and grahammechanical.

I want to join you the general informations about my system :
[http://hpics.li/1d56a2f](http://hpics.li/1d56a2f)

I tried to install Ubuntu version 14.04.3, I took it on the official website.

Windows work because I'm actually on the computer. At the boot menu, I tried to do the recovery mode of Ubuntu but after that there was a list choice and I didn't already tried anything because I'm new to Ubuntu I prefered to ask for your help.

I'm not sure to understand your last question, grahammechanical. If you ask if I tried Ubuntu before installing him the answer is not. I didn't tried the "live" mode.  I installed it first.

If you need more information or I didn't answered correctly, feel free to tell it

---

### Post by sudodus on 2016-02-05
It is a good idea to try Ubuntu before installing it, and I suggest that you do it now and tell us the result :-) See this link (and links from it)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Agouha on 2016-02-05
Hello sudodus,

I'm going to work in a little time so I won't have the time to do it. I'll see your post and try it in the afternoon.

Thank you for your answer

---

### Post by Agouha on 2016-02-06
I have find the problem in internet :

"This usually happens because you have an Nvidia or AMD graphics card, or a laptop with *Optimus* or switchable/hybrid graphics, and Ubuntu does not have the proprietary drivers installed to allow it to work with these."

If you have the same problem and are in this case, check this website : 

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Go to the section "Black/purple screen *after* you boot Ubuntu for the first time"
This is how I solved it.

---

