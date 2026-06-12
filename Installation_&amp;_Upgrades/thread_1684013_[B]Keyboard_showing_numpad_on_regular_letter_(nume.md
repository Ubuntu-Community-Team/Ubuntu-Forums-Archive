---
title: "[B]Keyboard showing numpad on regular letter (numeric pad its separated on my pc)[/B]"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by Josunik on 2011-02-08
I have an HP-Pavilion Laptop with numeric pad of its own which works fine; I did a fresh 10.10 maverick install. I noticed that my keyboard goes numeric (I mean it becomes numeric on the jkluiop letters) after I press the num lock key, everything else works fine for now, I tried the different layouts, but so far nothing has worked.

here is what I get when the numlock key is on

L=3
K=2
J=1
U=4
I=5
O=6
P=*

and so on...

I would like to use my numeric pad as normal without having to activate it every time. or for the defect deactivating it for normal keyboard use

thanks to all in advance

---

### Post by Josunik on 2011-02-08
Numlock - how do i prevent it from changing my alphanumeric keys into numbers?
I have an HP Pavillion laptop with an embedded number pad.
When I press numlock in Ubuntu, it allows me to use the number pad numbers (when numlock is off, the keys on the number pad act as arrow keys), but it also changes some of my keys (such as K,L,I,O) into numbers.

I understand that this is useful on laptops that dont have a separate number pad, but is there any way to disable this feature and only make Numlock activate my number pad?

---

### Post by Josunik on 2011-03-03
here is a trick that did it for me its not a solution but it works

Re: Numlock - how do i prevent it from changing my alphanumeric keys into numbers?

Code:

sudo gedit

open /etc/gdm/Init/Default

Find the line

exit 0

Add the following code above that line

Code:

if [ -x /usr/bin/numlockx ]; then
        /usr/bin/numlockx off
      fi

save and restart your pc,

the outcome will be that every time you boot your computer numlock will be on and your numpad will work as numbers and your alphanumeric will be fine also.

PD: if you cannot get to the right path on terminal get to the file trough 
typing into terminal *sudo nautilus* but be very very careful not to change anything while you are logged in as a root.

---

