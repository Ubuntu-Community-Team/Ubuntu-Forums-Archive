---
title: "nautilus won't start from cairo-dock"
date: 2010-01-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-01-31
I can't get nautilus to start from cairo-dock , it don't mater if I create the launcher or let cairo-dock do it . I have tried modifying the cmd ( added %f , used full path etc ) without sucess , if I start nautilus from my desktop launcher and then minimize to the dock it remaximizes ok . Any ideas ?

---

### Post by mdurham on 2010-02-01
It works ok for me. 
Make sure the command is: "nautilus --no-desktop --browser " without the quotes of course.
Image's name is: system-file-manager

---

### Post by fabounet on 2010-02-01
it should end with a dot :
> nautilus .
is enough

---

### Post by ronacc on 2010-02-01
thanks for the tips . the dot works for me , nautilus --no-desktop --browser   does not .

---

### Post by AlanR8 on 2010-02-01
Try this as the command in Cairo

> nautilus /home/username

Clearly replace username with your own username!

This one did by box for a few weeks some months ago but works for me now....

---

