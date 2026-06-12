---
title: "Ubutnu configuration tools"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by gauvain65 on 2005-07-07
Hi there,

I just installed Ubtunu and am looking for a way to set the starting services.
Are there any tools for that in Ubutnu ? I couldn't find any...
I'm sure there something else than webmin for that...

Thanks for pointing me in the right direction.  \\:D/

---

### Post by mingus on 2005-07-07
Give a look at BUM (Bootup Manager) . . . it's in the repository.  Be sure to read the instructions on the website.

---

### Post by gauvain65 on 2005-07-07
Thanx,

Will this be on the install DVD or do i have to download it from somewhere ?

---

### Post by mingus on 2005-07-07
Not sure.  If not, it's just
$sudo apt-get bum

or use Synaptic to find and install it.

---

### Post by gauvain65 on 2005-07-07
I get the following message when i type sudo apt-get bum

E: Operation bum is not valid 

(original message is in french E: L'operation bum est non valable)

I typed this in a root terminal


Am i doing something wrong ?

---

### Post by mingus on 2005-07-07
[QUOTE=gauvain65]I get the following message when i type sudo apt-get bum
E: Operation bum is not valid 
[/QUOTE]

Oops, my bad.  It's:

$sudo apt-get install bum

---

### Post by gauvain65 on 2005-07-07
no problem , here is the message i get now....

 E: Impossible to find package bum


gee....

---

### Post by mingus on 2005-07-07
[QUOTE=gauvain65]no problem , here is the message i get now....

 E: Impossible to find package bum

gee....[/QUOTE]

Rats!  Double-bad on me!  It is in the Starter Guide in the Addon Apps section.  You need to download the .deb and install it.  It's not in the repositories.  Sorry about that.

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by gauvain65 on 2005-07-07
ok, i'll go check that, thanks for your help :)

---

