---
title: "About To Upgrade To 12.04 - couple quick questions on Encryption"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by johnsmoke on 2014-04-22
My existing version of Ubuntu hasn’t been supported for quite some time now, so I’m going to upgrade to 12.04 this weekend, I’m just getting all of my facts together before doing so. I’d like to have the entire hard drive encrypted upon installation…. Does the ISO disc I made of Ubuntu 12.04 have this option upon installation? I’ve been reading that this option is only on the “alternate” installation… what IS the “alternate” installation anyway?
 
If full disk encryption is not available upon installation, would the easiest option be to just use TrueCrypt to encrypt the drive after I install 12.04, as long as I do it before transferring my data to the newly installed OS?

---

### Post by EmpireITtech on 2014-04-22
Quick question: is there a reason you're not going to 14.04 that was just released?

But to your question: I do not believe 12.04 LTS has the full disk encryption as an option when installing (I believe that started with 12.10). You should be able to follow this to get it done in 12.04 > [http://www.rationallyparanoid.com/articles/ubuntu-12-lts-security.html](http://www.rationallyparanoid.com/articles/ubuntu-12-lts-security.html)

---

### Post by johnsmoke on 2014-04-22
> **empireittech said:**
> Quick question: is there a reason you're not going to 14.04 that was just released?

But to your question: I do not believe 12.04 LTS has the full disk encryption as an option when installing (I believe that started with 12.10). You should be able to follow this to get it done in 12.04 > [http://www.rationallyparanoid.com/articles/ubuntu-12-lts-security.html](http://www.rationallyparanoid.com/articles/ubuntu-12-lts-security.html)

Oh, sorry, I haven't been keeping up with the releases! Last I checked, 12.04 was the LTS release at the time I created the ISO disc. Well, I guess it makes sense than to just go with 14.04 since it will be supported longer anyway. I'll create the disc for that today.

So, based on that, I'm sure that 14.04 would have the option for full disk encryption as well since it's even newer than 12.04?

Also, if you can answer this one last question for me, another encryption q: I'm also getting a new flash/thumb drive. I'd like to encrypt this as well - I want to encrypt it so that it's accessible on both my Ubuntu machine as well as windows machines - now I know the default encrypt tool with Ubuntu is dm-crypt, however I've read that the way that is accessible in windows is with FreeOTFE, but FreeOTFE is abandoned at this point, so it may not be the best solution for accessing Ubuntu encrypted flash drives on a windows machine? In this case, would TrueCrypt be the best way to encrypt this thumb drive since TrueCrypt is readily available on Windows machines?

---

### Post by EmpireITtech on 2014-04-22
Lol, yes 14.04 came out 4/17/2014 and I believe it does have the full disk encryption available.

As far as TrueCrypt goes, I've never personally used it (never had a need for encrypting anything lol) but I do know people that use it on both Windows, Mac and Linux. There are however some requirements that you can read about here > [http://www.truecrypt.org/faq](http://www.truecrypt.org/faq).
Again, it's not 1st hand experience, so I'm not 100% sure TrueCrypt will do what you're asking =]

---

### Post by johnsmoke on 2014-04-24
Thanks for the info. Read up on TrueCrypt and created myself a little instruction doc to use to do it on my flash drives. I'll do the full encryption on 14.04 as well. THANKS!

---

