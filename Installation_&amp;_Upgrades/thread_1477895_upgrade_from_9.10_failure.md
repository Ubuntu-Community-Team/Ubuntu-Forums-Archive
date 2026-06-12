---
title: "upgrade from 9.10 failure"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by kree8or on 2010-05-09
Hi, I used the internal upgrade route to upgrade to 10.04. Now all I get on boot is a black screen. I tried booting from a 9.10 disk but the lappy refused to boot from the cd. The computer is a ibm thinkpad x40.
Help!
cheers
Paul

---

### Post by ateale on 2010-05-09
[COLOR=black][FONT=Verdana]hey, i have same issue.  my laptop in a Panasonic Toughbook CF-18.  Any help i would appreciate[/FONT][/COLOR].

---

### Post by ateale on 2010-05-09
More information as to the error message i got is (error:no suitable mode found) and (error:unknown command "terminal") followed by the ubuntu boot logo, then goes to a blank screen.  Hope this is similar to what is happening to you paul, if not i will post to new tread.

---

### Post by kree8or on 2010-05-09
no, I dont get any error messages. I tried to boot from a 9.10 disk but the machine wont boot from cd for some reason.

---

### Post by kree8or on 2010-05-09
bump

---

### Post by Catharsis on 2010-05-09
It's generally considered poor forum etiquette to bump your thread less than 24 hours after the last post.

That said, try:
1) Hold down Shift while booting to get the grub menu.
2) Hit 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.

---

### Post by kree8or on 2010-05-10
> **Catharsis said:**
> It's generally considered poor forum etiquette to bump your thread less than 24 hours after the last post.[COLOR="Red"]sorry![/COLOR]

That said, try:
1) Hold down Shift while booting to get the grub menu.
2) Hit 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.
I held down shift and I got a message saying "grub loading" but then nothing happens, it just carries on booting to the black screen and fails to boot.

---

### Post by Catharsis on 2010-05-10
> **kree8or said:**
> I held down shift and I got a message saying "grub loading" but then nothing happens, it just carries on booting to the black screen and fails to boot.

...Really? That is *very* strange. Did you hold down Shift the entire time?

If grub really won't load, then you need to reinstall it:
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD

---

### Post by kree8or on 2010-05-10
> **Catharsis said:**
> ...Really? That is *very* strange. Did you hold down Shift the entire time?

If grub really won't load, then you need to reinstall it:
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD

i held down shift the entire time, but i cant use a liveCD because it wont boot from cd.

---

