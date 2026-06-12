---
title: "grub setup question"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by blastradius on 2006-07-01
How do I re-install Grub?  Everytime I install Ubuntu I get a seperate entry In Grub so although I only have one Windows partition and one Ubuntu partition I have 4 Ubuntu entries and 1 windows listed in Grub, how do I get Grub to run update itself so that it only shows my current setup.

Thanks in advance

---

### Post by aysiu on 2006-07-01
You don't need to reinstall Grub for this.

You probably just updated your kernel. So you can uninstall the old kernel, if you want. Use your favorite package manager (Synaptic or Adept) and search for *linux-image*. Find the old image and uninstall it.

---

### Post by Sean-Michael on 2006-07-03
I also have this problem, I have my windows OS and the my one Ubuntu OS but I have many entries for systems,

My question is how do I know what to uninstall?  When I run Synaptic I have a total of 3 items to "uninstall" and am scared to ruin my Linux system by guesing what to do lol, 

Thanks in advance for any help!

---

### Post by aysiu on 2006-07-03
You should be rightly scared. If you uninstall the wrong ones, your system will be borked.

Basically, you should make sure you're currently booted into the most recent kernel and then uninstall the older kernels.

"Most recent" means the kernel with the highest version number. "Older" means the kernels with the lower version numbers.

If you're in doubt, post a screenshot of the Synaptic search for *linux-image*. I or someone else will help you sort out which ones to uninstall.

---

### Post by Sean-Michael on 2006-07-03
Thankyou for the reply, here is what I have listed as installed from the top of the list to the bottom'

1. linux-image-2.6.15-23-386  Installed Version 2.6.15-23.39

2. linux-image-2.6.15-25-386  Installed Version 2.6.15.23

3. linux-image-386  Installed Version 2.6.15.23

So, I'm thinking this means that 2 & 3 are the ones I could uninstall and keep number one,  sould one be kept in case I have a problem with the latest? Lol  I have a hard time even telling what is the newest...  I'm thinking its number 2 in my list now...  having the highest linux-image number.

Thanks again'

---

### Post by aysiu on 2006-07-03
No, I would uninstall only #2. Leave #3 in there.

---

### Post by Sean-Michael on 2006-07-05
Say, I made a typo when I wrote what was listed for linux-image  the error is in #2 where the actual listing should read,

2. linux-image-2.6.15-25-386 Installed Version 2.6.15-25.43

Sorry for the typo, can I still remove #2?

---

### Post by aysiu on 2006-07-05
No, sorry--you should remove #1 instead.

---

### Post by Sean-Michael on 2006-07-05
Perfect, Like i said it was my typo but I've uninstalled that linux-image and as it turns out, I think I was booting into the older version...

Thankyou again for your time, people like you are very helpful to new linux users like myself!

---

