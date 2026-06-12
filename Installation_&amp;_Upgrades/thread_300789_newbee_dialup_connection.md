---
title: "newbee dialup connection"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by larrybdl on 2006-11-16
Is there someone who could talk to me by phone with help with dialup internet connection I can call you or you can call me. running 5.04

3152896913
thanks larry

---

### Post by s_h_a_d_o_w_s on 2006-11-16
Most people would not really want to talk withn you on the phone, not because of you, but because people (myself included) are a little shy. There are alternatives.

You can search the forums for help
You can post a thread
You can PM, or email me (or other forum members)
MSN, Skype, etc.

But i'd recommend just posting your problem.

I would severly recommend upgrading to dapper. Everything works well and the internet connection sets itself up, out-of-the-box.

But open up a terminal (Applications -> Accesories -> Terminal) and type:

```
sudo pppoeconf
```

and it'll prompt for your pssword which you'l enter. It should guide you through setting up internet. :-) 

Cheers

p.s.: Welcome to the forums!

---

### Post by larrybdl on 2006-11-16
Thanks for responding at least. I just got this and installed 5.04 to try . My son is going to send me a newer version later. I have read some post but they quickly started refering to things I'm not familiar with so I thought a phone helper would be able to walk me through.
under addmin / network settings / modem connection
it says 
Interface pppo not configured

---

### Post by larrybdl on 2006-11-16
> **s_h_a_d_o_w_s said:**
> Most people would not really want to talk withn you on the phone, not because of you, but because people (myself included) are a little shy. There are alternatives.

You can search the forums for help
You can post a thread
You can PM, or email me (or other forum members)
MSN, Skype, etc.

But i'd recommend just posting your problem.

I would severly recommend upgrading to dapper. Everything works well and the internet connection sets itself up, out-of-the-box.

But open up a terminal (Applications -> Accesories -> Terminal) and type:

```
sudo pppoeconf
```

and it'll prompt for your pssword which you'l enter. It should guide you through setting up internet. :-) 

Cheers

p.s.: Welcome to the forums!

I tried your sugestion 
It says
 I found 1 ethernet device


It doesn't see my pci modem card 
Maybe its bad or could it need a driver and how do i go about obtaining and installing that

---

### Post by s_h_a_d_o_w_s on 2006-11-16
After it says found one ethernet device, press Enter. I'm not sure if that's what u mean but pressing enter continues the guide. I would recommend thou waiting till your son brings you the newer version, 5.04 if the first version of ubuntu. 6.06, dapperdrake, automatically sets up iternet connection. I would say wait till u can upgrade. Or you can order the CDs for free. shipit.ubuntu.com i believe.

cheers

---

### Post by Infamous Flame on 2006-11-16
> **larrybdl said:**
> I tried your sugestion 
It says
 I found 1 ethernet device


It doesn't see my pci modem card 
Maybe its bad or could it need a driver and how do i go about obtaining and installing that

Do you know what model of modem you have?

---

