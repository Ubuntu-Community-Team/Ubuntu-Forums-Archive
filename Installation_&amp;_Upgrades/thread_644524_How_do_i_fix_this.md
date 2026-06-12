---
title: "How do i fix this?"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by CCBalla10 on 2007-12-19
well i tried to update my comp tonight and got this error...i'm sure its prly easy fix, but i don't know how to do it.

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181


anyone know how to fix it?

---

### Post by erfahren on 2007-12-19
you need to add the key for the repository

I have no idea what it is

---

### Post by CCBalla10 on 2007-12-19
well i think it was when i was trying to install avant..but its working fully...is there any way to remove the key?

---

### Post by erfahren on 2007-12-19
> **CCBalla10 said:**
> well i think it was when i was trying to install avant..but its working fully...is there any way to remove the key?
you added the repository to your /etc/apt/sources.list 

when you go to update apt expects the authentication key for the repository

you *could* remove the repository from your sources.list but you wouldn't receive updates for avant. If you went by a HowTo the key was most likely given in the guide. 

if not (or you don't have it bookmarked) you could search the forum for a guide that has the key in it.

otherwise see "Managing Authentication Keys" here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

(I must admit that I don't completely understand that, which is why I didn't link to it before! :D )

---

