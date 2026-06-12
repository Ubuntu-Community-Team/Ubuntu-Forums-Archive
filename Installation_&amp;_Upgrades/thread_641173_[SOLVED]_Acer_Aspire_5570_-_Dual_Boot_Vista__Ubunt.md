---
title: "[SOLVED] Acer Aspire 5570 - Dual Boot Vista / Ubuntu 7.10"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by cam.king on 2007-12-15
Hi!

I am new to the Linux environment and want to install Ubuntu 7.10 on my Acer Aspire 5570 notebook.  

The unit came pre-installed with Windows Vista Home Premium (which I will require to keep due to certain Windows only programs I have to run).  When I took delivery of the notebook it had the hard drive already partitioned into two drives:
  - C:\     "ACER"    33.5Gb
  - D:\     "DATA"    33.5Gb 

I have run the Ubuntu 7.10 live CD and very much want to join the Linux experience but when I went to install there was no option for *"Guided - resize IDE1 master, partition ... [technical data here] ... and use free space" *that I have seen on the reputable installation guides.

Basically my question is; can someone please guide me as to how to create a partition, without reformatting the entire hard drive, and install Ubuntu 7.10 as a dual-boot with Vista Home Premium?

To assist in this endeavour here are the specifications on my Acer notebook:

 - MODEL:          Acer Aspire 5570
 - CPU:               Intel CPU - T1350 @ 1.87GHz
 - RAM:              1024Mb
 - HDD:              Aprox 60Gb (partitioned at the factory as C:\ "ACER" and D:\ "DATA" with each having an identical size of 33.5Gb)

Should a user require any more information then please feel free to email me at: [email]cam.king.01@gmail.com[/email] or post on this thread.  

Anyone's help would be greatly appreciative, I think as far as computer communities go Linux generally (and Ubuntu especially) is the most supportive that I have come across.

Thank-you.

---

### Post by Pumalite on 2007-12-15
With Vista; you have to allocate space for Ubuntu from within Vista (Administration), then install Ubuntu. During installation, go Manual and partition as follows:
10 GB for '/'
1 GB for /swap (laptops; /swap=RAM)
The rest for /home.
This is an old link I found for 5100:
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by cam.king on 2007-12-15
> **Pumalite said:**
> With Vista; you have to allocate space for Ubuntu from within Vista (Administration), then install Ubuntu. During installation, go Manual and partition as follows:
10 GB for '/'
1 GB for /swap (laptops; /swap=RAM)
The rest for /home.
This is an old link I found for 5100:
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

Pumalite, thank-you for your assistance.  I have just finished installing Ubuntu on the system.  Your quick response is greatly appreciated.

---

### Post by erfahren on 2007-12-15
hey, if you reformatted the entire 30GB Data drive (Windows D:) to install Ubuntu you might need to disable Acer's eRecovery ("monitor.exe" specifically) in Vista. eRecovery looks for that data drive when booting Vista.

see the first part of this thread: [http://ithacafreesoftware.org/forum/viewtopic.php?t=251](http://ithacafreesoftware.org/forum/viewtopic.php?t=251)

---

