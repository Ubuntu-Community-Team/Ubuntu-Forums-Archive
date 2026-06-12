---
title: "How to check the installation went smoothly?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by linoox on 2010-04-29
Hi. I just installed Ubuntu but couldn't be sure that everything went well. I had some errors with the installation disk (certain fragment not read) but the entire installation went through anyway. Is there anyway I can check if it's alright? Thanks.

---

### Post by jjcv on 2010-04-30
You have not provided enough information to be able to get a full picture of what the problem might be.  Mu suggestion is to do an (in a terminal):

sudo apt-get update
sudo apt-get upgrade

if you get any errors then run

sudo apt-get -f install 

to see if that will fix them.

If these come out clean without an error then try a reboot.   (The proof is in the pudding).

Presumably you have backed up any important file already... if not then do so before you reboot.

---

