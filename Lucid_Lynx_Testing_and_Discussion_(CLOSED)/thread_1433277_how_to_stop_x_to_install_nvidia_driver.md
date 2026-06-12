---
title: "how to stop x to install nvidia driver??"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2010-03-18
I can not boot into any recovery modes. Could not with karmic and now not with lucid, it scrolls text and then screen goes blank with blinking cursor.

How about switching to a console?
what do you do

---

### Post by Austin25 on 2010-03-18
When you are loging in, try setting the session box to xterm

---

### Post by sdowney717 on 2010-03-18
I found from terminal this works
sudo /etc/init.d/gdm stop

that dumps you to a blinking cursor
then with a whole lot of finagling the key like alt-F5 etc, you get a login prompt. 
So I tried my linux nvidia driver but it is the wrong one for lucid kernel. So I got to go get the right one.

---

