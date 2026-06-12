---
title: "Installing Ubuntu on Samsung NP-Q1"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by TechViking on 2013-05-20
Hi Everyone,

I seem to be having real trouble getting Ubuntu to install onto my Samsung Q1 when I try to install or even run a live session I get an error telling me my CPU's architecture isn't supported. I know that the architecture is McCaslin, I have managed to install Debian using the multiarch installed but I would prefer Ubuntu as its my OS across the board.

Thanks,

TechViking

---

### Post by Bucky Ball on 2013-05-20
Are you attempting to use 64bit OS on a 32bit machine by any chance?

* Just having a quick look and looks like a mini-mobile PC with 800Mhz CPU so if you are trying to install the 64bit try the 32. Incidentally, your details say you are using 11.04. If so it has reached end of life and is no longer supported. Just thought I'd mention. ;)

---

### Post by TechViking on 2013-05-20
Thanks for the quick response no I am using a 32bit version I have tried 13.04 and 12.10. neither of which worked :/

---

### Post by sanderj on 2013-05-20
> **TechViking said:**
> Hi Everyone,

I seem to be having real trouble getting Ubuntu to install onto my Samsung Q1 when I try to install or even run a live session I get an error telling me my CPU's architecture isn't supported. I know that the architecture is McCaslin, I have managed to install Debian using the multiarch installed but I would prefer Ubuntu as its my OS across the board.

Thanks,

TechViking

Can you post the exact error message? Maybe make a picture of it, and post that? I think that would help. For example: since 12.04 PAE is needed

---

### Post by Bucky Ball on 2013-05-20
You might even want to try 12.04 LTS. That is the current long-term support release and supported until April 2017.

---

### Post by TechViking on 2013-05-20
hi thanks that is the one it I don't have the machine to hand at the moment but it says something about PAE and says my CPU isn't Supported I know it can work because I have seen videos with the same model running it :P

---

### Post by sanderj on 2013-05-20
> **TechViking said:**
> I know it can work because I have seen videos with the same model running it :P

running what?

Did you google "ubuntu pae"?

---

### Post by TechViking on 2013-05-20
running Ubuntu 13.04 and I did but I couldn't find anything useful unless I have been looking in the wrong places.

---

### Post by sanderj on 2013-05-20
> **TechViking said:**
> running Ubuntu 13.04

Ubuntu 13.04 on a non-PAE CPU? If you saw that somewhere, please come with the URLs. AFAIK that is something for real hackers; it means replacing the kernel.

Furthermore Ubuntu 13.04 on 9 year old hardware wouldn't be too great performance.

HTH

---

### Post by TechViking on 2013-05-21
OK then is there an older version/different distro you could suggest. I have six of them in the office and they are direly slow on XP but it seems a shame to just throw them away when they could work ok as a web surfing machine :P I do have debian installed I may just stick with that but if you have a better suggestion... it needs to be pretty user friendly as many of the staff will be completely new most won't probs know linux exists :P

---

### Post by sanderj on 2013-05-21
1) [https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions) shows that the supported Ubuntu Desktop versions are 12.04 and more recent.
2) Since Ubuntu 12.04, PAE is required (unless you're a real hacker and can replace kernels)

So, logically, you can only conclude from the above that there is no supported Ubuntu Desktop version for your non-PAE hardware.

If Debian works for you, stay on Debian.

---

### Post by Bucky Ball on 2013-05-21
Not sure why you keep insisting you need to be an expert hacker to replace the kernel. It's easy. One command and a reboot should do it.

[https://help.ubuntu.com/community/EnablingPAE#Ubuntu_10.04_LTS_.28Lucid_Lynx.29_to_Ubuntu_12.04_LTS_.28Precise.29](https://help.ubuntu.com/community/EnablingPAE#Ubuntu_10.04_LTS_.28Lucid_Lynx.29_to_Ubuntu_12.04_LTS_.28Precise.29)

That should just add the PAE kernel to you list when you boot. Choose it or choose the kernel you are currently using. You can install any kernel you like easily, even the 13.04 kernels and beyond, in 12.04 LTS (and the other supported releases, too).

* Note: 12.04 will install the PAE kernel automatically if it detects more than 3Gb of RAM (and you have an internet connection happening).

---

### Post by sanderj on 2013-05-21
> **Bucky Ball said:**
> 
That should just add the PAE kernel to you list when you boot.

The OP is looking for the opposite: his/her 9 years old CPU is not PAE-enabled, so he/she need a non-PAE kernel in a supported Ubuntu ...

---

