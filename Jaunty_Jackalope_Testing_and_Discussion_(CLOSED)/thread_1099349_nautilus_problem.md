---
title: "nautilus problem"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by formol on 2009-03-18
Hi, 

When I click on folder in Places (Documents, Music, Pictures or Videos) in the standard menu in the bar or in the Cairo AWN menu, it open Audacious.
it dont open Nautilus

is this a bug I should report? or just a bad and weird configuration of my computer?  
I install Alpla6 while keeping the /home of 8.04.

thank you

---

### Post by taavikko on 2009-03-18
Click on places->computer does it open filebrowser
Then select any folder-> click on properties -> set open with ->open folder


If that don't help
Try to delete
```
rm ~/.local/share/applications/mimeapps.list
```
Does this remove the unwanted behaviour...

Bad thing is that you need to to settings again for wanted filetypes...

It's this bug
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

---

### Post by formol on 2009-03-24
thank you taavikko, you solve both of the problem I had.

---

