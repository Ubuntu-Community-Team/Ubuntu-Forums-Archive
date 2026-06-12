---
title: "Ubuntu Software Centre/GDebi install problem"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-05-02
Trying to install Songbird from [http://www.getdeb.net/software/Songbird](http://www.getdeb.net/software/Songbird)

When I click the [Install Now]("http://www.getdeb.net/install/songbird") link it only recommends installing it with Ubuntu Software Centre which says the package is not found. 

I have read I need to open it with GDebi, which is installed but I do not know how to make Firefox open it with it. 

I tried pressing 'Choose an application' when Firefox prompts me and I looked in /bin but found nothing about GDebi, how can I fix this please?

I need to go away from the computer for awhile now and count to 10 :)

---

### Post by dino99 on 2011-05-02
direct install often fail, better to download it then choosing "install with" gdebi
or set getdeb directly into your synaptic repo tab

hhtp://archive.getdeb.net/ubuntu natty-getdeb

---

### Post by Dáire Fagan on 2011-05-02
> **dino99 said:**
> direct install often fail, better to download it then choosing "install with" gdebi
or set getdeb directly into your synaptic repo tab

hhtp://archive.getdeb.net/ubuntu natty-getdeb

Sorry, I should have clarified that right clicking Install Now doesn't allow me to save a deb file, only some html file. Also, I am using Maverick, so can I simply replace hhtp://archive.getdeb.net/ubuntu natty-getdeb with hhtp://archive.getdeb.net/ubuntu maverick-getde going into software sources and clicking add?

---

### Post by Dutch70 on 2011-05-02
I just installed it from your link. When I clicked the "install now" my option was to open it with apturl. 
Do you not have apturl installed?

---

### Post by Dáire Fagan on 2011-05-02
> **Dutch70 said:**
> I just installed it from your link. When I clicked the "install now" my option was to open it with apturl. 
Do you not have apturl installed?

When I type apturl in terminal it asks for a url so i'm assuming it is installed. How do I make firefox open it with it? It does not give me a choice, and amn't I supposed to be using Gdebi anyway?

---

### Post by Dutch70 on 2011-05-02
Make sure it's installed in software center, as in the pic below.

---

### Post by Dáire Fagan on 2011-05-02
apturl and apturl-common are installed as I am being given the option to remove. apturl-kde not installed but I'm in gnome.

---

### Post by Dutch70 on 2011-05-02
If you look at my pic, the one with kde isn't installed on mine either. 
I really don't know why you wouldn't be getting that option when you click the link. Do you have a different web browser you could try it with? 

If that doesn't work, maybe someone else will have some input on it.

---

### Post by Dáire Fagan on 2011-05-02
Chrome and Chromium do the same thing....

Can I not select GDebi or apturl from /bin or something? Firefox does let me browse my system for a program to open it with...

---

### Post by Dutch70 on 2011-05-02
I don't know why you're not getting the option to download it with apturl. This pic is exactly what pops up when I click "install now" from your link.
Then it starts the download in a window just like the one you get updates in, so I assume it's downloading it to software center. 
Then it gives you an option to install. You just click the install button when it pops up. 

If yours isn't doing this, something isn't working right, and you may be better off to open a new thread with the new information. That's totally up to you.

---

### Post by Dutch70 on 2011-05-02
I've also right clicked the link and saved it to my desktop. When I right click the icon, I get no option anywhere to install with Gdebi.

Edit: Don't miss my last post #10.

---

### Post by Dáire Fagan on 2011-05-02
> **Dutch70 said:**
> I don't know why you're not getting the option to download it with apturl. This pic is exactly what pops up when I click "install now" from your link.
Then it starts the download in a window just like the one you get updates in, so I assume it's downloading it to software center. 
Then it gives you an option to install. You just click the install button when it pops up. 

If yours isn't doing this, something isn't working right, and you may be better off to open a new thread with the new information. That's totally up to you.

I get the exact same window, only where it says apt-url for me it says software-centre, I also have that choose button - is there somewhere I can choose apt-url? When I try as is it brings up software centre but says: Not found. There isn't a software package called "Songbird" in your current software sources.

I don't see any point in opening a new thread, as the problem remains as it was when I began it?

---

