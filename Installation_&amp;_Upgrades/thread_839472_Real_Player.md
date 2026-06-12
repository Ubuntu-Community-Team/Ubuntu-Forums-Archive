---
title: "Real Player"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by asnarang.j on 2008-06-24
Recently I installed Ubuntu 8.04 on my windows PC.  Please let me know how can I run Real Player on Ubuntu.  I am a novice.  Please explain in simple language as we teach a child.
A S Narang.

---

### Post by Nikitas350 on 2008-06-24
Open a terminal (Application-->accessories--->terminal) and run the following commands:
wget [http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin)
chmod a+x RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin

---

### Post by asnarang.j on 2008-06-25
I tried the suggested commands but I got the reply that no such file or directory exists.

---

### Post by Suji on 2008-06-25
Hi 
 I followed the following steps to install RealPlayer in my computer.
    *)Download and save the installation file from [http://www.real.com/linux]("http://www.real.com/linux")
    *)Open up a terminal and go to the directory where the downloaded file is saved.
    *)use the following command to change the permissions fo r the file.
     "chmod 755 <filename>.bin"
    *)Now, you would be able to install the file by this command.
    " ./<filename>.bin"
    *)Just keep pressing Enter and the installation will be complete soon.

Eg:
 The downloaded filename will be RealPlayer11GOLD.bin
 so replace <filename> with RealPlayer11GOLD.bin

Note: 
  If you feel its tedious to fill long names, in directory  if you want to use the filename just give first 3 or 4 letters and press <tab>key, the shell would fill it for you.

  Hope I answered your questions.

---

