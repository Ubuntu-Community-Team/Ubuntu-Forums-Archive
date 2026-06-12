---
title: "Moonlight doesn't work"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by mistakentridgell on 2009-12-31
I installed moonlight-firefox-plugin using their website and using apt-get. I did not get any errors during installation.

But after restarting firefox, sites which need silverlight still ask me to install it. They somehow are not able to see that I installed moonlight.

Is there any way to fix it.

I read somewhere that changing apparmor profiles for firefox might help. But I dont know how to proceed in that direction. Any help will be highly appreciated

---

### Post by Cinch64 on 2010-01-01
I, also, have the same problem. At the website which runs Silverlight, my browser, firefox, ask's to install moonlight again and again. I am running Karmic 9.10 64 bit and Firefox ver. 3

---

### Post by pierocol on 2010-01-06
I have the same problem since I installed moonlight 2.0. Version 1 was working fine. I run ubuntu Karmic 9.10 and Firefox 3.5.6. I think I recently upgraded Firefox as well, without really noticing.

---

### Post by tanha on 2010-02-06
I also installed mono [no errors] from the repositories 

> Architecture: amd64
Source: moon
Version: 1.0.1-3ubuntu0.xul191build1


and firefox from the ppa's 

> Architecture: amd64
Version: 3.6.2~hg20100130r33550+nobinonly-0ubuntu1~umd1~karmic
.

It doesn't show up in the about:plugins and it doesn't work.

Any ideas?

---

### Post by bilalsana on 2010-05-13
i have the same problem, using lucid amd64! want to use the facebook client for silverlight..Help plz!

---

### Post by rickaron on 2010-09-28
I downloaded it from the website, seems to be installed ok, but it doesn't work for me either.

10.04 64 bit - amd

Please help - I spent many hours convincing my wife that switching the main computer from xp to ubuntu wouldn't impact - now no ITV!!! She is a convert apart from this though :)

---

### Post by SeijiSensei on 2010-09-28
What sites are they?  Moonlight doesn't support the digital rights management restrictions in Silverlight (for obvious reasons since it's open-sourced), so most sites that impose DRM controls over the stream won't work in Moonlight.  Typically these are sites that stream movies and videos whose rights-holders want to control access to and reproduction of their materials.

If, as I suspect, "ITV" refers to the British broadcaster, they probably only support Microsoft Silverlight for the reasons I just specified.

One alternative is to install [Virtualbox]("http://www.virtualbox.org/"), then create a Windows virtual machine that runs within Ubuntu.  I've done that in past years to watch the US NCAA Mens' Basketball Tournament over the Internet.

---

### Post by directhex on 2010-09-28
> **SeijiSensei said:**
> If, as I suspect, "ITV" refers to the British broadcaster, they probably only support Microsoft Silverlight for the reasons I just specified.

This is an old thread. Infuriatingly, ITV *did* work with Moonlight - until they dropped Silverlight and moved to Adobe Flash.

---

### Post by SeijiSensei on 2010-09-28
Guess I don't understand rickaron's complaint then.  His posting is from today.

---

