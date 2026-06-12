---
title: "Compatability between 10.04 and 12.04 libraries?"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by dcannon on 2012-10-18
Hi, 
 
I am new to Ubuntu (usually I administer Red Hat type Linux), so please bear with me if I have missed something obvious. 
 
I have been asked to upgrade the glibc, libglib, and pkg-config on my 10.04 server to the 12.04 versions. When I try to do this, I receive dependency errors. When I try to resolve those, I recieve more dependency errors. I have tried using apt-get (pointing to a 12.04 repository), as well as dpkg -i installing the actual .deb.files. I also tried synaptic. Still dependency errors. 
 
My question is, is this task possible or even wise? If it is possible, can someone please enlighten me :)
 
Thank you in advance

---

### Post by Cheesemill on 2012-10-18
Possible, maybe.

Wise, probably not.

If you need the 12.04 versions of library's then your best solution is to run 12.04.
Dependencies of some of the 12.04 library's may require other packages that are only available if  you are running 12.04.

---

### Post by Slim Odds on 2012-10-18
> **Cheesemill said:**
> Possible, maybe.

Wise, probably not.

If you need the 12.04 versions of library's then your best solution is to run 12.04.
Dependencies of some of the 12.04 library's may require other packages that are only available if  you are running 12.04.
I agree.... things are moving forward and the dependencies are too.

---

### Post by dcannon on 2012-10-22
Thank you for the replies. I am required to stay at 10.04, so moving to another version (while I would love to), sadly is not an option for me.

---

### Post by Slim Odds on 2012-10-22
> **dcannon said:**
> Thank you for the replies. I am required to stay at 10.04, so moving to another version (while I would love to), sadly is not an option for me.
If that's your requirement, then that's what you have to do. But if you stay with a two and a half year old version you will have to give up something.

---

