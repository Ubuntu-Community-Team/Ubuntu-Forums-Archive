---
title: "Xserver problem when installing?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by XLostSpartanX on 2006-06-04
I get the CD to boot, then I slect the option to boot [live] unbuntu, and install it.  It goes though all the file, the gives me an error about my xserver.  Im not sure what to do.  Im using an ATI Radeon X700 pro graphics card.

---

### Post by XLostSpartanX on 2006-06-04
help me please.

---

### Post by Axed on 2006-06-05
I know exactly what the problem is, but I'm not sure how to fix it (newbie here too). I installed Breezy and had the same issue, but was able to install it thanks to it not relying on the xserver.

My video card is an ATI X800GTO, and in short the default ATI driver does not work. Infuriatingly, nor does the "safe" vesa driver. 

Now I'm trying to install a fresh copy of Dapper, and can't (upgrade from Breezy isn't an option because I installed the x64 edition and need the i386 edition). Essentially you need to use the fglrx driver, but I have no idea how to get the install CD to use it. Any help on this would be greatly appreciated.

---

### Post by Boggles3 on 2006-06-15
hello there.
I am running ubuntu on my pc right now, and have an nvidia card.
But my roomate is haveing the exact same issue that you are. he has a fire gl v5000, and apperently the driver doesnt work for that iether.

I do have one hint though that may help you at least start trying to do something about it. 
Even though it is a live cd and you dont have a gui. you are running ubuntu. your just in consol. it was only the xserver that messed up. so if you go and find some commands online and  find out how to instal the fglrx stuff from the consol. if you do that and configure your xorg correctly for that from consol using nano command then  in my theory at least you should be able to get it working.
On the other hand dont take my word as the word to fallow because i am a newb too.
I also found something while looking through forums saying that the default ati has some kind of issue with monitors setting in you gdm conf. ill have to try that too.
Good luck, hopefully someone that really knows whats going on here will come help, since this is kind of a big deal, and a huge turn off from ubuntu to have it not even be able to run xserver from the live cd.  
Im tired of xserver issues, it seems ubuntu has a long run in with them from the get go

---

