---
title: "root file system undefined"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Chelovek on 2011-07-26
When I bought my computer it had Windows vista installed. I erased it and installed Windows XP. My sytem got crushed by a virus, hence I installed ubuntu 8.04. For possible fear of destroying my systems, I installed ubuntu 11.04 desktop edition alongside Ubuntu 8.04, but without defining the root file system. I am afraid I have erased OS's on my computer too many times.
 
May you please advise me on what to do to have the root file system defined.

---

### Post by haqking on 2011-07-26
> **Chelovek said:**
> When I bought my computer it had Windows vista installed. I erased it and installed Windows XP. My sytem got crushed by a virus, hence I installed ubuntu 8.04. For possible fear of destroying my systems, I installed ubuntu 11.04 desktop edition alongside Ubuntu 8.04, but without defining the root file system. I am afraid I have erased OS's on my computer too many times.
 
May you please advise me on what to do to have the root file system defined.



you mean you receive an error message when trying to boot ? if so is it with both versions in your dual boot


you could

mount an appropriate partition as /

however that should of been done during install ?

maybe i am not understanding your question ?

---

### Post by Chelovek on 2011-07-26
I mean 11.04 is installed already, but without the root system. there is an X on the root folder.
By the way, can erasing both 8.04 and 11.04 and reinstalling 11.04 be dangerous for my system?

---

### Post by westie457 on 2011-07-26
> **Chelovek said:**
> I mean 11.04 is installed already, but without the root system. there is an X on the root folder

I think that means it is locked IE no access at all.
 Possibly the only way around this is to reinstall to the same partition without formatting and this time remembering to set the '/' root.

---

### Post by coffeecat on 2011-07-26
> **Chelovek said:**
> I mean 11.04 is installed already, but without the root system. there is an X on the root folder.

I think you are muddling different usages of the word "root". If you have installed Ubuntu, you will have a filesystem in the "root" partition. This is quite different from the root user and the /root folder, which is root's (user) home folder. And it's normal to have an X showing on the root folder in a normal system when you view the filesystem in a nautilus browser as an ordinary user. That's because you have to be root (user) to be able to open the /root folder.

Please describe exactly what your problem is. Can you boot into Ubuntu 11.04, or are you getting an error message?

---

### Post by Chelovek on 2011-07-26
my problem is when trying to mount the matlab ISO file for installation I get this message:
only root can do that

---

### Post by Chelovek on 2011-07-26
[QUOTE=Chelovek;11087524]my problem is when trying to mount the matlab ISO file for installation I get this message:
only root can do that 
thats why I thought maybe I didnt define /root system

---

### Post by coffeecat on 2011-07-26
> **Chelovek said:**
> [QUOTE=Chelovek;11087524]my problem is when trying to mount the matlab ISO file for installation I get this message:
only root can do that 
thats why I thought maybe I didnt define /root system

You need root (user) privileges to do whatever you're trying to do. This has nothing to do with other meanings of the word root. Tell us what you are trying to do and then someone can give you the right commands.

---

### Post by dino99 on 2011-07-26
no, thats mean you need to be root : eg use "sudo"

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

and your install should be something like:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Chelovek on 2011-07-26
I want to install matlabR2009a on ubuntu 11.04

---

### Post by coffeecat on 2011-07-26
> **Chelovek said:**
> I want to install matlabR2009a on ubuntu 11.04

Kindly advice: no one is going to help you if you won't do some of the work yourself. I presume from what you said before that you've downloaded an ISO. Did it come with instructions? A readme? Where did you get it? Link?

---

### Post by dino99 on 2011-07-26
something newer that you can easily find yourself :)

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

