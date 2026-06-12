---
title: "tata photon plus data card not getting detected in ubuntu 11.10"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by vireshsb on 2012-01-25
Hi, 

I brought new Tata Photon+ data card . Do not know how to install Tata Photon+ in ubuntu 11.10 . 

When I tried by plugining it in its not getting detected so.

Can any one help me on the same.

Thanks and regards
Viresh SB
9980867000

---

### Post by mastablasta on 2012-01-25
thats'a  USB modem right? what does it give if you type
 
lsusb 
 
and
 
lspci
 
in terminal?
 
if it realyl doesn't detect it you will need to install drivers for it or find what chip it uses. you might get it working with ndsiwrapper or whatever it is called.

---

