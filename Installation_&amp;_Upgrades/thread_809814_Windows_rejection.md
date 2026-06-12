---
title: "Windows rejection???"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by pmq on 2008-05-27
OK, 

I just decided to install ubuntu to my home computer. This will be a dual boot system. I used a 7.10 disk i had and later upgraded to 8.04. After everything was sorted i went back to windows to sort out some work. Next think i know windows is going crazy. Although the boot into windows takes so long, i noticed some applications in windows are going crazy. One is skype and msn, keep randomly logging in and out.
Next firefox, when i use 2 or more tabs and switch between them, i notice the pages reload and refresh every time i do this. I scanned for virusus and used an anti spyware, but everything is clean.
Also my external hard drive is turning on and off randomly too. 
All of this seems to happen in windows. This never occured before the dual boot. 
Is my machine haunted?

pmq

---

### Post by xfceuser on 2008-05-27
hi, dont worry, you dont have a virus !
 this problem happens because windows is confused about the new partition, due its file format (ext3).
every time windows starts up (and many occasionally when it is even started), it search all the hardware for recognizing them, also to check for any changes, but when it comes to the Linux partition, it gets confused, and it suppose that it must wait longer time for hardware response to recognize it. this is the reason your very long windows start time.
your external hard drive turns on and off randomly, since windows restart the related I/O port intentionally, as an effort to recognize the Linux partition.
As for a solution, maybe the only way is to have Linux on a separate HDD and disconnect it when you are not using Linux ! (even if you dont disconnect it , there might be less severe problem , as long as in windows, you dont do anything with Linux HDD)

However, the severity of your problem is peculiar. which version of windows do you use?

---

### Post by pmq on 2008-05-27
im using xp home, however i have solved the problem of the crazy internet browser.
i checked processes running and with 1 browser it was using 56% cpu (dual system).
i checked the error console on firefox and discovered a skype plug-in was installed, this was done in a very sneaky manor by skpye as i didnt see it.
I installed skype windows right after linux, so it was a co-incidence that it occured.

---

