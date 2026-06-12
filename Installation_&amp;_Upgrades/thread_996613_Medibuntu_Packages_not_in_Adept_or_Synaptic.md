---
title: "Medibuntu Packages not in Adept or Synaptic"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by SneakPeak on 2008-11-29
Hi,

I wanted to install Acrobat Reader so I followed the instructions at:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Specifically I ran:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

And then:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

After doing this I thought that all the Medibuntu packages would be available in Adept or Synaptic so I could just search for Acroread or Acrobat and install it but unfortunately not.

I got everything installed by using 

sudo apt-get install acroread

I also installed the recommended and suggested packages again using

sudo apt-get install "Package Name"

So no problem really but why are the packages not listed in Adept or Synaptic??

Thanks

Sneaks:-?

---

### Post by doas777 on 2008-11-29
I think the pdf reader is in the ubuntu-restricted-extras package with java and flash and whatnot.

```
sudo apt-get install ubuntu-restricted-extras
```

have fun

---

