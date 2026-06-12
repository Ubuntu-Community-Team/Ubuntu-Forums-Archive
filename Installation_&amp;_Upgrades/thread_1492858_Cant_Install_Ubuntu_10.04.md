---
title: "Cant Install Ubuntu 10.04"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by arjunbajaj on 2010-05-25
Hey Guys,

I am Facing Huge problems installing ubuntu 10.04.

I have an IBM Laptop. Its ThinkPad R51.

I had installed ubuntu 9.10, then when i upgraded to 10.04 it didn't work.

Then i downloaded the cd image and booted from that. It loaded and told to choose the options. I choose install now and after some time my screen went blank and after that my laptop shut down automatically.

Then I ordered an Original Ubuntu 10.04 CD. The same thing happened and it didn't work.

I have also tried USB Boot.....

but none of them work......

So is there any **compatibility problem** or what is it......

Why cant i run ubuntu 10.04 on my laptop.......

And how should i run it???.......

Thnx......

---

### Post by mikewhatever on 2010-05-25
Post your laptop hardware specs: cpu, ram, graphics.

---

### Post by darkod on 2010-05-25
The first thing to try with the cd is not Install Now, it is Try Ubuntu. That will show you whether it can load in live mode, or there is some incompatibility.
According to what you said so far, i don't think it will load live mode correctly.

At the main menu, you could try pressing F6 and in the advanced option select nomodeset. After that select Try Ubuntu and see if it loads.

If that helped, usually you can install, but on first boot you would have to add nomodeset in the boot line again, otherwise it won't boot.

And once you have booted the installed ubuntu, search for drivers which should make it work fine. If not, there is a way to add the nomodeset parameter permanently.

---

### Post by arjunbajaj on 2010-05-25
mikewhatever my laptop's specs are

IBM ThinkPad R51 :

1.7 GHz Pentium M Processor
1.4 GB RAM 
160 GB hard drive 
DVD/CD-RW Combo Drive
15" 1400x1050 display
Integrated 802.11b/g wireless network card.


and i think there is no special graphics card.....

---

### Post by arjunbajaj on 2010-05-25
hey darkod......

i tried to do nomodeset but that also didn't work.....

what should i do.....

cause i want an os on my laptop.......

please help..........
thnx

---

### Post by SoftPops on 2010-05-25
Have a look at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes). If you have an i8xx graphics chipset this may resolve your problems. I would suggest trying the LiveCD part of Workaround A first.
 
Cheers.

---

### Post by darkod on 2010-05-25
How about Safe Graphics?

You need to test the advanced options one by one, and see if it works. If it does, remember whichoption made the difference.

---

### Post by mikewhatever on 2010-05-25
> **SoftPops said:**
> Have a look at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes). If you have an i8xx graphics chipset this may resolve your problems. I would suggest trying the LiveCD part of Workaround A first.
 
Cheers.
+1
I suspect pentium M puts the laptop into that category. I would suggest installing Karmic and hope Intel fixes the driver for the next release.

---

### Post by arjunbajaj on 2010-05-26
hey softpops....

i did the thing what the page said and it booted....
i even installed ubuntu
but now

i cannot start it....it doesn't load.....

i know that page has a solution for that but i cannot enter the kernel to type that code.....

what should i do?????

thnx....

---

### Post by SoftPops on 2010-05-26
> **arjunbajaj said:**
> hey softpops....
 
i did the thing what the page said and it booted....
i even installed ubuntu
but now
 
i cannot start it....it doesn't load.....
 
i know that page has a solution for that but i cannot enter the kernel to type that code.....
 
what should i do?????
 
thnx....
 
Hi arjunbajaj:
You have gone one stage further than me now, I have only tested booting from the liveCD so far. Did you do the installation steps?
 
 
>  
1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Ctrl+x to boot.
 

 
and then entering the > echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -uto make it permanent?

---

### Post by SoftPops on 2010-05-26
Found a bit more info that maybe useful in this post: [http://ubuntuforums.org/showpost.php?p=9352327&postcount=12](http://ubuntuforums.org/showpost.php?p=9352327&postcount=12)
 
This describes how to update grub after installing 10.04 and optionally install a fresh kernel. Hope it helps.

---

### Post by arjunbajaj on 2010-05-26
hey SoftPops it worked.......

thanks man.............now i'm using ubuntu 10.04....

thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)

---

### Post by SoftPops on 2010-05-26
> **arjunbajaj said:**
> hey SoftPops it worked.......
 
thanks man.............now i'm using ubuntu 10.04....
 
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
thanks everyone........:)
 
And thank-you arjunbajaj - knowing that yours has worked, I can now give mine a go!
 
Happy Days

---

### Post by arjunbajaj on 2010-05-26
sure softpops

thanks for the info and go try......

hope your works too....

thanks....:)

---

