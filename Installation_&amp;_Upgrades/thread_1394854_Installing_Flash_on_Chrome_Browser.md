---
title: "Installing Flash on Chrome Browser"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by TheRainbowBitMe on 2010-01-31
Okay, so i'm not quite sure how to ask this or what all you guys need but I'm currently using the Google browser, Chrome. I would like to know how to install flash on it. I have read a few other sites about this, and they mostly just tell me to use Firefox. I would like to know if there is a simple way to get flash on Chrome.

I'm not sure what you will need to know to be able to help me so just tell me what you need and I will try to give you answers back as soon as possible.

---

### Post by giarca on 2010-01-31
The easiest option is to install the package flashplugin-installer. Now the Chrome browser recognize the plugin automatically.

---

### Post by TheRainbowBitMe on 2010-01-31
When I tried to install the flash plug-in, it wouldn't install and i thought that maybe i had downloaded something wrong or something so i have tried downloading it again and trying to install and it still didn't work.

---

### Post by foresthill on 2010-01-31
If this story is to be believed, Google has no interest in supporting Flash:

[http://www.fanboy.com/2010/01/why-flash-is-doomed.html](http://www.fanboy.com/2010/01/why-flash-is-doomed.html)

> In a way Adobe reminds me a great deal of Yahoo! and Sun — it’s a company from a previous era where it was the star but it hasn’t aged well. In the same way that Microsoft Office is under a disruptive threat from Google Docs you can see that all the key Adobe products could be next in line to be killed by the cloud and other disruptive forces that are changing the tech landscape.

**Is this the immediate end of Flash? No. However it’s the beginning of the end as other parties like Google and Microsoft have no interest in supporting Flash. **

---

### Post by RTrev on 2010-01-31
I simply downloaded Flash from the Adobe site, extracted the libflashplayer.so file, and put it in /opt/google/chrome/plugins and Chrome spotted and used it without problems.  I did it that way to try the 64-bit Flash, but I presume it would work equally well with the 32-bit variant.

---

### Post by Soul-Sing on 2010-01-31
> **rtrev said:**
> i simply downloaded flash from the adobe site, extracted the libflashplayer.so file, and put it in /opt/google/chrome/plugins and chrome spotted and used it without problems.  I did it that way to try the 64-bit flash, but i presume it would work equally well with the 32-bit variant.

+1

---

### Post by TheRainbowBitMe on 2010-01-31
Well i ask my sister who has had Ubuntu, for as long as i can remember, and she told me to try getting gnash. I tried that and still nothing. I don't understand. I used Chrome before i switched back to Linux and it was fine.

---

### Post by Soul-Sing on 2010-02-01
> **TheRainbowBitMe said:**
> Well i ask my sister who has had Ubuntu, for as long as i can remember, and she told me to try getting gnash. I tried that and still nothing. I don't understand. I used Chrome before i switched back to Linux and it was fine.

The latest Gnash works fine, but you have to uninstall flash-nonfree.

---

### Post by TheRainbowBitMe on 2010-02-01
How do i do that?

I'm sorry that I keep asking questions that seem like something i should know but I'm not use to Linux and how it runs yet.

---

### Post by giarca on 2010-02-04
If you want to use flash plugin for 64bit (alpha release for Linux) you have to download the flashplugin from labs.adobe.com then unzip it and move libflashplayer.so in /opt/google/chrome/plugins/
Is the right plugins directory for Google Chrome.

---

### Post by Soul-Sing on 2010-02-15
> **TheRainbowBitMe said:**
> How do i do that?

I'm sorry that I keep asking questions that seem like something i should know but I'm not use to Linux and how it runs yet.

Gnash is in the off. ubuntu repositories, and works fine with
youtube, etc.
but again all flashnonfree software has to be removed before installing gnash.

---

### Post by saif_held on 2010-02-15
Check these two:
[http://www.ghacks.net/2009/09/02/enable-flash-and-use-themes-in-google-chrome-linux/](http://www.ghacks.net/2009/09/02/enable-flash-and-use-themes-in-google-chrome-linux/)

[http://h3g3m0n.wordpress.com/2009/07/12/linux-chrome-flash-ext/](http://h3g3m0n.wordpress.com/2009/07/12/linux-chrome-flash-ext/)

---

