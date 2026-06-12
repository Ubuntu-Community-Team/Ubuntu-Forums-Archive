---
title: "emacs-snapshot font problem"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forcotton on 2008-09-17
Hi,
Just upgraded from hardy to Intrepid. The font rendering has changed; that can be changed back by adding
```
  <match target="font">
    <edit mode="assign" name="lcdfilter">
      <const>lcddefault</const>
    </edit>
  </match>
```
in the local.conf file. However, emacs-snapshot uses xft directly (I think). Adding 
```
Xft.lcdfilter: lcddefault
```
in my .Xresources doesn't seem to work. Is there a way to let emacs use the nice font rendering?

---

### Post by sge_kane on 2008-09-28
Is this what you want?
Don't know, why fontrendering isn't using xft per default in Intrepid yet.

```

echo "Emacs.FontBackend: xft" >> .Xresources 
xrdb -merge .Xresources

```

Cheers

---

### Post by forcotton on 2008-09-28
I do have xft enabled. My problem was emacs doesn't use the good lcd filtering. However, the problem is gone after I changed some link in /etc/fonts/conf.d/ . I am not sure which exact change caused it, I was tidying my local.conf. (There are multiple sections that exist as a file in conf.avail )

---

