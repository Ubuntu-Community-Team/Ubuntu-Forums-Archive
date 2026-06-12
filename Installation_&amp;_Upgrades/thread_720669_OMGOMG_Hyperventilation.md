---
title: "OMGOMG *Hyperventilation*"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by Exsecrabilus on 2008-03-10
Okay, so my laptop got screwed up so bad that whenever I turned it on, it would turn off immediately after.

So I pulled out the Ubuntu 7.10 installation disc my friend sent me and I tried to install it.....and it worked.

Except when I tried to use partial disc space to install it, it wouldn't work and I ended up using the entire disc space for the new installation.

Now, unable to get wireless Internet connection, I have tried inserting Windows installation discs and restarted the computer but it won't work!

Am I stuck with Ubuntu forver? :(

---

### Post by Pumalite on 2008-03-10
Post from Terminal, output of:
sudo fdisk -lu

---

### Post by Exsecrabilus on 2008-03-10
> **Pumalite said:**
> Post from Terminal, output of:
sudo fdisk -lu

1. What do you mean "output of"?

2. What will that command do?
Do I just insert the installation disc afterwards, during, or before entering that command into Terminal?

---

### Post by Pumalite on 2008-03-10
I thought you had and installed Ubuntu. If not, boot your Ubuntu Live CD and from: Applications>Accessories>Terminal, copy and paste my command and press 'Enter'; whatever is the result of that in the Terminal is the 'output'.
The command gives us a view of your drives and partitions and will let us know if you still have Windows or not.

---

