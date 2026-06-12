---
title: "help-black screen"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by lafolla on 2008-04-27
hi to all
i m trying everything
i ve got a nvidia geforce2 mx
a samsung 17 710n
i cant see
i have to use a old crt
heplp pleaseeeeee

 Angry

---

### Post by lafolla on 2008-04-27
is everybody??????????????????

---

### Post by white_rule on 2008-04-27
Hi, it may be depends on your LCD vertical or horizontal frequency...
can you login under the text mode or recovery mode with no X ?

---

### Post by lafolla on 2008-04-27
yes
but if i use my lcd
i can see nothing
and it s working (i ve tried it on another pc)
the resolution is low and it becomes all bòack....

---

### Post by lafolla on 2008-04-27
help
im so newbie....

---

### Post by white_rule on 2008-04-28
it's very easy for config,
1- find your LCD or CRT specification, look for values named Horizontal Frequency and Vertical Frequency. 

2- Open the file /etc/X11/xorg.conf
3- Locate the section "Monitor" 
4- Write the values you found in step 2 in the "Monitor" Section like so :

HorizSync 31-81
VertRefresh 56-76

and do it,

for more information search about it, many of users and moderators that help to others don't reply any thing for these topics, because you can find the solution with search on the forum, or google and another search engines.
following URL can help you:


[http://ubuntuforums.org/archive/index.php/t-285125.html](http://ubuntuforums.org/archive/index.php/t-285125.html)

---

