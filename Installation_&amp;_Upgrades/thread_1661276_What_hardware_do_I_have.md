---
title: "What hardware do I have?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Philfalafelsophy on 2011-01-06
Nothing too hard to crack. I need to know what type of soundcard I have 'cause right now there's no driver installed for it. I downloaded the Device Manager but it's not giving me enough information for me to download an appropriate driver. But I guess the first step is having more info. Would gladly appreciate any free time devoted to my aid.

---

### Post by oldos2er on 2011-01-06
```
lspci
```

---

### Post by Philfalafelsophy on 2011-01-07
Thanks! That'll do.

---

### Post by Rubi1200 on 2011-01-07
Some other commands to find system information:

```
sudo lshw
```

For your question specifically;

```
sudo lshw -C multimedia
```

See here for more:
[http://manpages.ubuntu.com/manpages/lucid/en/man1/lshw.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/lshw.1.html)

---

### Post by mörgæs on 2011-01-07
The application **hwinfo** is another good tool for investigating hardware. 

Entering **hwinfo --help** gives a list of available switches.

---

