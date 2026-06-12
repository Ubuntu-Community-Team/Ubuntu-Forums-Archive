---
title: "error: invalid enviorment block, failed to boot default entries; HELP!!!!!!!"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by unknown23 on 2009-10-01
ok

so i have an acer aspire 1350, i was running jaunty; with little problems, but one day, all of a sudden, i had some big issues with my screen

so, i have friends who know more about linux than me

after some days of trying to fix this problem, my friends upgraded me to karmic

fixed the screen problem, but now my dvd drive does not work at all

so, now i did a reboot last night and i get this error message

error: invalid enviorment block, failed to boot default entries

so, i have some big problems, because i cant boot from a removeable device

my dvd drive is not working

so i cant boot from disc

i cant do a netboot

and, frankly; i am not very clever with linux, i have absolutely no idea what to do now

i need the kind of direction u would give to a two year old, really explicit, and step by step

problem is, i am not home, i am travelling, i need my computer to work ; that is why i have to travel, is because of work; pretty soon i am going to miss deadlines which if i dont meet, i am going to be fired

i need my laptop to be working, but i have no idea what to do and i am all alone; in a city where i know no one

pleqse help

---

### Post by Joe_Bishop on 2009-10-01
The latest grub2 has this regression, related to "environment block" for me too. I switched back to old good grub.

---

### Post by bedbug on 2009-10-01
while the system starts the GRUB2 
press e to edit grub
remove the line save_env recordfail
press CTRL+X to boot

---

### Post by unknown23 on 2009-10-01
that did the trick!   tannx one million, now i can get back to work

---

### Post by unknown23 on 2009-10-01
thanx for your help

but now i have a problem with when the computer boots up

i have some kind of see through panels with icons on it that are not active; i can not click on them to do anything 

the control panel or taskbar that was on the top, has dissapeared ..... this where i could click and access my programs, but now its gone

any ideas

---

### Post by emarkay on 2009-10-04
Why is this - This happened to me on an new install when I went to the "Recovery" mode.  Removing the line as instructed allowed this to proceed.

Is this a bug, has it been filed?

---

### Post by quique1hn on 2009-10-04
tks... that worked for me too.. It happend with alpha 6.. and fresh install of beta.. :P

---

### Post by emarkay on 2009-10-08
Bug Filed:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)

OP, mark post a solved :)

---

