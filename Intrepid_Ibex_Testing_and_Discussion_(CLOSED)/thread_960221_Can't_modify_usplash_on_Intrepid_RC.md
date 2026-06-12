---
title: "Can't modify usplash on Intrepid RC"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by johnlocke2342 on 2008-10-27
Hi.
I was hesitating on whether or not waiting next week to install the final release of Intrepid, but my new graphics card which wasn't correctly detected on Hardy made the decision, and it works fine on Intrepid RC. Everything works fine, I customized my system as usual, but when I tried to install a new usplash theme, it didn't work. I tried others, I have the same problem and I'm forced to boot in verbose mode, unless I select the original Ubuntu/Kubuntu one.
I tried using startup-manager and manually, none works
Any help, please?

Thanks in advance.

---

### Post by ogregore on 2008-10-27
John,

I had the same problem.  I looked  on Gnome-Look and found some usplashes that included the source, downloaded those, recompiled the source for the Intrepid kernel and viola, I have matching usplash (although still doesn't show on shutdown, haven't figured that out yet).

I am sure once Intrepid is final most of the usplash designers will probably be uploading intrepid specific precompiled versions.

Cheers
Ogre

---

### Post by johnlocke2342 on 2008-10-27
Thanks, but when I said I tried to install manually, I meant "from source".
But I can't understand why, the "make" command rarely works for me.:(

PS: I'm french, it's "VOILA", "VIOLA" means another completely different thing...:biggrin:

---

### Post by ogregore on 2008-10-27
You may not have one of the necessary "dev" files installed, do you get any error messages when you try to compile?

PSS- I am not French, however it was a typo versus ignorance :).

Cheers
Ogre

---

### Post by johnlocke2342 on 2008-10-27
What dev files do you mean ? Gcc ones?

PS: I know it was a typing error but this word is so frequently typed with this error on english-speaking websites, it's disturbing when you know what this means in french...

---

### Post by ogregore on 2008-10-27
I installed libusplash-dev and I think in doing so it may have installed one or two other lib files from dependencies, don't remember for sure.

If I remember correctly, when I first tried to compile one it gave me an error 17 or something like that.  At a minimum you will need libusplash-dev.

Cheers
Ogre

---

### Post by johnlocke2342 on 2008-10-27
Thanks mate, it works !!!

---

### Post by ogregore on 2008-10-27
Glad I could help - that's what it is all about.:smile:

Cheers
Ogre

---

### Post by Cifra on 2008-10-28
I have the same problem, but I don't really know how to compile a theme. Can someone post the instructions step by step for us ninnies? :D

Thanks in advance

---

### Post by johnlocke2342 on 2008-10-28
It's very simple: First, you have to install libusplash-dev.
```
sudo apt-get install libusplash-dev
```Then, you open a terminal and browse to the folder the theme sources are into (just drag ad drop the folder into your terminal is enough): ```
cd /path/to/your/theme/sourecs
```And you type:```
sudo make
```, then ```
sudo make install
```Now, it should work!

---

### Post by AaronMT on 2008-10-29
Sweet, the above worked.

I've been using ColorizeMe ones Brave

---

