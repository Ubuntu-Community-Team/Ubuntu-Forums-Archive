---
title: "Change default editor"
date: 2006-05-23
forum: Installation &amp; Upgrades
---

### Post by saaz on 2006-05-23
Where do I change the default editor from nano to something else? I thought something like this should be in /etc/profile but I didn't notice it there.

---

### Post by Ramses de Norre on 2006-05-23
```
sudo update-alternatives --config editor

```

---

### Post by TheXanaX on 2006-05-23
[QUOTE=saaz]Where do I change the default editor from nano to something else? I thought something like this should be in /etc/profile but I didn't notice it there.[/QUOTE]

well I dont know how you open files? By terminal or GUI?
If you open a file in the terminal you could use [sudo gedit "filename.extension"]

Edit: didnt see the above post when I posted sorry.

---

### Post by saaz on 2006-05-24
[QUOTE=Ramses de Norre]```
sudo update-alternatives --config editor

```[/QUOTE]

Bedankt, Ramses. That did the trick! 

OT..I just brewed a Belgian Pale Ale using a yeast strain from Leuven 	=P~

---

