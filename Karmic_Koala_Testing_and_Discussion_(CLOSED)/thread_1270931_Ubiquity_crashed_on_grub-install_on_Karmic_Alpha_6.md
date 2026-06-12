---
title: "Ubiquity crashed on grub-install on Karmic Alpha 6"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chrissk_2 on 2009-09-20
Hi all,

i just tried to install karmic alpha 6 on a dual boot machine (windows XP) and the installer crashed when it tried to run grub-install.

I found that this was a known bug but in was fixed on alpha 5. However it is still happening on my pc. Anything i can do to finish the installation ?

I will also try with the alternative installer to see how it goes.

Any help will be appreciated 

Thanks in advance

---

### Post by wilee-nilee on 2009-09-20
If you can get to the command run a apt-get update and apt-get install grub. I have had similiar problems and the update fixed it. Hopefully others will chime in with more definitive answers. I have never had this issue with dual boot though.

---

### Post by chrissk_2 on 2009-09-20
> **wilee-nilee said:**
> If you can get to the command run a apt-get update and apt-get install grub. I have had similiar problems and the update fixed it. Hopefully others will chime in with more definitive answers. I have never had this issue with dual boot though.

The problem is that i run the installation from usb stick.
Its not an upgrade from Jaunty

---

### Post by wilee-nilee on 2009-09-20
I think you will need to give more information to get responses. 

Is it a net book with no disc reader. also a USB install I believe would allow the same command line access. 

This forum is quite helpful but you have to be specific, even as far as what the computer model is, and exactly what you have done so far, like did you repartition before installing and although you say dual boot is it a wubi install.

---

### Post by chrissk_2 on 2009-09-21
> **wilee-nilee said:**
> I think you will need to give more information to get responses. 

Is it a net book with no disc reader. also a USB install I believe would allow the same command line access. 

This forum is quite helpful but you have to be specific, even as far as what the computer model is, and exactly what you have done so far, like did you repartition before installing and although you say dual boot is it a wubi install.

Well yes you are correct, i just did not know what info is relevant.
Anyway its a pentium 4 (64 bit) pc with 2GB ram and a sata disk(i don't remember the model but i can find out if needed). It has 2 win XP primary partitions and one more for ubuntu with ext4. Obviously it also has a swap partition too. The boot loader is on the MBR.

I had partitioned the machine once when i installed jaunty and i just re-formatted the ext4 partition to install ubuntu.

It is not a wubi installation. I can post any logs you might need just tell me ...

---

### Post by chrissk_2 on 2009-09-21
> **chrissk_2 said:**
> Well yes you are correct, i just did not know what info is relevant.
Anyway its a pentium 4 (64 bit) pc with 2GB ram and a sata disk(i don't remember the model but i can find out if needed). It has 2 win XP primary partitions and one more for ubuntu with ext4. Obviously it also has a swap partition too. The boot loader is on the MBR.

I had partitioned the machine once when i installed jaunty and i just re-formatted the ext4 partition to install ubuntu.

It is not a wubi installation. I can post any logs you might need just tell me ...


Btw jaunty installs flawlessly every time i tried it

---

### Post by QIII on 2009-09-21
Did you try to install fresh from the Alpha 6 iso dated Sept 17th?

---

### Post by chrissk_2 on 2009-09-21
> **QIII said:**
> Did you try to install fresh from the Alpha 6 iso dated Sept 17th?
 
Yes thats how i did it. Its not an upgrade, its a clean install, since i formatted the disk first

---

### Post by QIII on 2009-09-21
Every machine on which I attempted to install Alpha 6 (Sept 17 iso) fresh resulted in a borked system.  That's both the 32 and 64 bit versions on 32 and 64 bit machines.  I'm not sure if the iso has been updated.

What I finally did to get Alpha 6 running was to reinstall Alpha 5 and use dist-upgrade from the terminal.  (apt-get upgrade resulted in the same issues as a clean install.)

I still have a few weird issues (some tty before xsplash) but everything else seems to be working.

I went to launchpad to report this and found a lot of other similar reports for fresh installs.  Same with the method I used.

Like I said, the problems I have do not seem to persist when I get to xsplash -- and that seems to have been reported as well.

BTW -- Before attempting the dist-upgrade, I did

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```to get my other OSs to show in GRUB.

---

### Post by chrissk_2 on 2009-09-21
thanks very much :)

---

