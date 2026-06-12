---
title: "Reinstall or downgrade?"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by TipTricky on 2013-01-28
I have a desktop i use for a game server but the last month i can download anything or update anything without it giving me an error i already posted on the forums for help and no one knows why so i want to reinstall Ubuntu 12.10 but i dont want to have 2 copies of the same os and i dont want to lose all my info on the drive is this possible? If so how?

---

### Post by Cheesehead on 2013-01-28
You should probably try to figure out what the problem is it's usually really easy to fix you should link to the old thread that didn't get answered maybe you didn't prove enough information or didn't bump your problem daily i looked at your old thread and it seems easy to fix.

---

### Post by TipTricky on 2013-01-28
Well i just installed a fresh clean 12.10 any way but still have a issue. When i use software updater it says ```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
```
Any ideas as to why?

---

### Post by offgridguy on 2013-01-28
> **TipTricky said:**
> I have a desktop i use for a game server but the last month i can download anything or update anything without it giving me an error i already posted on the forums for help and no one knows why so i want to reinstall Ubuntu 12.10 but i dont want to have 2 copies of the same os and i dont want to lose all my info on the drive is this possible? If so how?
Technically there is no downgrade for ubuntu, you would have to 
reinstall, or install another OS.

Can you backup your info and save it ?

edit ; i see i am a little late.

---

### Post by TipTricky on 2013-01-28
> **offgridguy said:**
> Technically there is no downgrade for ubuntu, you would have to 
reinstall, or install another OS.

I ment go back to 12.04 but i installed 12.10 and erased all info on the drive so its a fresh install

---

### Post by Old_Grey_Wolf on 2013-01-28
Edit:  Never mind. You already reinstalled.

---

### Post by TipTricky on 2013-01-28
> **Old_Grey_Wolf said:**
> Edit:  Never mind. You already reinstalled.
Lol well i already did a fresh install and everything seems to be working fine thus far go the updater working again and all is well again. But to answer your question in the other post Wolf it was a disk install of ubuntu

---

### Post by Cheesehead on 2013-01-28
> **TipTricky said:**
> ```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
```
Any ideas as to why?

It is a valid FQDN, and points to a valid server, and downloads a valid package when I try it.
Did you try several times, a few minutes apart? Perhaps the server hiccupped. Or perhaps your DNS server hiccupped.

Or are you perhaps behind a proxy?
Or pointing to a lagging DNS?
Has this happened before for an inconveniently long period?

---

### Post by TipTricky on 2013-01-28
> **Cheesehead said:**
> It is a valid FQDN, and points to a valid server, and downloads a valid package when I try it.
Did you try several times, a few minutes apart? Perhaps the server hiccupped. Or perhaps your DNS server hiccupped.

Or are you perhaps behind a proxy?
Or pointing to a lagging DNS?
Has this happened before for an inconveniently long period?

It worked after about 15 minutes...
Not behind a proxy.
Possibly.
Yes has happened once before for about 3 days lol.

But all is fine now with the fresh install im changing post to solved

---

