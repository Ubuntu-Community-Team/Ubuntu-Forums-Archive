---
title: "exe files"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by casperzshado on 2007-06-01
ok so im new to linux  so dont yell at me. exe files are microsoft what are lnux equivalent called and how do i install my software for my sound and video cards ?

---

### Post by tgm4883 on 2007-06-01
Well first we would have to know what video and sound card.  I suppose .deb files are the closest to .exe, but still not the same.  Lets just start from the beginning.  

What kind of video and sound card do you have.

What does "lspci" output on the terminal?

---

### Post by rillip on 2007-06-01
I don't think there really is an exe equivalent... .bash would be more like a .bat file.  RPM and .deb are more like installers, not the actual program.  

I think most of the actual executables don't have an extension, they're just binaries.

---

### Post by casperzshado on 2007-06-01
well i just checked the website and the x-fi fatal1ty is not compatible with linux, so i need to find another way to get sound.  2 gforce 7600 pci express and im pretty sure that they are not compatible either and you may have to elaborate on that terminal thing cause i have no idea

---

### Post by tgm4883 on 2007-06-02
FYI, you are probably going to get zero help from the manufacturer on any of these items.

Go to
Applications > Accessories > Terminal
Type in "lspci" without the quotes and hit enter.
Copy whatever it says after that and post it on here.

---

### Post by tgm4883 on 2007-06-02
It looks like creative is blocking the compatibility of the sound card.  The video card looks to be supported though

---

### Post by casperzshado on 2007-06-02
so do yall work around these obstacles or is there a different store ofr linux compatible stuff, seems like an uphill battle

---

### Post by tgm4883 on 2007-06-02
Your video card works.  

When you buy things that are compatible with linux, then it makes things a lot easier.  More and more things become compatible every day so sooner or later your sound card may work.  I buy my things from whatever store I can find them in be it best buy, circuit city, pc club, newegg.

---

### Post by casperzshado on 2007-06-02
i cant even figure out how to install java ugh

---

### Post by tgm4883 on 2007-06-02
[http://ubuntuguide.org/wiki/Ubuntu_Feisty](http://ubuntuguide.org/wiki/Ubuntu_Feisty)

---

### Post by hoggbottom59 on 2007-12-01
I think you need to skip all this and look at the Synaptic Package Manager. 
From here you do all the installation and can automatically install thousands of packages.

If you have no success there try the .deb files as suggested then get involved in the nitty gritty compiling from scratch if absolutely necessary.

In general you'll find everything you need in System-Administration-Synaptic Package Manager.

Unlike Windows Ubuntu will upgrade anything you installed with Synaptic when there are updates ready.


Yours
Leon.

---

