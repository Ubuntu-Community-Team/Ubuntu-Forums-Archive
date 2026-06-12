---
title: "Dual booting windows 8.1 + Ubuntu issues."
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by jmmrly on 2014-10-22
I currently have windows 8.1 pre-installed on the laptop. I have a 840 evo 120gb and a 500gb hdd. I've shrunk the SSD and cleared 20gb free for ubuntu. However, when i go onto ubuntu installation, it shows the SSD being completely free, when it should have a windows partition on it. I'll attach images to show what i mean. Help would be appreciated.
Computer management in windows : [http://oi59.tinypic.com/2ytqr7a.jpg](http://oi59.tinypic.com/2ytqr7a.jpg)
Ubuntu installation : [http://oi61.tinypic.com/29wppic.jpg](http://oi61.tinypic.com/29wppic.jpg)

Edit: Sorry. Posted in wrong section. Here's the correct thread. - [http://ubuntuforums.org/showthread.php?t=2249458&p=13149198#post13149198](http://ubuntuforums.org/showthread.php?t=2249458&p=13149198#post13149198)

---

### Post by jmmrly on 2014-10-22
I currently have windows 8.1 pre-installed on the laptop. I have a 840 evo 120gb and a 500gb hdd. I've shrunk the SSD and cleared 20gb free for ubuntu. However, when i go onto ubuntu installation, it shows the SSD being completely free, when it should have a windows partition on it. I'll attach images to show what i mean. Help would be appreciated.
Computer management in windows : [http://oi59.tinypic.com/2ytqr7a.jpg](http://oi59.tinypic.com/2ytqr7a.jpg)
Ubuntu installation : [http://oi61.tinypic.com/29wppic.jpg](http://oi61.tinypic.com/29wppic.jpg)

---

### Post by davit2 on 2014-10-22
Hi, 
while installing select "Try ubuntu"

1.connect to internet
2.open terminal 

type
sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo fixparts /dev/sda  (is will ask your for Y/N, press Y, then it will write "MBR command" or something like that, don't press anything in this line just close terminal and try to install ubuntu)

---

### Post by jmmrly on 2014-10-22
/sda is my 500gb HDD which i don't want to be installing to. So i typed /sdb and it said "Found valid MBR and GPT. Which do you want to use?" 1. MBR 2. GPT 3. Create blank GPT   Which do i pick? This won't overwrite my drive will it?/delete my windows partition

---

### Post by davit2 on 2014-10-22
No, don't worry, choose MBR

---

### Post by jmmrly on 2014-10-22
> **davit2 said:**
> No, don't worry, choose MBR

Worked perfectly. Thanks.

---

### Post by davit2 on 2014-10-22
you are welcome

---

### Post by oldfred on 2014-10-22
Merged threads.

If drive was showing both MBR and gpt, was Windows installed in BIOS mode or gpt mode?

Windows only boots from gpt with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) with BIOS.
So partitioining has to match how you install.

You issue may have been just the drive was gpt and you installed Windows in BIOS mode. Windows does not correctly convert a gpt drive to MBR when re-installing in BIOS mode on a gpt partitioned drive. It leaves the backup gpt partition table and ignores it. But Linux tools see both MBR & gpt and get confused. It must be one or the other.

---

