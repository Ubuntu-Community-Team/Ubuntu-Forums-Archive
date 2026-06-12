---
title: "Partition format"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by zzz@tkz on 2006-03-02
I was looking into saving on my empty partion using a liveCD, and I learned that I could use FAT32. So, I went into diskpart.exe (The windows utility), and it said that my empty partion was "FAT" format...is that the right kind?

---

### Post by andrewsawyer on 2006-03-02
Looks good.  Remember, you will have to mount it each time you boot the liveCD.  Also, don't mount it as your home partition else it will kill the session.

---

### Post by zzz@tkz on 2006-03-02
Yea, I heard about "mounting" it, how would one go about that :P?

---

### Post by andrewsawyer on 2006-03-02
[QUOTE=zzz@tkz]Yea, I heard about "mounting" it, how would one go about that :P?[/QUOTE]

System >> Administration >> Disks

You should be able to click on the disk that you want to mount, and then through the GUI you can choose where you want to mount it.  I would suggest either /mnt or /media

Alternatively, you can mount it from the terminal, however you will need to know the name of the disk - hda1, sda2 etc.  You can type:```
sudo mount /dev/hda1 /mnt
```For example.

---

### Post by zzz@tkz on 2006-03-02
I assume that is under ubuntu?

---

### Post by andrewsawyer on 2006-03-02
Sorry - yes, in Ubuntu.  The first way (using the GUI) is from the System drop down menu at the top left of your screen on the Gnome-Panel.

---

