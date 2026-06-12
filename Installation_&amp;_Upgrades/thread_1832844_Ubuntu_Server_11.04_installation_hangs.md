---
title: "Ubuntu Server 11.04 installation hangs"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by PL04Mgt on 2011-08-25
I can't install Ubuntu Server 11.04 x64. I boot from CD and the installation stops responding after showing this screen:

[ATTACH]200759[/ATTACH]

My first thought was that maybe the problem is in my USB keyboard, but I tried another keyboard, the result was the same. Legacy USB support in BIOS is turned on, I even updated the BIOS just in case. No luck.

The most interesting thing is that 10.04 server installation doesn't hang, goes through all steps. But it doesn't recognize the network card :(. So the problem with 11.04 hang is definitely not in a malfunction of my hardware.

Motherboard Intel DH67CF (H67 chipset), CPU Intel Core i3 2100T with integrated graphics, 4GB RAM, network is integrated to the MB, a usual SATA HDD (AHCI is turned on in BIOS), a usual USB keyboard. This is pretty much everything.

---

### Post by mörgæs on 2011-08-26
Hi, welcome to the fora. 

Have you tried the alternate ISO?

---

### Post by YesWeCan on 2011-08-26
> **Nox Metus said:**
> I can't install Ubuntu Server 11.04 x64. I boot from CD and the installation stops responding after showing this screen:
If you get to the main menu screen try pressing F6 to select "nomodeset" (I think this what you so on the server ISO; haven't used it in a while). This sometimes mitigates graphics problems. It may be because you are using Intel integrated graphics it is getting upset. It may not be this at all but worth a try.

The alternate ISO is the desktop version.

---

### Post by PL04Mgt on 2011-08-27
> **mörgæs said:**
> Hi, welcome to the fora.Thanks :).

 
> **mörgæs said:**
> Have you tried the alternate ISO?Hmm... they are for the desktop versions. You mean check 11.04 text version installer with a desktop OS instead of server? How it can help to resolve the issue?

---

### Post by PL04Mgt on 2011-08-27
> **YesWeCan said:**
> If you get to the main menu screen try pressing F6 to select "nomodeset" (I think this what you so on the server ISO; haven't used it in a while). This sometimes mitigates graphics problems. It may be because you are using Intel integrated graphics it is getting upset. It may not be this at all but worth a try.It's text only installer, no graphics mode. It should work with any display chip, right? I'll try it anyway.

I have finally pulled it through by installing Ubuntu Server 10.10 (it didn't hang and recognized the network card in contrast to 10.04) and then upgrading it to 11.04.

---

### Post by mörgæs on 2011-08-27
Good, please mark the thread 'solved'.

---

### Post by PL04Mgt on 2011-08-27
Yes. Should I report a bug in the installer of Ubuntu Server 11.04 to somewhere?

---

### Post by CharlesA on 2011-08-27
You can try launchpad for reporting bugs.

I was going to ask which kind of keyboard you were using USB or PS/2, but it seems you got it working.

---

### Post by PL04Mgt on 2011-08-27
> **CharlesA said:**
> You can try launchpad for reporting bugs.Thanks.

> **CharlesA said:**
> I was going to ask which kind of keyboard you were using USB or PS/2, but it seems you got it working.Anyway... it's USB. This motherboard doesn't have other options.

---

### Post by CharlesA on 2011-08-27
> **Nox Metus said:**
> 
Anyway... it's USB. This motherboard doesn't have other options.

Ah ok. I was just wondering if that could have been part of the problem. Glad you got it working in the end tho. :)

---

### Post by PL04Mgt on 2011-08-27
> **YesWeCan said:**
> try pressing F6 to select "nomodeset"It doesn't help, btw.

---

