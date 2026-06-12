---
title: "Install hangs"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by Ric95 on 2006-03-14
(moved thread )
I restart with the disc in, get the logo screen, hit 'enter' and it scrolls through some install steps, then stops at;
'66.448658 Unlink after no IRQ? Controller is probably using wrong IRQ'
It stops there. It doesn't let me esc. either.
I have a HP/Compaq(amd64) with the D recovery partition( I want to open a 3rd partition for Ubuntu), Is that D part. the problem, and should I make a new part. first?
thanks in advance.

---

### Post by Ric95 on 2006-04-01
Problem found. I have a Compaq/HP and this seem to happen a lot with all partitioning software.
The solution is to run Chkdsk on C: first.
( Command console,  Chkdsk C:/f .) Then the partitioner can kick in.:)

---

