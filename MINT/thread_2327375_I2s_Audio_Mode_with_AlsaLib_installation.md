---
title: "I2s Audio Mode with AlsaLib installation"
date: 2016-06-10
forum: MINT
---

### Post by noam4 on 2016-06-10
Hi everyone,

I would like to use my laptop (Delll xps 13 2015 9343) with audio mode set to I2S because I am working in a dual boot system, and windows works only with I2S and not HDA.
In order to do that I upgraded the Kernel to 4.4, as instructed in the [Arch Wiki page of the laptop]("https://wiki.archlinux.org/index.php/Dell_XPS_13_%282015%29#I2S_mode").
Despite I did that, I2S Isn't recognized yet because I didn't install [AlsaLib]("https://www.archlinux.org/packages/?name=alsa-lib"), Which I don't know how to install.
I would like to be instructed on how to install this package.

Thanks,
Noam

---

### Post by howefield on 2016-06-10
Which operating system are you dual booting Windows with ?

---

### Post by noam4 on 2016-06-10
I am dual booting linux mint 17.3 with XFCE and Windows 10

---

### Post by howefield on 2016-06-10
OK, thread moved to the "*MINT*" sub forum.

I know nothing about Linux Mint so hopfully someone will come along to help you.

There is an alsa-lib package that you should be able to install with apt-get or the Software Manager included in your distribution.

---

### Post by noam4 on 2016-06-10
I didn't find that apt-get. Can you specify the command?

Alright found it
sudo apt-get install libasound2
But it doesn't help.
When I am running kernel 4.4 I2S mode Isn't detected in alsa-lib and wifi driver disappears, no matter what I do...

---

### Post by Rob Sayer on 2016-06-10
First thing I'm wondering is why you feel you need to implement I2S audio in Mint just because you are dual booting with Windows?  I see no connection there, and this looks like the sort of thing you'll be up against:

[http://www.udoo.org/forum/threads/using-i2s-audio-output.2097/](http://www.udoo.org/forum/threads/using-i2s-audio-output.2097/)

Second thing is that you are copying things from Arch while perhaps not realizing it is a rolling release distro and not a fixed release one like ubuntu and mint.  Do NOT assume that you can just cut and paste solutions from their tech support.  Their support is great, I often recommend it for non arch users, but it isn't noob level stuff.

---

