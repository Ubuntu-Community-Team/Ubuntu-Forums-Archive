---
title: "how to read pdf files using chm"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Abdel_eid on 2010-03-07
dear all;
  i want to know how to read a pdf file using a chm reader e.g: xchm
thanks.

---

### Post by mkvnmtr on 2010-03-07
I believe the chm reader is for reading chm files . There are a few pdf readers that you can install. Most releases come with one preinstalled and all you nhave to do is double click on the file.

---

### Post by wojox on 2010-03-07
You'll probably need to convert to text first.

```
man pdftotext
```


Remember .chm files are Microsoft Compiled HTML Help files

---

### Post by Abdel_eid on 2010-03-07
i convert it to text but nothing happened , the file is changed to text file that is opened by any text editor i also tried to open it by xchm reader but it refuses and i also tried to change the file extension from .txt to .chm but it doesn't work also
thanks

---

### Post by wojox on 2010-03-08
Sorry meant:

```
man pdftohtml
```

Then try:

```
pdftohtml -c test.pdf test.html
```

---

