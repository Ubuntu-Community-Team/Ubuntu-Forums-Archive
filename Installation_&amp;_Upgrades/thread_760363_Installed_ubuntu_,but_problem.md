---
title: "Installed ubuntu ,but problem"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Markoo on 2008-04-20
Hi,

I have installed my ubuntu on my D: partition with E: partition for swap, on C: are windows. There were no problems while I was instaling my ubuntu, after reset I dont get graphic view, only terminal. Is that a problem or I can start a graphic view?

Thanks

---

### Post by glennzo on 2008-04-20
You can log in at the prompt and type **startx**. Post the error output in a reply here. The errors will be the lines preceded by EE.

---

### Post by daengbo on 2008-04-20
Which disk did you use to install Ubuntu? What version? When you get text mode, are there any errors? Log in and type
> dmesg
try to remember the last few lines and tell us of anything that sounds suspicious. Post it if you can.

---

### Post by Markoo on 2008-04-20
when I write **startx** I get : Not found

At top of the page is writen:

busy box v.1.13 (Debian 1:1.1.3-5ubuntu 7) Built-in shell rash
(initramfs) _ 

After (initramfs) I can write


Disk is Ata, maxtor 40gb, 

There is no errors, when I press to start ubuntu I get the logo and nothing is happening, after 3-4min I get what I write in 3line of this post

---

### Post by daengbo on 2008-04-20
It sounds like you installed the server version, which doesn't have desktop software. Asking again, which CD did you use to install?

---

### Post by Markoo on 2008-04-21
Version is 7.10 i386, when I boot from cd I get desktop,
While is trying to boot ubuntu I presed ctrl + alt + F1 and I get some error obout hard

---

### Post by bohmto on 2008-04-21
Hi i just wonder if its a laptop you installed it on if it is then you can try to turn of the diskett drive in bios

bohmto

---

### Post by Partyboi2 on 2008-04-21
> **Markoo said:**
> Version is 7.10 i386, when I boot from cd I get desktop,
While is trying to boot ubuntu I presed ctrl + alt + F1 and I get some error obout hard
What is the exact error message you are getting when you press ctrl+alt+F1? Also can you post what type of graphics card you are using as well as the rest of your system specs.

---

### Post by FredB on 2008-04-21
For dmesg, just type this :

dmesg | tail

---

