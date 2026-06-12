---
title: "How to install jdk in ubuntu 6?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by bilol on 2008-10-20
Hello friends,
Please tell me how to install jdk in ubuntu 6.
Thanks in advance.

---

### Post by ajgreeny on 2008-10-20
Ubuntu 6?  What do you mean?  If you are still running 6.06LTS there should still be repos available for it with java included.  If you have 6.10, I'm afraid there are no updates any more and you will need to update to a newer version of ubuntu.

---

### Post by guitsy on 2008-10-20
copy/download j2sdk-1_4_18-linux-i586.bin(or any version of jdk .bin file) to ur desktop.

go to applications>accessories>terminal

enter

cd ~/Desktop
sudo cp j2sdk-1_4_18-linux-i586.bin /usr/local/bin
(here iam copying j2sdk.bin from my desktop to /usr/local/bin)
sudo -s
pw:type ur password
cd  /usr/local/bin
(now iam changing to /usr/local/bin from my desktop)
chmod a+x j2sdk-1_4_18-linux-i586.bin
(ie changing permission of file to be executable)
ls -l
(ie to verify whether the file j2dk is there in /usr/local/bin  DIR)
./j2sdk-1_4_18-linux-i586.bin
press ENTER few sec.now u will come to the end of egreement.TYPE yes)

BINGO!:guitar:U HAVE SUCCESFULLY INSTALLED UR JDK

---

### Post by bilol on 2008-10-22
Hi ajgreeny,
Thanks for your help.I am very new to ubuntu.You may wonder ...I had to shift from Ubuntu 8.04(hardy) to Ubuntu 6.06LTS. Because-I had to install Ubuntu in my external disk.Installing 'Hardy' to external disk was a nightmare.It was getting installed but not running in any other machine except by which it was installed to the external.I tried several ways , but it was giving *grub erro*r in all occasions.In contrast,running ubuntu 6.06LTS from external disk in any machine is as smooth as butter.

Hi guitsy,
Thanks a lot.Could you please send me the link from where I can download jdk (and possibly all different libraries)for Ubuntu?

---

### Post by guitsy on 2009-07-18
hi friend 
just try this...........
click on system......help and support........advanced topics........writing your own programs......... select java........now choose jdk option you want........follow the instruction

---

