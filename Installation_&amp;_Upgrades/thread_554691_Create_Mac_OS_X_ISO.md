---
title: "Create Mac OS X ISO"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Black Mage on 2007-09-19
Hi, I have purchased a copy of MAC OS X and I am trying to install it on VMware Sever in Ubuntu. I was reading through a tutorial and it said I need to create an ISO image from the Mac CD and it said to use some program called Alcholol 120%, but that cost money I don't have(Mac OS X cost enough).

So how do I create  an ISO of Mac OS X CD in Ubuntu to install onto VMware Server?

---

### Post by Pumalite on 2007-09-19
[http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

---

### Post by Black Mage on 2007-09-19
Yes I've read that but the OS X CD doesn't mount..........

So what else should I do?

---

### Post by Pumalite on 2007-09-19
'To make an ISO from your CD/DVD, place the media in your drive but do not mount it.'

---

### Post by Black Mage on 2007-09-19
dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

All of these return an error, example: dd: opening `/dev/scd0': No medium found

---

### Post by Pumalite on 2007-09-19
Check your CD for data corruption.

---

### Post by Black Mage on 2007-09-19
Its work fine when I pop it into my PowerBook Dual Core.

---

### Post by Black Mage on 2007-09-19
Ok, I decided to Mac an ISO on my Mac using Mac OS X and then burn it to a CD(again) and put it on my IBM running Ubuntu.

---

### Post by Pumalite on 2007-09-19
Obviously Ubuntu cannot read what's in your CD.

---

### Post by maybeway36 on 2007-09-19
Can you even install Mac OS in VMWare?

---

