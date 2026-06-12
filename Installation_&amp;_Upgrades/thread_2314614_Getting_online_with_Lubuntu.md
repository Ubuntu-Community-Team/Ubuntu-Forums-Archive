---
title: "Getting online with Lubuntu"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by chris9872 on 2016-02-22
Dear Experts
 
I should be grateful for your help with getting Lubuntu 15.4 (version 219) online. It is on live CD, and the computer is called
 
Hewlett Packard Pavilion desktop a.808.uk
 
This connects via an ethernet cable to a cable modem called
 
Motorola Surfboard 5100i
 
which in turn connects to a length of coax, as supplied by my broadband provider. The HP machine was bought about 8 years ago, as I remember. Windows 7 has replaced the pre-installed XP. Using boot options noapic/nolapic/nomodeset gets me as far as the purple desktop. But there is a whirligig churning away endlessly, on the taskbar where the network icon should be. Opening a terminal window to type
 
sudo service network-manager start
 
has no effect.
 
And typing
 
sudo service network-manager restart
 
yields the message
 
disconnected you are now offline.
 
Is all of this symptomatic of a missing driver? If I unplug the ethernet cable from the HP, and connect it to my new Windows 10 machine, I can get online without difficulty. Like right this minute for example. There isn't a problem with the network itself.

---

### Post by mörgæs on 2016-02-23
Hi, welcome to the fora.

First we should get the computer into a live boot, forgetting about web connection to begin with. Is it possible using Lubuntu 15.10?

---

