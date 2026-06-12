---
title: "How to change font in Google Earth 6"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by baumtopf on 2011-06-25
Hello Ubuntu users,

I get following problem, I cannot change the font in my installed Google Earth6. I would like to change the font, because the font is unreadable. I find in a forum that I can change the font in the following file: home --> .config --> Google --> GoogleEarthPlus.conf. and I read also that I set this entry:

[Render]
...
GuiFontFamily=DejaVu Sans
GuiFontSize=12
...
GuiFontWeight=70

in this GoogleEarthPlus.conf. Any changes in this file don't work, but the fonts with Arial work. Does anyone know how to change the font to a readable font, but without to use the fonts like Arial, Times Roman? I would like to use Open Source fonts for example Liberation Serif

I set the a picture in attachment to show you the unreadable font in Google Earth. 

Regards Juergen.

---

### Post by baumtopf on 2011-07-07
You do not need to install windowfonts. More likely use this: sudo apt-get install xfonts-75dpi xfonts-100dpi

---

### Post by manbill on 2011-07-30
To solve this issue, simply reinstall msttcorefonts.
I had this problem with 10.04 and I was going to get crazy looking on forums for a solution.

Finally it was more simple than I expected.

Cheers.
William.

---

### Post by adelani on 2011-09-19
> **baumtopf said:**
> You do not need to install windowfonts. More likely use this: sudo apt-get install xfonts-75dpi xfonts-100dpi

Thanks, it works properly, I'm using ubuntu 11.04

---

### Post by yugal on 2011-10-02
> **baumtopf said:**
> You do not need to install windowfonts. More likely use this: sudo apt-get install xfonts-75dpi xfonts-100dpi

Thank you so much, it helped me too.

---

### Post by namik2b on 2012-03-27
> **baumtopf said:**
> You do not need to install windowfonts. More likely use this: sudo apt-get install xfonts-75dpi xfonts-100dpi

thank you it is very helpful, but you need to restart your computer after install!

---

### Post by xfjhdz on 2012-04-25
Thanks [baumtopf]("http://ubuntuforums.org/member.php?u=1264204").  I'm new to Ubuntu and this makes it easier to wean from Windows.  I'm starting to become a believer.

---

