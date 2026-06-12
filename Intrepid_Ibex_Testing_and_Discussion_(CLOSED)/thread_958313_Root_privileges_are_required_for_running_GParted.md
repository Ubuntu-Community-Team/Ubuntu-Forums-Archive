---
title: "Root privileges are required for running GParted"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pheedback on 2008-10-25
I upgraded to Intrepid Ibex Beta from Hardy Heron and when I try to click on specific links in the Places menu (Home, Desktop, Documents, Music, Pictures, and Videos) I get the error message:

Root privileges are required for running GParted
Since GParted is a powerful tool capable of destroying partition tables abd vast amounts of data, only root may run it.

I can get to my files by clicking on Computer in the Places menu, but I would like to get the other links working in the Places menu because it is so much easier. I have tried looking all over and have not found a reason or a solution as to why i am unable to click those links and have them work properly. Can someone help me in getting them to work or pointing me in the right direction? Thanks.

---

### Post by Polygon on 2008-10-25
it seems to be that its trying to open your folders with gparted rather then nautilus. maybe try right clicking a folder and make sure its set to open with nautilus?

---

### Post by pheedback on 2008-10-25
That fixed it. Thanks.

---

