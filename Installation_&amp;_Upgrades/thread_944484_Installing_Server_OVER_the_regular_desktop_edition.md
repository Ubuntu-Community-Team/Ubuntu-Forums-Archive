---
title: "Installing Server OVER the regular desktop edition"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by bnciwebdesign on 2008-10-11
I have BOTH Desktop Edition and Server Edition of Ubuntu 8.04, I was wondering, if I could install the Server Edition OVER the Desktop. I am just playing with the OSes seeing how far I can go without connecting it to the Internet. The hardware is just some old junk parts that I randomly picked up, when I was cleaning my room.. So if not, I really don't care. But if you know any way to do this, please let me know. I could make it a file server so I don't have to fool with the many external drives I have.

Anywho, Thanks a lot!

---

### Post by cilkay on 2008-10-11
For your purposes, the differences between the server and desktop editions probably aren't important. The server edition has a different kernel, which you could install in the desktop edition anyway, and it doesn't install any GUI applications. If you're going to be using it for Windows file sharing, you'll probably want to install SWAT (Samba Web Administration Toolkit) in order to have a good and easy way of administering Samba.

---

### Post by cariboo on 2008-10-11
Just to expand on what Clifford said, if you install the server version over top of the desktop version you will end up without a gui, but because there is no gui it will run faster! I can think of no better way to learn linux than to see how much you can do without a gui.

Jim

---

