---
title: "Ubunt on my Laptop"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by Jhodytropical on 2005-08-30
Hi,
 I have a Gateway Laptop 7326GZ - P4 : 3.06, 512 Ram- 80GB Hd. It came with Windows XP that I would like to flush and install Ubuntu. When I tried the live Cd it didn't recognize my Wireless connection and that I really need.
 Would you suggest a dual boot or anything else ?

Thanks in advance

---

### Post by stoffe on 2005-08-30
[QUOTE=Jhodytropical]Hi,
 I have a Gateway Laptop 7326GZ - P4 : 3.06, 512 Ram- 80GB Hd. It came with Windows XP that I would like to flush and install Ubuntu. When I tried the live Cd it didn't recognize my Wireless connection and that I really need.
 Would you suggest a dual boot or anything else ?

Thanks in advance[/QUOTE]
 Didn't it find it at all, or does it report it as unknown? Can you find it in System->Administration->Networking?

IMO, dualbooting isn't going to help this particular matter, if you need to use the wireless connection and it only works in Windows, you're just going to use Windows, right? =) Better to try and figure this one out (or if it isn't possible, wait a little with your switch).

I've gotten several different laptops to work out of the box with wireless, only thing I've neede to do is add the WEP key.

---

### Post by shakin on 2005-08-30
[QUOTE=Jhodytropical]Hi,
 I have a Gateway Laptop 7326GZ - P4 : 3.06, 512 Ram- 80GB Hd. It came with Windows XP that I would like to flush and install Ubuntu. When I tried the live Cd it didn't recognize my Wireless connection and that I really need.
 Would you suggest a dual boot or anything else ?

Thanks in advance[/QUOTE]
 I would try installing Ubuntu then using the NdisWrapper ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)) to get the Windows driver running on Linux. You can add the Debian repository (deb [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./) to /etc/apt/sources.list and then use Synaptic to intall NdisWrapper. I have no idea if using the Debian deb will break anything, so be careful. Maybe someone else here has tried it. I bet there is a how-to in the Tips & Tricks forum.

---

### Post by Jhodytropical on 2005-08-30
[QUOTE=stoffe]Didn't it find it at all, or does it report it as unknown? Can you find it in System->Administration->Networking?

IMO, dualbooting isn't going to help this particular matter, if you need to use the wireless connection and it only works in Windows, you're just going to use Windows, right? =) Better to try and figure this one out (or if it isn't possible, wait a little with your switch).

I've gotten several different laptops to work out of the box with wireless, only thing I've neede to do is add the WEP key.[/QUOTE]

Thanks for your prompt answer.
 The problem is before installing Ubuntu I tested my Laptop with the LIVE Cd to see if everything was ok and apparently my Wi-FI Connection didn't show up. when I tried to locate it the network tools even though I enter the specs for the card it won't see it.

 Since I really need that Wi-fi connection for my Internet I can't take a chance to install Ubuntu and lose that.

I do like UBUNTU but I also want to be On Line.

Maybe I should consider a dual boot

---

### Post by fparri on 2005-08-30
What is the output of lspci?

---

### Post by Jhodytropical on 2005-09-05
It doesn't show my Wi-fi connection. Only my Ethernet card shows. And Gateway tells me they are not supporting Linux at this time if I want to put Ubuntu on the Laptop I'll be on my own.
 I really want to switch to linux.

---

### Post by Shaggy on 2005-09-05
If you're laptop is anything like mine, which it most likely is since they're from the same company, you're using a broadcom chipset on your wireless card.  If you do lspci -v | grep Broad, it'll most likely show up there.  Just use the windows driver that came with your computer ( download it from the gateway website). Use ndiswrapper with that and it should work like a charm, I even use the ndiswrapper deb that comes with ubuntu.  Read the ndiswrapper how to about resetting the radio function if you have problems.

---

### Post by Jhodytropical on 2005-09-07
thanks,
 
 I will give that a try. In the meantime I opted for a dual boot following the directions giving in an earlier forum regarding downloading sysresccd and partition my hard drive for Ubuntu and XP, unfortunately it gave me a memory error and was not able to continue.
 Any other program that you know that will partition the hd (for free).
Thanks

---

