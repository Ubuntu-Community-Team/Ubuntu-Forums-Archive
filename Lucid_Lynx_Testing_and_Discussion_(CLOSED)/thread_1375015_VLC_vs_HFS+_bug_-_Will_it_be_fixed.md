---
title: "VLC vs HFS+ bug - Will it be fixed?"
date: 2010-01-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mickie.kext on 2010-01-07
I filled this bug a week ago:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/502736](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/502736)

Can anyone confirm this bug in Lucid? I did not tested with Lucid (I plan to join with Alpha 2) but I am pretty sure it is not fixed...

I have lots of videos on 1TB HFS+ disk and it really bugs me.

---

### Post by Eclipse. on 2010-01-07
> **mickie.kext said:**
> I filled this bug a week ago:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/502736](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/502736)

Can anyone confirm this bug in Lucid? I did not tested with Lucid (I plan to join with Alpha 2) but I am pretty sure it is not fixed...

I have lots of videos on 1TB HFS+ disk and it really bugs me.

Its not something thats ever going to be fixed by a ubuntu developer, its an issue between the vlc and kernel developers.The vlc guys say its not their fault and the kernel devs are not keen on the changes needed to fix it unfortunately.Downgrading to vlc 0.8.6 will solve the problem though.

---

### Post by mickie.kext on 2010-01-07
> **Eclipse. said:**
> Its not something thats ever going to be fixed by a ubuntu developer, its an issue between the vlc and kernel developers.The vlc guys say its not their fault and the kernel devs are not keen on the changes needed to fix it unfortunately.Downgrading to vlc 0.8.6 will solve the problem though.

Thanks for reply:D. Do you happen to know how to find lkml post which says something about this issue? I would like to know why they do not want to fix it, and where I should start hacking if I want to fix it myself.

---

### Post by Jordanwb on 2010-01-07
> **Eclipse. said:**
> the kernel devs are not keen on the changes needed to fix it unfortunately.

Wait. What? These dudes have written millions of lines of code, fix numerous bugs, yet they don't want to fix this particular bug? Do the FS guys have a vendetta against HFS+?

---

### Post by Eclipse. on 2010-01-07
> **Jordanwb said:**
> Wait. What? These dudes have written millions of lines of code, fix numerous bugs, yet they don't want to fix this particular bug? Do the FS guys have a vendetta against HFS+?

Wait. What?

Your making silly claims and accusations without actually reading up on the situation? Nobody has a vendetta against anyone, those who spend time on for example ext4 and not the same people that spend time on hfs+.My previous post should have said that in hindsight instead of the "kernel devs" generalisation.

please read: [http://marc.info/?t=122823360800002&r=1&w=2](http://marc.info/?t=122823360800002&r=1&w=2) for the mailing list discussion on the subject and [http://forum.videolan.org/viewtopic.php?f=13&t=52379](http://forum.videolan.org/viewtopic.php?f=13&t=52379)

---

### Post by BwackNinja on 2010-01-08
> **Chauncellor said:**
> Actually, on a humorous note, I do recall Linus stating in his charming manner something to the lines of:

"HFS is a piece of crap file system".

Something like that ;)

not really relevant to this thread, but this is what you were talking about: [http://www.tuaw.com/2008/02/06/linux-creator-disses-leopard-file-system/](http://www.tuaw.com/2008/02/06/linux-creator-disses-leopard-file-system/)

---

