---
title: "Paint.NET on Ubuntu"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Ubinity on 2008-07-15
Hey guys,

I just installed Ubuntu on my what *was* Windows Vista machine. LOVE IT!!!!! This is the best OS I've ever used!! 

Anyways I dislike GIMP (sorry gimp fans), and I love Paint.NET.
I've heard rumors that it's possible to install Paint.NET on Ubuntu, but I can't figure out how. I DID install Wine, but during installation it needs to download .NET Framework 2.0, which crashes the installation. 

Could someone PLEASE give me a detailed complete walkthrough of how to install Paint.NET on Ubuntu if it actually is possible? Thanks.

Dylan Taylor

---

### Post by mikewhatever on 2008-07-15
Not every Windows program can be run in wine. You should visit their home site and check if paint.net can.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by ilrudie on 2008-07-16
If paint.NET is pure .NET code it may run in mono.  If I understand correctly mono is an open-source cross-platform implementation of the .NET framework which should allow you to run pure .NET applications.  I could be wrong or perhaps mono does not completely implement .NET yet.  Might be worth checking out though.

---

### Post by Ubinity on 2008-07-16
> **ilrudie said:**
> If paint.NET is pure .NET code it may run in mono.  If I understand correctly mono is an open-source cross-platform implementation of the .NET framework which should allow you to run pure .NET applications.  I could be wrong or perhaps mono does not completely implement .NET yet.  Might be worth checking out though.

Ok, thanks, both of you. 
One more prob then. I've tried installing Mono from their website from the 'Other linux distributions' and 'Ubuntu' list. 
the Ubuntu version seems to not work (I haven't even found the download file) and the Linux distributions doesn't work once I download it.

So sorry to ask, but how do I download and install Mono? A step-by-step kinda deal would be nice. Sorry, I'm new to Ubuntu and I haven' quite figured things out yet.

---

### Post by ilrudie on 2008-07-16
In the terminal try ```
sudo apt-get install mono-runtime
```
You can also look it up in synaptic if you are more comfortable with a gui.  Synaptic is always a good place to look before resorting to crawling the web looking for packages.

---

### Post by Ubinity on 2008-07-16
> **ilrudie said:**
> In the terminal try ```
sudo apt-get install mono-runtime
```
You can also look it up in synaptic if you are more comfortable with a gui.  Synaptic is always a good place to look before resorting to crawling the web looking for packages.

Ok heres what is says:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Mono-runtime is already newest version
0 upgraded, 0 newly installed, 0 to removed and 0 not upgraded

```

If it's saying that Mono is already installed, I don't think that is the case. Paint.NET or any other .NET based app works.
Its probably a small problem that im completely oblivious to, sorry. Like I said this is only my third day with Ubuntu (love it)


Dylan

---

### Post by ilrudie on 2008-07-16
I tried running this with ```
/usr/bin/mono '~/Desktop/Paint.NET.3.35.exe'
``` and it brings up a window saying that .NET is not installed.  I'm not sure but maybe its looking at the version or something and its different from .NET to mono or maybe its missing some part of the .NET libraries.

---

