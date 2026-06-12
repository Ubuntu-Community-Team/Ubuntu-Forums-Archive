---
title: "Karmic 64 bit and ubuntu reastricted extras (flash0"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-08-05
Yes, another 64 bit flash question.
After borking 64 bit and flash install, I have reinstalled Karmic 64 bit.
Fresh install, I was going to install 'ubuntu restricted extras' package. But it wants to install a 'flashplugin-installer'.
With the borked install I just had, 'flashplugin-installer' was causing the problem I was having. So I am asking is it ok to install the ubuntu restricted extras package?
Also I know that there are many, many thread pertaining to 64 bit flash. I would wish for some one to please give me a terminal ready codes to install flash for my 64 bit Karmic. Every time I have tried it does not come out right. I am not good with installing .tar packages.
Thanks for any help provided :)

---

### Post by taavikko on 2009-08-05
the u-r-e contains the 32-bit flash. and ia-32 bit libraries to go with it.
Don't install this, install what you need separately.


Just download the .tar.gz file, extract the libflashplayer.so file where-ever you desire. then 
move it to /usr/lib/mozilla/plugins/ there you go.

If it is a hassle use 
"gksudo nautilus" to move it. restart browser and you're set.

---

### Post by DougieFresh4U on 2009-08-05
> **taavikko said:**
> the u-r-e contains the 32-bit flash. and ia-32 bit libraries to go with it.
Don't install this, install what you need separately.


Just download the .tar.gz file, extract the libflashplayer.so file where-ever you desire. then 
move it to /usr/lib/mozilla/plugins/ there you go.

If it is a hassle use 
"gksudo nautilus" to move it. restart browser and you're set.

Thanks for your input. Much appreciated.
I have major issues installing/extracting .tar files and I really do not want to mess this up again

---

### Post by taavikko on 2009-08-05
> **DougieFresh4U said:**
> Thanks for your input. Much appreciated.
I have major issues installing/extracting .tar files and I really do not want to mess this up again

extracting .tar* is easy, just click and choose the destination...
this is rather easy, since it only contains the .so file which then nees to be moved to appropriate place. no need for {configure,make,make install}

---

### Post by DougieFresh4U on 2009-08-05
> **taavikko said:**
> extracting .tar* is easy, just click and choose the destination...
this is rather easy, since it only contains the .so file which then nees to be moved to appropriate place. no need for {configure,make,make install}

Thanks. Got it (I hope) as youtube videos are playing correctly. :P:P

---

### Post by graaant on 2009-08-05
This might be silly, but I'm stumped!
I've put libflashplayer.so in /usr/lib/mozilla/plugins/
But simply cannot get FF to see it? 
about:plugins shows no plugins installed and cannot get any flash videos to work.

Am I doing something wrong?

---

### Post by nanog on 2009-08-05
> I've put libflashplayer.so in /usr/lib/mozilla/plugins/
But simply cannot get FF to see it? 

Maybe a permissions problem. Did you tar -xzf as root? You can also point firefox to pluging. I think it looks in a different directory if you had the 32 bit pluginwrapper version installed.

---

### Post by graaant on 2009-08-05
I ended up throwing the 32bit libflashplayer.so in there and it worked straight away.
Performance is probably going to suck, but I won't know until I have a chance to play around with it.

---

