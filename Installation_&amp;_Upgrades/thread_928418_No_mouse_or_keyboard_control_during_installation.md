---
title: "No mouse or keyboard control during installation"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by spriite2903@yahoo.com on 2008-09-24
Hi,
  I'm trying to dual boot Ubuntu on my current comptuer, which is now running Vista. It is an HP s3200n AMD dual 4800+ with 1GB of ram. I have a ps/2 compatible mouse and keyboard. I dowloaded the newest version of ubuntu 8.04 iso file and burned onto CD. I rebooted the computer with the CD. I chose my language and picked to install. Once ubuntu loaded,  I lost control of the mouse and keyboard and was unable to complete my installation. I rebooted and checked the CD, which came out okay. I tried again and decided to run Ubuntu without installing. As soon as Ubuntu loaded, I lost control of the mouse and keyboard again. 
   I tried again today with an older version of xubuntu (7.1) and it still did the same thing.

Is there anything I can do to make Linux recognize my mouse and keyboard?

---

### Post by xeth_delta on 2008-09-24
> **spriite2903@yahoo.com said:**
> Hi,
  I'm trying to dual boot Ubuntu on my current comptuer, which is now running Vista. It is an HP s3200n AMD dual 4800+ with 1GB of ram. I have a ps/2 compatible mouse and keyboard. I dowloaded the newest version of ubuntu 8.04 iso file and burned onto CD. I rebooted the computer with the CD. I chose my language and picked to install. Once ubuntu loaded,  I lost control of the mouse and keyboard and was unable to complete my installation. I rebooted and checked the CD, which came out okay. I tried again and decided to run Ubuntu without installing. As soon as Ubuntu loaded, I lost control of the mouse and keyboard again. 
   I tried again today with an older version of xubuntu (7.1) and it still did the same thing.

Is there anything I can do to make Linux recognize my mouse and keyboard?

Are you sure the system is still running, and that only the keyboard and mouse get locked?

In any case, I would suspect some incompatibility which you might be able to address with some kernel parameters before boot. I don't recall which ones, but there have been many threads. Look for them and feel free to as any further questions.

---

### Post by spriite2903@yahoo.com on 2008-09-25
Its definitely the mouse and keyboard. Still no fix as of yet.

---

### Post by xeth_delta on 2008-09-25
> **spriite2903@yahoo.com said:**
> Its definitely the mouse and keyboard. Still no fix as of yet.

I see. Ok, can you please post the output of the following commands:
```
lspci
lsusb
sudo lshw -short
```
Please remember to use the CODE tags (# button in the posting window) when pasting the output.

---

