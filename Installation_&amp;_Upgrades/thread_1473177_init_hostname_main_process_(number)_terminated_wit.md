---
title: "init: hostname main process (number) terminated with status 1"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Ihaveaproblem on 2010-05-04
Hi to all, I upgraded ubuntu 9.10 64bit to 10.04 64bit and I have now this strange phrase that appears a bit after boot-grub choose:

> init: hostname main process (number) terminated with status 1

Please, what means and how I can correct it?
Thank you
:confused:

---

### Post by Ihaveaproblem on 2010-05-11
up

---

### Post by DrAcid on 2010-05-17
I have the same problem... Only I have just installed Lucid, got some updates... And now it's showing this...
Irritating and dangerous[?] little...thing...

Anybody?

---

### Post by Ihaveaproblem on 2010-05-18
up

---

### Post by Ihaveaproblem on 2010-05-24
some idea?

---

### Post by al_erola on 2010-06-04
Yes, I am having this problem also with the same message.  I also tried to upgrade instead of a clean install.  I have to wait while some process recycles.  

Can anyone help with at least how to debug this?

Thanks

---

### Post by luceerose on 2010-06-04
I started to get this message after I edited /etc/hosts & /etc/hostname
to change the name of my computer.
I was thinking it had something to do with the fact that I used Japanese characters in my new hostname.
The new hostname still shows up on login screen & works for networking purposes, so it hasn't caused any problems. Only that message on startup.

---

### Post by Ihaveaproblem on 2010-06-04
This alert seems innocuous for me too but, anyhow, I'd like understand why ubuntu writes on my monitor this sentence every boot and how to resolve it!
;)
Some expert can help us please?

---

### Post by Ihaveaproblem on 2010-08-15
up

---

### Post by markackerman8@gmail.com on 2011-01-25
wow sooo many Questions and no answers.  There must be a general answer.

Yes I have it too, innocuous but irritating... ideas?

Mark

---

### Post by paze79 on 2011-01-30
Hi,

just got this fixed myself.

I think the problem started around a month ago when I changed my computer hostname. 
-> /etc/hosts AND /etc/hostname

Now I removed character _ from the name and problem solved. Ubuntu launches without errors.

Check if you have special characters in your hostname.


paze79

---

### Post by tahir.salfi on 2011-05-31
Asslam-o-Alaikum
 Dears i am also new to Ubuntu and i am using Ubutnu 10.04 LTS and i was facing same problem "**init: hostname main process (number) terminated with status 1**"
But now i have fix it with changing to some in my computer, i tell you how....
when i install ubuntu then give it my name **"Tahir" **and ubuntu installed with name of **tahir@desktop **on my computer.......
after some days i had changed my host name (**tahir-desktop**) to **"Tahir Mahmood"** then start to receiving on my log in "**init: hostname main process (number) terminated with status 1**"
Dears i have changed my host name "**Tahir Mahmood" **to "**tahir-desktop**" again....

Now i am not receiving that "**init: hostname main process (number) terminated with status 1**"


Tahir Mahmood:KS

---

### Post by Wtwine on 2011-09-24
Changing "_" to "-" in my computer hostname did the trick

Edit using  gksudo gedit /etc/hostname

---

