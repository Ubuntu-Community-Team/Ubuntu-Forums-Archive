---
title: "Synaptics and software botique broken in ubuntu mate Release 22.04.1 LTS"
date: 2022-10-15
forum: Installation &amp; Upgrades
---

### Post by Neon John on 2022-10-15
I just tried to install a package using synaptic package manager after the latest upgrade to Release 22.04.1 LTS (Jammy Jellyfish) 64-bit.  It returns this error message:



E: The value 'impish' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.




I've reinstalled the package using apt but no change.

Also Software Boutique does not load at all and I don't know the package name to apt.

Any help would be much appreciated.

John

---

### Post by Bashing-om on 2022-10-15
Neon John -

Ruh Roe :(
> 
Ubuntu 21.10 (Impish Indri) was the 35th release of Ubuntu, support ended on July 14, 2022.


take a look at your sources list files and remove the impish entry with your favorite text editor
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

as to >>
"tried to install a package -- Software Boutique does not load at all and I don't know the package name to apt."

I can not hazard a guess as to what package you may be referring to :D

[INDENT]in small steps
[INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by Neon John on 2022-10-16
> **Bashing-om said:**
> Neon John -

Ruh Roe :(


take a look at your sources list files and remove the impish entry with your favorite text editor
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

as to >>
"tried to install a package -- Software Boutique does not load at all and I don't know the package name to apt."

I can not hazard a guess as to what package you may be referring to :D

[INDENT]in small steps
[INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

My release is Release 22.04.1 LTS (Jammy Jellyfish) 64-bit, current.

I removed everything in /etc/apt containing "impish". and verified with

```

jgd@den:/etc/apt$ sudo grep -R impish *

```

Which returned nothing.  Yet synaptic is returning the same error.  

```

E: The value 'impish' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

```

It must be looking somewhere else. I executed this:

```

jgd@den:/etc$ sudo grep -R -i impish *

``` 

which returned nothing except a word in the dictionary.  

Where do I look next?

Re: software boutique, when I click on the menu item, nothing loads.  What package do I need to install to make Software Boutique work again.

John

---

