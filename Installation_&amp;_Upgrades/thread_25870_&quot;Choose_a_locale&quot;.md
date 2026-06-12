---
title: "&quot;Choose a locale&quot;"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by Jaromba on 2005-04-11
During installation I am asked to "Choose a locale" 
and given three options (I am in UK.):
en-GB.UTF-8
en-GB
en-GB.ISO-8859-15

What do these mean?
And which should I choose?

---

### Post by erkki70 on 2005-04-11
Hi,
Assuming you're using Hoary this should do.  ;-)  
[QUOTE=Jaromba]
en-GB.UTF-8
[/QUOTE]

Welcome to Ubuntu!
Cheers,
Erkki

---

### Post by Jaromba on 2005-04-11
[QUOTE=erkki70]Hi,
Assuming you're using Hoary this should do.  ;-)  


Welcome to Ubuntu!
Cheers,
Erkki[/QUOTE]
 Thanks. I have opted for en-GB.UTF-8.
And thanks for your welcome!

I am trying Linux in order to learn computing - and so I would like to know what a "locale" actually is - and what the choices mean.

I would be grateful if anyone can point me to a good explanation.

---

### Post by erkki70 on 2005-04-11
Hi,
Locales are the languages, for example if you want to run Linux Ubuntu in French you have to install those files and run ```
sudo dpkg-reconfigure locales
```
The best way for you to learn about it is to write this command in a terminal:
```
man locale
```
man stands for manual, therefore you can type any command after that and you will get infos about it, actually that's a great start to get to know the environement and how powerful command lines are.

Hope this helps.
Cheers,
Erkki

---

