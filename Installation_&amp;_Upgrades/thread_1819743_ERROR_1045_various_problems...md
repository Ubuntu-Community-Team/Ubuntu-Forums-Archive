---
title: "ERROR 1045 various problems.."
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by undercash on 2011-08-06
ubuntu 10.4.2 x86-64

Hello,

today i noticed several problems with my server. one of them being a 1.1TO error.log for apache (that i rotated 2 days ago)

other is that i tried to remove (or install) mtop, for example, and it gives me the following output:


Suppression de mtop ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

this obviously wasn't like that before, what happened and what can I do?

thanks all

---

### Post by lisati on 2011-08-06
> **undercash said:**
> 
Suppression de mtop ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

This looks to me like a MySQL error message. I'm not familiar with using [MTOP]("http://mtop.sourceforge.net/") but suspect that there could be some setting somewhere that needs to be investigated to get it working with MySQL properly.

---

### Post by undercash on 2011-08-06
hmm so this would only happen with mtop, I thought I coulnd't install anymore packages..

---

### Post by undercash on 2011-08-06
Do you have any idea of what could create those process

[IMG]http://img268.imageshack.us/img268/1566/clip7i.jpg[/IMG]

For around 3 weeks, they randomly starts , adding a day or more, another threads will appear and starts loading more the cpu.

anyway to understand where this come from?

thanks

---

