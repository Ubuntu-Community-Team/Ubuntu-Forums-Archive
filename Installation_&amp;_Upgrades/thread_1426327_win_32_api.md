---
title: "win 32 api"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by Abdel_eid on 2010-03-10
hey guys i am using ubuntu 9.10 and i am using netbeans c++ compiler but i 'm facing a great problem which is when working on a windows application on windows os it use win32 api which is not found on ubuntu linux so is there any alternatives.thanks alot

---

### Post by shriramrs31 on 2010-03-10
you can get many windows apps to run on linux with wine. If your windows app uses some special hardware, you need to look in cross-platform development direction. you can seperate application and hardware interface in your project. use a cross platform framework for application part (like qt, or .NET with mono) and implement hardware part once for windows and once for linux.

---

### Post by Mark Phelps on 2010-03-10
Maybe I'm misunderstanding your question, but in my own experiences, APIs are used for Development.  So, this is NOT the same as running Windows Apps using Wine, this is doing Windows development in Linux.

Thus, if you're asking can you use the Win 32 API to do development in Linux, I would have to say NO.

But, I've not actually tried it, so I defer to others who have ...

---

