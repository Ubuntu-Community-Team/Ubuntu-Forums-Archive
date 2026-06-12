---
title: "how to convert . pdf to .eps"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by nehakapila on 2010-08-30
hello everyone!
kindly suggest me how to convert .pdf to .eps.
i have installed Imagemagick for this conversion but may be its not installed properly.its giving me an error "install libLTLIBRARIES".i dont know from where i can get it.
or is there some other way to convert .pdf files to .eps files in ubuntu?
then please help me
thank you in advance
neha:confused:

---

### Post by kindlychung on 2011-03-27
```
sudo aptitude install ps2eps
ps2eps -f input_file output_file
```

-f mean force overwrite

---

### Post by dingodog on 2011-03-27
> **nehakapila said:**
> hello everyone!
kindly suggest me how to convert .pdf to .eps.


first of all you need to say us if you

- want keep *vector format*
- want simply wrap your pdf in an *EPS container*

assuming you want do the first thing (keeping vector), imagemagick is not the proper software to perform this task

you can:

- use **Gsview** + **pstoedit**
- open your pdf
- convert in **EPS** format

or use ps2eps but first you must convert pdf in ps with

**pdftops** (different from pdf2ps that is a ghostscript wrapper)

pdftops (part of poppler utils) is able to perform conversion more reliably  

then on your ps you can use **ps2eps**

---

