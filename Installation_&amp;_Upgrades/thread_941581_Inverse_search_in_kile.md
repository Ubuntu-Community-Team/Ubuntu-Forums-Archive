---
title: "Inverse search in kile"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by Feanor22 on 2008-10-08
Hi everyone,

This is my third day trying to use linux (ubuntu). In windows latex (Texniccenter) there was the possibility to click on the dvi and go to the line of the code refering to the image in the dvi. How can I do that in ubuntu kile?
I installed the kile based in a site but it create the dvi in the folder not openning by itself and not allowing for the inverse search.

If someone could help me...

Thanks

Renato

---

### Post by Feanor22 on 2008-10-10
Come on pleople.
Help your buddy here that just want to avoid the new office that is almost as good as latex to make math papers.

---

### Post by kforum on 2008-11-01
ok, if you had looked up the kile docs, you would know that...
basically you set kdvi to view dvis, and in kdvi set the appropiate settings(by clicking on, 'get this to work with kile', in the specials-options).
that should do it ;)

also, you need to set everything you can in the build sections to mode 'modern', form mode, 'default'.

now while thi works great in kde, and if you set kdvi as embedded you can have instant click n' switch reality... i still havent managed to get this fully on gnome.
so that means you are forced to click back on kile after hitting the middle mouse button...
instead of it minimizing one and setting the other on top ;)


anyways, good luck. 


cheers.

---

### Post by ck_tomato on 2009-03-05
In Kile, go to Settings - Configure Kile - Tools - Build.
Then choose LaTeX in "Select a tool" menu.
Under the General tab, in Options:
--src-specials -interaction=nonstopmode '%source'

(This also enables Forward DVI search.)

In Kdvi, go to Settings - Configure Kdvi - Dvi Specials.
Editor: Kile
Shell command: kile %f --line %l.

---

### Post by lethalfang on 2009-03-28
> **ck_tomato said:**
> In Kile, go to Settings - Configure Kile - Tools - Build.
Then choose LaTeX in "Select a tool" menu.
Under the General tab, in Options:
--src-specials -interaction=nonstopmode '%source'

(This also enables Forward DVI search.)

In Kdvi, go to Settings - Configure Kdvi - Dvi Specials.
Editor: Kile
Shell command: kile %f --line %l.

I was just getting frustrated with Kile with the same problem, ran into this post, fixed it. 
Thanks! :popcorn:

---

### Post by eudemus on 2009-04-09
Yes, and the other way to get the Kile end right is in
Configure Kile > Tools > Build > LaTeX
to choose "Modern" rather than "Default" from the 'select a configuration' dropdown.

---

