---
title: "NAM is not working"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by NemiRathore on 2010-03-05
I am using ubuntu 9.1 and i have installed NS2-2.33 ,but when i run any tcl script i am getting following error message....


nemi@nemi-desktop:~/Desktop$ ns ns-simple.tcl
CBR packet size = 1000
CBR interval = 0.0080000000000000002
nemi@nemi-desktop:~/Desktop$ nam: 
[code omitted because of length]
: no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D / 120) * 4}] units
}"
    invoked from within
"if {[tk windowingsystem] eq "classic" || [tk windowingsystem] eq "aqua"} {
bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D)}] units
}
bind Li..."






Plz somebody guide me to solve this problem. Thanks.

Regards 

Nemi Chandra Rathore

---

### Post by Ashish Nayan on 2010-04-01
I too have the same problem ne1 plz help to get rid of that...
plz help

---

### Post by Ashish Nayan on 2010-04-02
did u got the solution..
if yes then plz help me 2...
i'm also gttng d same problem...

---

### Post by sumiitkgp on 2010-05-17
nam: 
[code omitted because of length]
: no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D / 120) * 4}] units
}"
    invoked from within
"if {[tk windowingsystem] eq "classic" || [tk windowingsystem] eq "aqua"} {
bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D)}] units
}
bind Li..."
[B]


Having the same problem. Kindly reply.
[/B]

---

### Post by neoragexxx on 2011-03-12
to those still looking for a solution , this link contains the patches needed to solve this :

[http://bugs.gentoo.org/show_bug.cgi?id=225999](http://bugs.gentoo.org/show_bug.cgi?id=225999)

just apply the first 2 . 

cheers

---

