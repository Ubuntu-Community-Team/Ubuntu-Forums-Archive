---
title: "Error whenever I use apt-get"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by gejr on 2006-10-05
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I get a couple of these whenever I apt-get something. The programs I install seem to install well anyway, so it's not really a biggy. Just curious if anyone knows why this message appears, and if there's a reasonably easy way to remove the problem. Thanks :)

---

### Post by henriquemaia on 2006-10-05
Looks like an X server error. Try apt-getting something from a tty* to see if you still have that message.

*press ctrl+alt+F1 (or any F until F6 - press ctrl+alt+F7 to get back to the gui)

---

### Post by Kateikyoushi on 2006-10-05
The first line says it is an invalid or uninitialized pointing device in X.

You could check your /etc/X11/xorg.conf to see what device it is.

---

### Post by gejr on 2006-10-09
#1 Correct, I didn't get the error when i apt-get something in another tty.

#2 How would I find that particular error in xorg.conf? I looked in the file, but didn't see anything pointing to device number 168 or 145..am I being blonde now?:)

---

### Post by gejr on 2006-10-10
*bump*

Am I really the only one who's ever encountered a problem like this?:)

---

### Post by nathanbriggs on 2006-10-10
> **gejr said:**
> *bump*

Am I really the only one who's ever encountered a problem like this?:)

probably easiset is to post the pointer device section of your xorg.conf file most likely you have a typo

---

