---
title: "problem displaying php file in mozilla"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by aconite on 2007-03-14
im using ubuntu 6.06 dapper with
php5 and
apache 2

i have a php file which creates frames.i ve been running the file on windows and it displays fine in internet explorer.now im running the same file on ubuntu mozilla.
but it doesnt support the frames.i have tried mozilla 1.6 as well as mozilla 2 the prob persists.
do i need to update or install new packages???:confused: 



the code of the php file is
<HTML>
<BODY>
<P align="center">
<iframe 
name="n_top"
src ="/top.php"
width="100%" height="30%"
frameborder="0"
scrolling="no">

<P align="right">
<iframe 
name="n_right"
src ="/right.php"
width="30%" height="70%"
frameborder="0">

<P align="left">
<iframe 
name="n_left"
src ="/left.php"
width="70%" height="70%"
frameborder="0">


</iframe>
</BODY>
</HTML>

---

