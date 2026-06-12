---
title: "How to Reinstall Grub2 10.04 LTS"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by kilowattradio on 2010-05-01
I had a fubar with my Win7 laptop HD and now I need to reinstall Grub2 to the boot sector of my HD. I can find plenty of examples for Grub 1 legacy and how to upgrade from grub 1 to 2 but nothing on how to reinstall Grub2. I stll have the partition with Ubuntu 10.04 LTS on the computer so I don't need to reinstall LTS, just Grub2.


TIA,

Keith
:confused:

---

### Post by tommcd on 2010-05-01
Here are two tutorials for reinstalling grub2 to the MBR from the live CD:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
I would try it as it says in the second link first. If that fails, then follow the method 2, or the method 3 in the second link, or try it as it says in the first link.
 You can also easily reinstall grub2 to the MBR from the Ubuntu 10.04 alternate install CD. Just boot the alternate install CD and choose "rescue a broken system". It will proceed through a few screens and then get to a screen where it gives you the option to reinstall grub2 to the MBR.
Hope this helps.

---

### Post by kilowattradio on 2010-05-01
Thank you very much. That helped solve my problem.
:P

---

### Post by tommcd on 2010-05-02
> **kilowattradio said:**
> Thank you very much. That helped solve my problem.
:P
Glad I could help.
Just out of curiosity, and for future reference when trying to help others with the same problem, which method did you use to reinstall grub2 to the MBR? The only method I have personally used to reinstall grub2 was from the alternate install CD. So I would like to know what way worked for you.

---

### Post by reiki on 2010-05-02
I had to do this so many times I think I can do it in my sleep now. Windows 7 DataSafe was breaking grub any time I booted to Win7. So after every Win7 boot I had to reinstall grub2. 

I have Dual boot with Win7 and Ubuntu. This is on a stock Dell machine so I also have the Dell Utility partition and the recovery partition. (They're small so I'm leaving it alone for now).  Single hard drive (internal... I also have an external eSATA but that will confuse you so for now.... just one drive...)

#1 Boot live CD
#2 Go to Places and look for your Ubuntu partition.
  - some folks have separate /boot partition. I don't. I just have root and /home partitions. SO I just have / and /home. If you have a separate /boot partition you might have to make adjustments to the instructions.
  - My Ubuntu root partition is called Zino-root
#3 Mount the Ubuntu partition (I do this just by clicking on Zino-root)
#4 In terminal type:
```
 sudo grub-install --root-directory=/media/Zino-root /dev/sda
```
   - you will want to change the "Zino-root" part to whatever the name of YOUR directory is
   - that will install Grub2 to the MBR of my first (and only, in this case) hard drive and tell it that the other files it needs are in Zino-root
   - It should look for other OSs and you should not see errors.  
#5 In terminal type:
```
 sudo update-grub 
```

Done! 

That normally fixes things for me. I've also used this method by booting from a USB flash drive which is a lot faster than working from the CD (for me)

I think all of the above is correct... kinda did it from memory. I did it every day, sometimes more than once, while I was figuring out how Win7 was screwing up Grub.

---

