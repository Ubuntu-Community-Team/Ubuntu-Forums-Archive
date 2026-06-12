---
title: "ChrUbuntu"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by bram6 on 2014-10-10
Dear,

I've recently purchased a Samsung Chromebook Series 3 (ARM). I was satisfied with everything my Chromebook could do, but it wasn't optimized for school because it didn't have a stable connection. That's why I decided to run Ubuntu on it. I know it's an ARM Device, but I can still run everything I want with [http://eltechs.com/product/exagear-desktop/](http://eltechs.com/product/exagear-desktop/). So now I've installed ChrUbuntu several times, but I couldn't get the flavor I wanted. I want the Unity version with Ubuntu 12.04 or later. On my ARM device I kept getting the xUbuntu version, which I don't like that much. I considered using Crouton, but I don't think it's possible to change the Linux Kernel with the Crouton OS. Best would be if I could get rid of whole Chrome OS and make it a full Linux device, but that's not possible. So can anyone tell me which flavor to take?

This is directly copied from the website, and this is what I used.

[B]curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd xubuntu-desktop lts

this will install Xubuntu and the latest LTS release (12.04.3 as of writing) rather than a 13.10 Unity desktop. Some possible flavor alternatives to Unity are:

[B]default  (ubuntu-desktop on x86, xubuntu-desktop on arm)
[B]kubuntu-desktop
lubuntu-desktop
xubuntu-desktop
edubuntu-desktop
ubuntu-standard    (no GUI installed)

some possible versions are:

[B]lts -- latest LTS Ubuntu release, 12.04.3 as of this writing
[B]latest -- latest official release, currently 13.10
[B]dev -- unstable development Ubuntu release, experts only! If this breaks, don't be surprised
[B]12.10 -- Ubuntu 12.10 release

[/B][/B][/B][/B][/B][/B][/B]In other words; What command do I have to run to install the Unity Ubuntu 12.04+ flavor so I can run ExaGear Desktop on my ARM Chromebook?

Yours sincerely,
Bram.

PS: I'm not sure wether this is the right sub-forum or not, but I think it is.
PPS: Sorry for my poor English and my bad knowledge of Linux, I'm 13 years old and my main language is Dutch. (No one could help me on the Dutch fora, so I tried it here.)


[B][B][B][B][B][B][B]


[/B][/B][/B][/B][/B][/B][/B]

---

### Post by Vladlenin5000 on 2014-10-10
I cannot help with the desktop environment because I have zero experience with those chomebooks. I don't know what can and what can't be installed but...
Reading the system requirements for ExaGear Desktop nothing there is saying it is dependent on Unity. Requiring *Ubuntu 12.04 or later *doesn't mean it has to be the standard Ubuntu (with Unity). As far as I can tell it's just a specialized VM and as such it cannot have dependencies on the desktop environment.

> Sorry for my poor English and my bad knowledge of Linux

What??? Your English as shown in your post above is better than the one of many natives I know.
And "bad knowledge of Linux"???? C'mon, don't sell yourself so short. What you already did requires a level of expertise that most users don't have. I know people running Linux (Ubuntu mostly) for many years that still don't know the differences between x86, x86_64 and ARM...

---

### Post by bram6 on 2014-10-10
Thanks. But I just want to make sure I don't blow it, so that's why I'm taking Unity. Also I like the visual of Unity better. But if there's no other option I can take the xUbuntu version ofcourse, but first I want to know if I can get Unity to work.

Regards,
Bram.

---

### Post by Vladlenin5000 on 2014-10-10
> **bram6 said:**
>  I like the visual of Unity better. 

A big +1
I couldn't agree more. And it's not only beautiful but productive as well. 


Regarding your initial question and keeping in mind I still don't know what can and what can't be installed in such environment, I would strongly recommend one of the supported releases - 12.04 or 14.04 - and nothing else, regardless of the choice of desktop.

---

### Post by bram6 on 2014-10-11
The problem is; I don't see Unity on the list.

[B][B][B]kubuntu-desktop
lubuntu-desktop
xubuntu-desktop
edubuntu-desktop
ubuntu-standard (no GUI installed)


[/B][/B][/B]

---

### Post by Vladlenin5000 on 2014-10-11
I *think* you can go for the *ubuntu-standard* and then install Unity:
```
sudo apt-get install --no-install-recommends ubuntu-desktop  <- basic
-or-
sudo apt-get install ubuntu-desktop  <-full
```
You need to login as usual but in a CLI (command line interface) and keep in mind the password won't be echoed, ie, nothing shows while you're typing the password, no dots or "*", and that's normal.

Beware of:
1. It may fail. Please note down the error messages, post here and we'll try to sort them out.
2. Depending on what you want to do with the chromebook, Unity might be excessive. Unity will certainly use more RAM than any other DE and it may impact other hardware resources too. The general consensus points to XFCE (Xubuntu) as the best compromise between a modern* DE and the usage of resources in a resources limited machine like the chromebook.


* Yes, I know we both disagree but some people simply can't get along without a start menu...

---

### Post by bram6 on 2014-10-12
> **Vladlenin5000 said:**
> I *think* you can go for the *ubuntu-standard* and then install Unity:
```
sudo apt-get install --no-install-recommends ubuntu-desktop  <- basic
-or-
sudo apt-get install ubuntu-desktop  <-full
```
You need to login as usual but in a CLI (command line interface) and keep in mind the password won't be echoed, ie, nothing shows while you're typing the password, no dots or "*", and that's normal.

Beware of:
1. It may fail. Please note down the error messages, post here and we'll try to sort them out.
2. Depending on what you want to do with the chromebook, Unity might be excessive. Unity will certainly use more RAM than any other DE and it may impact other hardware resources too. The general consensus points to XFCE (Xubuntu) as the best compromise between a modern* DE and the usage of resources in a resources limited machine like the chromebook.


* Yes, I know we both disagree but some people simply can't get along without a start menu...

I log in as user Chronos, no password needed. I didn;t use the sudo apt methode, because I dont think you can add repositiries on a Chromebook. I think it would look like this then:
```
curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd ubuntu-desktop
```
And if Unity is more excesivve... I only have 2 GB RAM. So if the Ubuntu Desktop won't work the easy way, I'll guess I'll just install XFCE ](*,). And if I can install Unity correct and it turns out to be too slow I'll take XFCE aswell... Let's hope it works in one time and it isn't too slow! But this how the command would look:
```
curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd ubuntu-desktop
```

Regards,
Bram.

---

### Post by Vladlenin5000 on 2014-10-12
Interesting... I just learned a new thing. Thank you.

PS - You're now only 2 posts short of gaining the full forum features.

---

### Post by bram6 on 2014-10-12
What features?

Bram

---

### Post by Vladlenin5000 on 2014-10-12
Some relevant information can be found here: [http://ubuntuforums.org/showthread.php?t=2034393](http://ubuntuforums.org/showthread.php?t=2034393)
It boils down to being able to edit your own profile extensively and having the possibility to add friends, etc.

---

### Post by bram6 on 2014-10-12
It is currently installing, with the command above. I Will let you know what happens after completion!

Regards,
Bram

---

### Post by bram6 on 2014-10-13
Okay... Unity didn't have any GUI. Not even a console. So I installed XFC. But that is so ugly... I think I will install Crouton, but the question is; can I change my linux kernel when using Crouton?

Bram

---

