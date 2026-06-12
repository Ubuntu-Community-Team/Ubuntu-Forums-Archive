---
title: "Installed Lucid, then XP, can't dual boot."
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by EmporerD on 2011-05-02
So I had Lucid Lynx installed, when it turned out I needed XP, made a new partition, installed xp, and then restored the grub bootloader. It boots into ubuntu just fine now, but I can't figure out how to bring up the dual boot menu. Does anyone know how this is done? Thanks

---

### Post by oldfred on 2011-05-02
Welcome to the forums.

Have you run this?

```
sudo update-grub
```

If that does not work, post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by EmporerD on 2011-05-02
Haha, yeah I forgot to do that. Everything working now, Thanks. :)

---

