---
title: "Install problems on presario v6310us"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by jbrantley on 2007-06-06
Hello all, I have tried numerous times to install 7.04 on my 32 bit  Vista Presario V6310US laptop, 1gb RAM, 1.6 ghtz processor(AMD 64 Turion X2) The install stops, cd drive stops and nothing happens. As the install progresess initially I notice that there are items that say they failed to load, something also mentioned about firmware and some type of 'helper' it's not there long enough to write it down, I read about pressing f6 when it boots and I entered 'noapic irqpoll noirqdebug' this was supposed to fix a something in the BIOS I believe, I have moderate computer skills ( more than average) but this is an area I have never delved in before. I would be grateful for any help that anyone could give me.

---

### Post by jcaveman on 2007-06-07
You need some initial boot options to get the CD to load properly.  On the startup screen hit F6 and add the following additional boot parameters:

noapic irqpoll noirqdebug

then hit enter

---

