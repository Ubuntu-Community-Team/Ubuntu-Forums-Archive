---
title: "Vostro 200 Installation Issue"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Requiemforroksy on 2008-10-16
Hi everyone 

I am new to these forums and new to Ubuntu. I really want to try Ubuntu out. I have a Vostro 200 and I want to dual boot XP and Ubuntu. I downloaded Ubuntu but when I go to install it I get an error. I actually found the error and a solution to it but I am not sure how to use it. It can be found here:

[http://johnbokma.com/mexit/2008/08/05/fixing-the-vostro-hang-issue.html](http://johnbokma.com/mexit/2008/08/05/fixing-the-vostro-hang-issue.html)

The error described there is the same one I am getting. He said to make a script etc. but my computer skills are somewhat limited and I have no idea how to do it. I would appreciate any help you can give me. 

Thank you.

---

### Post by Partyboi2 on 2008-10-17
Maybe something else that might work is to add all_generic_ide as a boot option, this worked for someone else that was having this problem.
You can do this by booting the ubuntu disk and when you are at the main menu press F6 and at the end of the line add[FONT=monospace]
[/FONT]```
all_generic_ide
``` then press enter.
If this also works for you, you can make it permanent after you have installed ubuntu.

---

