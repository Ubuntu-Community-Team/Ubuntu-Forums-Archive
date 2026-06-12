---
title: "Installing EXT4 with Jaunty (new install)"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iheartubuntu on 2009-04-06
I'm installing Jaunty on my dads new netbook and wondering if Jaunty uses EXT4 by default or I have to manually partition my drive?

If I have to manually do it, what is recommended? Its an Acer 1.6ghtz Atom chip with 2gb memory on board.

When I select sda1, type ext4, and click "forward" it asks me to define a root file system, but when i do this and label it root, it still doesnt work. Do I need to create a swap partition too?

---

### Post by iheartubuntu on 2009-04-06
also, does the swap go at the beginning or end?

---

### Post by 0cton on 2009-04-06
it doesn't matter where the swap goes but ussualy its at the end :)
And ussualy a swap isn't required but (Highly) Recommended
/*Dissregard this I've read  your signature
Also you don't name it root its / for root (If i understood correctly)
Dissregard the above */

---

### Post by iheartubuntu on 2009-04-07
Thanks... I just copied my desktop Ihad in front of me also. When Ubuntu formated that (8.10) it put the swap at the beginning, so... thats what I did on this new system. I must say, EXT4 is incredibly fast.

---

