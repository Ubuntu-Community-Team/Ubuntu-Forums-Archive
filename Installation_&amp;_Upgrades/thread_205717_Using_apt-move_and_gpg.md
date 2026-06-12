---
title: "Using apt-move and gpg"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by uxohus2b on 2006-06-28
Hi,

I'm trying use apt-move to burn newly downloaded packages on a CD so I can install them on a PC with no Internet. 

For the most part, I've been able to follow the directions at: 

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

But I'm stuck at:
"Then we need to make Release.gpg, to make it you must already have your GPGKey set and ready to sign."

How do you exactly do this (set up GPGKey)? I ran "gpg" in the terminal and it asked me to "type a message" but I didn't know what to do after that. I guess this is a publc key cryptosystem (RSA or Rabin?). How do you make gpg accept my message?

Also, as I was doing exactly as the above howto said to do, it occured to me that there should be an easier way to download and transport packages. I'm talking about moving around a lot of packages, not just a few. Is there an easier way to do this?

Thanks for your help. 
Regards,
h.y.

---

### Post by jstueve on 2006-06-28
gpg --gen-key

---

