---
title: "Problem with Sushi Huh"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by geromd91 on 2014-12-19
I'm not sure if this is the right forum, but here it goes. I have a 7 yo laptop that can't be connected to internet (network card is screwed for some reason) in which I installed Lubuntu. The thing is that I'm triying to use Sushi Huh to download some packages on my Windows PC (this one has internet obviously) but whenever I try to execute it I get this message:

Traceback (most recent call last):
  File "C:\Documents and Settings\User\Desktop\sushi-huh\src\il_cuore\lib\sushi_huh_PyHP.py", line 99, in __init__
    exec(python_script, globals(), locals())
  File "<string>", line 33, in <module>
ImportError: No module named 'sushi_huh_INIFile'

I have the latest version of python installed and everything, but I don't get why it's not working.

---

### Post by oldos2er on 2014-12-19
I think you'd have better luck contacting the developers of Sushi Huh, although since their software hasn't been updated for 4 or 5 years (according to sourceforge) that could be problematic.

Since you're asking about Windows software running under Windows, there's not much we can do for you here.

---

