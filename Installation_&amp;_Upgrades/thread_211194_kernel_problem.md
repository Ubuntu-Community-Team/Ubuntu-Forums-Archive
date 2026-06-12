---
title: "kernel problem"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2006-07-07
I compiled and instaled 2.6.17.4 on ubuntu 6.06.  This was my first kernel compile/install..anywho..i did everything on a guide. I used my current config file for the new kernel ( i figured id have less problems) ..restarted booted into the new kernel..it loaded...but got a :
"Fetal Servor Error"
no screens found
XIO fatal IO error 104 (connection reset by peer)
on x server ":0.0"
after 0 requests ( 0 known processed) with 0 events remaing <_< 

so what can i do...i dont really wanna recompile...i will if i have to ( its a learning process) but is there anything i can do CLI wise at that stage...i can type int he terminal..just cant start X seems to me
PS the nvidia module not found

---

### Post by FenrisAbraxas on 2006-07-08
> **raffytaffy said:**
> I compiled and instaled 2.6.17.4 on ubuntu 6.06.  This was my first kernel compile/install..anywho..i did everything on a guide. I used my current config file for the new kernel ( i figured id have less problems) ..restarted booted into the new kernel..it loaded...but got a :
"Fetal Servor Error"
no screens found
XIO fatal IO error 104 (connection reset by peer)
on x server ":0.0"
after 0 requests ( 0 known processed) with 0 events remaing <_< 

so what can i do...i dont really wanna recompile...i will if i have to ( its a learning process) but is there anything i can do CLI wise at that stage...i can type int he terminal..just cant start X seems to me
PS the nvidia module not found

Hmmm you should use your old kernel to boot up and start over again.

Probably you missed some key drivers or filesystems.

Did you followed a ubuntu guide? :P

---

### Post by raffytaffy on 2006-07-08
Offcourse..i followed a guide i found here:P

---

### Post by raffytaffy on 2006-07-08
Well i solved some problems....first off..i forgot to relize..i need to get nvidia drivers from nvidia website..and not synaptic..since its a custom kernel...duh.....i did that..x started fine...but..no iptables ( no modules) and no sound ( confg problem) ..imma wait for next kernel to come out..and try again:P
So i installed 2.6.17.3 ..and everything works...except my iptables...it says..my kernel does not support  iptables...do i need to compile iptables from scratch?

---

