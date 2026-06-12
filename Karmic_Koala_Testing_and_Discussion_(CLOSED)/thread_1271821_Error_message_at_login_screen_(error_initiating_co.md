---
title: "Error message at login screen (error initiating conversation w/ authentication)..."
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cristomac24 on 2009-09-21
My problem is probably better suited for this board, I also posted this in the general help but there doesn't seem to be much response there, it's regarding Karmic (Netbook Remix):
 
---
 
(Karmic UNR alpha 6 is being used, clean install)
 
Still relatively new to Ubuntu (experienced Mac and Windows user), and when I launched my Dell Mini 9 this morning, I was greeted with an unpleasant message when I selected my name at the login screen:
 
error initiating conversation with authentication general failure.
 
I tried selecting the "other" account (I'm the only user of the computer) but the same message appears. I rebooted multiple times and I still can't login.
 
Google the error message and I found nothing relevant to my problem too... 
 
What do I do? :sad:
 
---

---

### Post by dblock110 on 2009-10-15
i have the same problem . i was messing with the keyring pop up disabling

im screwed hah

just before i set the grub bootloader timeout to 0 so i cant even get into windows . ...

---

### Post by homeofpoe on 2009-10-27
Had this same issue myself. Fought with it a while before it occurred to me...

Why not just undo the change, if this is the command you ran:
```
echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm
```

Simply:
```
sudo vim /etc/pam.d/gdm
DELETE: @include common-pamkeyring
```

---

