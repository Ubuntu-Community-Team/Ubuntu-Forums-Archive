---
title: "I deffintly messed up...big time."
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by Rival904 on 2007-04-17
Ok, so on my main machine, I installed the 64bit version of Edgy a few weeks back. And due to the fact of nothing working with that version (flash, etc etc) I decided to remove it, but I had no idea of the proper method. 

So I booted to the live CD, used the partion manager on the CD and deleted all the Linux partions, great right? Well, thats what I thought at first. 

I rebooted, posted as normal, then, it tried to load GRUB(which I thought was GONE) but apprently not, it obviously cant find it, and gives me an error, not allowing me to do anything or boot into XP Pro.

Fearing that I would loose all my data, I tried to install the 64bit version again, so I could boot normally, but now, I get an error saying it cant resize my HD. 

WTF happened and how can I fix it? I would love it if I didnt have to wipe my whole HD, but that looks like my only option as of now.

And yes, I am very new with Linux.

---

### Post by kornhead127 on 2007-04-17
Removing Linux will not remove grub if it is installed to the master boot record(mbr). Hopefully you still have your windows cd. A real one. Boot it up, get to the recovery console, wait for it to load. Select the partition with windows on it. Type your admin passowrd, hopefully you know it. And then type fixmbr. That will replace the master boot record and you'll be able to boot into windows. Happy computing.

---

### Post by Rival904 on 2007-04-17
I just did the fixmbr. I get to the XP boot screen, then my comp restarts.

---

