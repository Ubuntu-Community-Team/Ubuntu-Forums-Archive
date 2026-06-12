---
title: "cannot choose adobe acrobat as preferred program for pdf"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by telegiovi on 2012-05-08
Dear experts,
I am happy to have upgraded from ubuntu 11.10 to 12.04. It seems to be better. Only one thing I cannot do; that is opening pdf documents with adobe acrobat as preferred program. Each time I have to choose to open the pdf document with adobe but have not the chance to get it for ever so.
How can I do?
Thank you for a suggestion

---

### Post by Pilot6 on 2012-05-08
Right-click any pdf file, then choose Properties -> Openwith -> Choose Adobe and set is as default.

---

### Post by telegiovi on 2012-05-08
exactly here is the problem; if Right-click any pdf file, then choose Properties -> Openwith -> cannot choose
Acrobat because it does not appear in the available programs.  It appear only if I Right-click any pdf file and then choose "open with"....

---

### Post by WHiZZi on 2012-05-10
I've had exactly the same problem.

after a 
sudo dpkg-reconfigure acroread

It was fixed :)

---

### Post by telegiovi on 2012-05-10
Thank you. I tried it but got this result:

No LSB modules are available.
nspluginwrapper: /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so is not a valid nspluginwrapper plugin
No LSB modules are available

And it does not work. 
I also removed the software and installed it again, but without success

---

### Post by wojox on 2012-05-10
Have you tried editing the default list file? [How to set Adobe Reader to be default pdf viewer?]("http://ubuntuforums.org/showpost.php?p=11663196&postcount=9")

---

### Post by telegiovi on 2012-05-10
I am not sure which suggestion was the decisive one, but the fact is that now it works.
Thank you

---

