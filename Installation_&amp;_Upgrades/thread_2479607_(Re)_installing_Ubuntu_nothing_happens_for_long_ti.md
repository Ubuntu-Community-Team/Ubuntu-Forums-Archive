---
title: "(Re) installing Ubuntu: nothing happens for long time"
date: 2022-09-30
forum: Installation &amp; Upgrades
---

### Post by daanheuvelbeuk on 2022-09-30
Recently I bought a new computer. I am installing from USB. I have problems with the installation. After pressing ‘Install now’ nothing happened for a long time. I was going to ask if I could kill the installation process, but after some time (15 min) the next window appeared. 

Why did this take so much time?

I was watching this window for 15 minutes:
[https://ibb.co/mG3mqYq](https://ibb.co/mG3mqYq)

System:
SSD (old Windows HD with 4 partitions, Ubuntu HD with regular partitions (/, /home/ and /swap))
AMD Ryzen 9 9500X, 12 cores
NVIDIA RRX 3069 12GB
Two terminals

---

### Post by yancek on 2022-09-30
Did you download the iso file from the official Ubuntu site?
Which version, 22.04?
Did you do a checksum on the iso after it was downloaded to  verify that it was not corrupted in the process of downloading?
Which version of windows do you have?  Is it an EFI install?  Did you boot and try to install in EFI mode?
Could you post some information on your hardware?
Boot the Ubuntu usb and select the Try ubuntu option and open a terminal and enter the command: sudo parted -l and post the output  here.

---

### Post by MAFoElffen on 2022-10-02
It takes a while to boot from USB as you have seen. If you had pressed <ESC> you would have seen that in the background, when it first boots, it does a file check, which the first panel says "Press Control-C to skip file check"... So the first 5-10 minutes of that could have been that file/filesystem check... If there were problems from that file check, it would have prompted those...

Like you said: 
> 
*"...but after some time (15 min) the next window appeared. "*


---

