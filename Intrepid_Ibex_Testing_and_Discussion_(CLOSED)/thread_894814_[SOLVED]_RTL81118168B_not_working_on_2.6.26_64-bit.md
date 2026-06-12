---
title: "[SOLVED] RTL8111/8168B not working on 2.6.26 64-bit"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aamukahvi on 2008-08-19
Anybody else seeing the same? This is using the r8169 driver.
Works ok with the Hardy kernel but not the intrepid 2.6.26 series.
Don't have any idea what I should be looking for/at to solve this so ideas are welcome.

Bugged it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259534](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259534)

---

### Post by plun on 2008-08-19
Maybe this thread is useful from Hardys development  ?

[http://ubuntuforums.org/showthread.php?t=755002](http://ubuntuforums.org/showthread.php?t=755002)


I helped a guy running Hardy and it cannot be fixed, slow speeds.
So some bottle-necks must be left.

From the beginning this was a firmware flaw which MS found a year ago.

---

### Post by aamukahvi on 2008-08-19
Thanks for that piece of info. :) Just wondering why it works great with the hardy kernel and not with the newer one...

---

### Post by plun on 2008-08-20
No, I dont think it works great.  But this is just speculations from me..:)

The person I helped had bad values when he tested his Internet connection.
In Sweden we have a official consumer site against all ISPs, [http://www.bredbandskollen.se/](http://www.bredbandskollen.se/)   "Starta Mätning" = "Start Measure"...

Your country, Suomi   ?  

Everything started with this Realtek firmware flaw which corrupted data
[http://blogs.zdnet.com/Ou/?p=663](http://blogs.zdnet.com/Ou/?p=663)


You can find several bugs within Launchpad about this, totally broken or low speeds for Networking/Samba shares.

Maybe you can use the same method as this ?
[http://ubuntuforums.org/showpost.php?p=4718501&postcount=4](http://ubuntuforums.org/showpost.php?p=4718501&postcount=4)

EDIT, Need for patch ?, latest driver seems to be kernel 2.6.26 compatible.

Latest Realtek driver
[http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Seems to be brand new ones for Linux....

---

### Post by aamukahvi on 2008-08-20
Yeah Suomi :)

I'll try to compile 8.008 for my kernel, thanks again for your help!

---

### Post by plun on 2008-08-20
> **aamukahvi said:**
> Yeah Suomi :)

I'll try to compile 8.008 for my kernel, thanks again for your help!

Please remember your bug....:)

If it works, this bug is probably a kernel issue.... and also
a "high" ranked change...  IMHO.

I haven't checked anything "upstream" for clues.

---

### Post by aamukahvi on 2008-08-20
Thank you so much, it's now working with the r8168 driver! I have reported what I did in the bug report :)

---

### Post by plun on 2008-08-22
> **aamukahvi said:**
> Thank you so much, it's now working with the r8168 driver! I have reported what I did in the bug report :)

Well... some more info which was syndicated with Ubuntu Planet

[http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/](http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/)

I also saw that the bug was confirmed....:)

---

### Post by aamukahvi on 2008-08-28
This is fixed in 2.6.27 (just in case there was anyone with the same problem) :)

---

