---
title: "Hard drive wiped clean"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by run6run1 on 2012-11-23
Problems re installing 10.04 lucid   I have been using lucid for sometime on an Acer 1 net book with a small hard drive 8gb.Recently whilst streaming I picked up a bug which froze the system.I attempted usuall disconnection procedure but the system would not reboot.I then attempted to re install lucid which went smoothly untill I encountered error message when I aborted the install and then attempted  to repeat the procedure when the hard drive appeared to have been wiped clean so no system is available on computer.Having tried to use boot repair, when I begin the install I get asked WHERE DO YOU WANT TO PUT UBUNTU NET BOOK 10.04 Giving me the option to either eraze and use the entire disk, and below is shown the drive SCS12(000)(SDA)8.1GB ATA P-SSD 1800 and below the option is shown to specify partitions manually (advanced) .Which ever option I chose I keep getting error message stating UBUNTU NET BOOK 10.04 DETECTING FILE SYSTEM INPUT/OUTPUT ERROR DURING WRITE ON /DEV/SDA. I can boot the system live from a USB flash drive but only get error messages when I try to install the system.Can you help please.

---

### Post by dgharmon on 2012-11-23
> **run6run1 said:**
> Recently whilst streaming I picked up a bug which froze the system.I attempted usuall disconnection procedure but the system would not reboot.

Could you be more specific as to what kind of 'bug' froze your system. What 'usuall disconnection procedure' are you referring to.

---

### Post by ibjsb4 on 2012-11-23
DETECTING FILE SYSTEM INPUT/OUTPUT ERROR DURING WRITE

Sounds like your SSD has either been corrupted or died.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=DETECTING+FILE+SYSTEM+INPUT%2FOUTPUT+ERROR+DURING+WRITE+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=DETECTING+FILE+SYSTEM+INPUT%2FOUTPUT+ERROR+DURING+WRITE+&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by 2F4U on 2012-11-23
> **run6run1 said:**
> Problems re installing 10.04 lucid   I have been using lucid for sometime on an Acer 1 net book with a small hard drive 8gb.Recently whilst streaming I picked up a bug which froze the system.I attempted usuall disconnection procedure but the system would not reboot.I then attempted to re install lucid which went smoothly untill I encountered error message when I aborted the install and then attempted  to repeat the procedure when the hard drive appeared to have been wiped clean so no system is available on computer.Having tried to use boot repair, when I begin the install I get asked WHERE DO YOU WANT TO PUT UBUNTU NET BOOK 10.04 Giving me the option to either eraze and use the entire disk, and below is shown the drive SCS12(000)(SDA)8.1GB ATA P-SSD 1800 and below the option is shown to specify partitions manually (advanced) .Which ever option I chose I keep getting error message stating UBUNTU NET BOOK 10.04 DETECTING FILE SYSTEM INPUT/OUTPUT ERROR DURING WRITE ON /DEV/SDA. I can boot the system live from a USB flash drive but only get error messages when I try to install the system.Can you help please.

Without you giving the error messages, the post is not very helpful. From what you are saying I would guess that your hard drive has died.

---

### Post by run6run1 on 2012-11-25
> **2F4U said:**
> Without you giving the error messages, the post is not very helpful. From what you are saying I would guess that your hard drive has died.

Yes I guess  you are right and there is no real likely hood of recovery I can not even get into the bios to attempt to rectify the system another error message read FAILED TO CREATE FILE SYSTEM, THE EXT 4 FILE SYSTEM CREATION PARTITION #1 OF SC12 (000) (SDA) FAILED.

---

### Post by run6run1 on 2012-11-25
> **ibjsb4 said:**
> DETECTING FILE SYSTEM INPUT/OUTPUT ERROR DURING WRITE

Sounds like your SSD has either been corrupted or died.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=DETECTING+FILE+SYSTEM+INPUT%2FOUTPUT+ERROR+DURING+WRITE+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=DETECTING+FILE+SYSTEM+INPUT%2FOUTPUT+ERROR+DURING+WRITE+&as_qdr=all&sa=Google+Search&lang=en)


Used a programe called system rescue which is an ISO file which appears to have done what it says.Made a USB drive and it appears it has ressurrected the hard drive the system as I write is currently updating.Certainly I would recommend this tool for anybody experiecing simillar problems

---

