---
title: "how to update 5.10 to 6.06 with out starting all over again"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by tim123 on 2006-06-15
i need some help in updating my laptop from 5.10 to 6.06

---

### Post by Arnaud_B on 2006-06-15
in /etc/apt/sources.list replace "Breezy" with "Dapper" everywhere it appears (with out the " ").
to do that: $sudo pico /etc/apt/sources.list
you make the changes, you save and then:
$sudo aptitude update
$sudo aptitude dist-upgrade
Good luck!
A.
PS: do that in a virtual terminal (Control+Alt+F1)

---

### Post by nanotube on 2006-06-15
or just open the update manager, and it should have a button that says "new version of ubuntu is available, do you want to upgrade" and just hit the "upgrade" button.
that will upgrade the packages and everything, but keep your personal files and settings and stuff.

---

### Post by tim123 on 2006-06-16
i tryed your metod but it came with an error 

"Only one software management tool is allowed to run at the same time"

"Please close the other application e.g. 'aptitude' or 'Synaptic' first."

how do i close it down so i can use update manager

---

### Post by Arnaud_B on 2006-06-16
It's far safer to close X before doing that and kill all the applications in it:
you do Control+Alt+Backspace and than Control +Alt+F1, then you login and do what I said before:
$sudo pico /etc/apt/sources.list
you make the changes, you save and then:
$sudo aptitude update
$sudo aptitude dist-upgrade
Hope this helps,
Good luck!
A.

---

### Post by tim123 on 2006-06-16
hi i got a small problem it is coming with an error "[ Error writing /ect/apt/sources.list:  Permission denied ]"

---

### Post by Arnaud_B on 2006-06-16
yes it is because you are not root you need to use sudo:
$sudo pico /etc/apt/sources.list
you enter your password
you change breezy for dapper everywhere and then you do:
Control+O and then Control+X and then:
$sudo aptitude update
$sudo aptitude dist-upgrade
and then you wait... :-)
A.

---

### Post by tim123 on 2006-06-16
what is the next step that i have to do? :cool:

---

### Post by Arnaud_B on 2006-06-16
hehe... you did all that? and it downloads?... so well you wait :-)
it gonna finish the download, then it will install and then you'll reboot to boot a new kernel... everything should work... you might have to take care of graphic driver possibly but everything will likely be fine :-)
congrats! ;-)
you might want to re-prelink all that later too :-)
A.
PS: you do Control+Alt+Del to reboot from a virtual terminal...

---

