---
title: "Getting wireless going in HH"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by yogo on 2008-05-20
Is there an easy way to get wireless going on HH, it does not work out the box.

Feisty does work and has the right drivers installed, it has been quite a while since I did install them on Feisty.

Can I just copy the installed drivers over to the same place on an HH install? What I am getting at, is there a simple way to get the wireless going by borrowing what is already working on Feisty?

It took quite a bit to get that working and would like to simplify things, I take it I will still have to use ndiswrapper?

TIA

---

### Post by dstew on 2008-05-21
First check to see if you have any restricted drivers for your wireless card in System --> Administration --> Hardware Drivers. If so, activate them. If you have to use ndiswrapper, press alt-F2, and enter```
gksudo ndisgtk
```If the Windows drivers are in still on your disk, you can navigate to them and use them. They should work as well in Hardy as in Feisty. However, linux native drivers are often specific for a particular kernel, and native drivers that worked with Feisty will probably not work well with Hardy, because the kernels are different.

---

### Post by yogo on 2008-05-21
> **dstew said:**
> First check to see if you have any restricted drivers for your wireless card in System --> Administration --> Hardware Drivers. If so, activate them. If you have to use ndiswrapper, press alt-F2, and enter```
gksudo ndisgtk
```If the Windows drivers are in still on your disk, you can navigate to them and use them.   So what you are saying is, is that HH should work out of the box?  In other words if I enter this in terminal gksudo ndisgtk, it will work in HH? Simply because last night I went to synaptic to add ndiswrapper but it was not able to download as there is not an internet connection yet,

Or would I be better using a falsh card to put everything on that like ndiswrapper etc.

I have a 
**[SIZE=1][COLOR=black] 					EDIMAX EW-7128G IEEE 802.11b/g PCI Wireless Card[/COLOR][/SIZE]**

 that is suppose to work but was a pain to get going on Feisty, is there support for the native driver in HH?

TIA

---

### Post by dstew on 2008-05-22
Ndisgtk is a graphical front-end for ndiswrapper. I do not know if there is a native driver in HH. Did you check for a restricted driver?

---

