---
title: "Toshiba Software Modem"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by thunderson on 2005-11-17
Hi,

I have a Notebook Toshiba, it has a Intel 537aa modem (Toshiba Software Modem). Is there a way to install it on ubuntu 5.04?

---

### Post by phanboy_iv on 2005-11-17
I've got a Toshiba Software modem as well, and I just found out that while it shows up on my list of network interfaces, it's not detected for configuration.
Maybe the access point (e.t.c, /dev/modem) is mis-detected? Maybe someone who knows can tell us.

---

### Post by phanboy_iv on 2005-11-21
I found this page [http://linux.toshiba-dme.co.jp/linux/eng/reference.htm]("http://linux.toshiba-dme.co.jp/linux/eng/reference.htm"), and from this it looks as if my (soundcard-based) modem is not gonna work...oh well.

EDIT: This is an old page, I realized. I also found out that the Ubuntu package "sl-modemd" should let you use the modem if the right kernel module is present(it should be). Anyone try this?

---

### Post by the_pc_dude on 2005-11-30
How do you install your modem drivers I've Got an  Intel 537Ep Modem I've been close I get drivers to install but the autodetect Modem can't find the Modem.

---

### Post by phanboy_iv on 2005-11-30
That was my problem, Autodetect couldn't find the modem. Try installing "sl-modem-daemon" via synaptic and see if that fixes it. I don't know if it will work with your modem, though. Is yours a software modem? 
I was able to autodetect the modem after installing this, but I don't have a dial-up connection right know, so I can't do a full test.

---

### Post by the_pc_dude on 2005-11-30
Yeah, it will If you read the readme.txt in your driver dir it will because it's list it there I believe.

P.S Let me give My tutuorial that I used on hoary to get Intel 537Ep Modem to work and see if that helps you.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=533049](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=533049)

---

### Post by phanboy_iv on 2005-11-30
Oh, I forgot to make it clear that my modem is an ATI soundcard type, so I don't think sl-modem-daemon will work for ya'll. My modem has a kernel module installed by default(snd-atiixp-modem), so I jut needed the daemon to get things working.
 I'll have to go read up on Intel modems on the Winmodem page......

---

