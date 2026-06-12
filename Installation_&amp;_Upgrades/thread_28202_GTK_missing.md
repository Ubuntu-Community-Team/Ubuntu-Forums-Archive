---
title: "GTK missing??"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by Nob on 2005-04-19
so it is... i downloaded Ubuntu 5.04 and installed it.
i downladed XFCE-4.2, but i cant isntall it, it says i dont have GTK2 and GLIB installed... :) it has GTK and GLIB libraries [gnome is working fine], but i just cant compile any application that needs GTK or GLIB...
so i did next - GLIB installation from source went fine, but i couldnt install GTK 2.6 coz it needs pango, atk and glib. so I tried to compile pango, but it stops. for some odd reason, it is reporting some kind of font error.. :( so i cant compile pango, that means no GTK, and eventually - no XFCE, or any gtk application that builds from source...

anyone has solution?

---

### Post by Bob D. on 2005-04-19
Unless you have a real need, don't compile from source. Just enable the Hoary Universe repository and download the XFCE4 metapackage. This will give you version 4.2.1.1..

Very easy, no muss, no fuss!  ;-)

Bob

---

### Post by Nob on 2005-04-19
[QUOTE=Bob D.]Unless you have a real need, don't compile from source. Just enable the Hoary Universe repository and download the XFCE4 metapackage. This will give you version 4.2.1.1..

Very easy, no muss, no fuss!  ;-)

Bob[/QUOTE]
 you mean like... dont compile anything? to install everything from binary packages? 
oh well :) that should work... i got used to installing from sources.. .yey...

10x

---

### Post by az on 2005-04-19
...And if you want to compile something, you need developmental packages.  What you are running are just the binaries.  The -dev packages for those binaries include the ehaders eeded for other software to be compiled using them.

Example

xlibs and xlibs-dev

---

### Post by Nob on 2005-04-19
thats cool, BUT there is a problem...[as allways]

ubuntu doesnt have source code for linux kernel [/usr/src/linux-2.6.10.... ]
and i need source code for kernel if i want my modem to work :(

anyway, i have Lucent Win Modem, or LT modem, whatever..
is there any binary package driver for my modem?

---

### Post by Nob on 2005-04-19
so i found modem driver - and its dialing allright :)

but i cant access any web site, or connect to any IM accounts. i think it may be a dialer problem, so i downloaded gnome-ppp [will try it later], or i think that momething is missing in /etc/resolv.conf [i got same problem with gentoo... fixed later]

any clues?

---

### Post by globalspace on 2005-04-20
[QUOTE=Nob]so i found modem driver - and its dialing allright :)

but i cant access any web site, or connect to any IM accounts. i think it may be a dialer problem, so i downloaded gnome-ppp [will try it later], or i think that momething is missing in /etc/resolv.conf [i got same problem with gentoo... fixed later]

any clues?[/QUOTE]


if you can't connect to web sites you can check the DNS on /etc/resolv.conf

but i don't know if it resolve ...

---

### Post by Nob on 2005-04-20
see, as far as i know, rasolv.conf shold be empty, and dialer to write it with required DNS...
but it doesnt work...

should i reinstall ubuntu?

---

### Post by globalspace on 2005-04-20
[QUOTE=Nob]see, as far as i know, rasolv.conf shold be empty, and dialer to write it with required DNS...
but it doesnt work...

should i reinstall ubuntu?[/QUOTE]

well,
i don't know your case but i made my /etc/resolv.conf like this :


> 
nameserver 80.20.6.36 #Primary DNS
nameserver 212.216.112.112 #Secondary DNS
 

PS. That is my dns settings but you must search your provider's dns
;)

---

### Post by Nob on 2005-04-21
well damn it :(
i set the DNS, and still isnt working... ($&@#(@$

reinstall Ubuntu? 


and yes, what dialer are you using?

---

### Post by globalspace on 2005-04-21
[QUOTE=Nob]well damn it :(
i set the DNS, and still isnt working... ($&@#(@$

reinstall Ubuntu? 


and yes, what dialer are you using?[/QUOTE]


telecom italia  ;-)

---

