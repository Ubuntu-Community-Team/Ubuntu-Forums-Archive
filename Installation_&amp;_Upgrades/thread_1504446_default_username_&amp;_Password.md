---
title: "default username &amp; Password"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by saeghe3000 on 2010-06-08
hi 
I have a wonderful problem during installation ubuntu .
I don't want use wubi . when boot with cd and choose "install ubuntu" or "try without install" , I go in a page with brown color that i should give username & password !
why ubuntu want user & pass when i didn't install ubuntu  ??!!???

I didn't have this problem with 9.04 or 9.10 . I cleaned previous ubuntu because had problems .

I get .iso file from ubuntu.com yesterday .

---

### Post by mikewhatever on 2010-06-08
That shouldn't happen, and you might want to check the downloaded iso file and the cd for integrity. Try also *ubuntu* for username and leave the password blank.

---

### Post by saeghe3000 on 2010-06-08
i checked this username and pass .
download link : [http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-i386.iso]("http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-i386.iso")
from this page : [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

---

### Post by Elfy on 2010-06-08
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

There's a link on that page on how to check the md5sum

---

### Post by saeghe3000 on 2010-06-08
thank you for your answers

i found new thing !
in the texts of background install appear this message :
sudo : invalid user : ubuntu

i understood that process installation make "ubuntu" user , and in my installation can't make this .

now my question is : could i boot with live ubuntu 9.10 and from that install 10.04 with mi .iso file( or extracted .iso file ) from my USB or hard ?how?

if not : i install 9.10 and upgrade with my .iso file or cdrom .
but how i can this ?

---

### Post by mikewhatever on 2010-06-08
> **saeghe3000 said:**
> thank you for your answers

i found new thing !
in the texts of background install appear this message :
sudo : invalid user : ubuntu

i understood that process installation make "ubuntu" user , and in my installation can't make this .

The installation process makes the user that you create, and apparently, the 'ubuntu' username is not a valid one. Simply choose another username.

> now my question is : could i boot with live ubuntu 9.10 and from that install 10.04 with mi .iso file( or extracted .iso file ) from my USB or hard ?how?
No.

> if not : i install 9.10 and upgrade with my .iso file or cdrom .
but how i can this ?
You can't upgrade using the Desktop cd. If you have to use a cd to upgrade, there is another type called Alternate.

---

### Post by saeghe3000 on 2010-06-08
> **mikewhatever said:**
> The installation process makes the user that you create, and apparently, the 'ubuntu' username is not a valid one. Simply choose another username.

no . i think that you didn't my mean . my mean was a user that make itself . for example did you make your username when boot in Live state? thus what the username that you loged in?
i think is made a user named 'ubuntu' by default in live satate and beginning process installation . during install could make  my user .


> **mikewhatever said:**
> You can't upgrade using the Desktop cd. If you have to use a cd to upgrade, there is another type called Alternate.

and how cand do this?

---

