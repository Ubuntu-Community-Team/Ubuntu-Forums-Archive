---
title: "is there anything like &quot;sandboxie&quot; on ubuntu?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by newsboost on 2011-07-27
Hi,

Q:
Is there anything like "sandboxie" on ubuntu? Some kind of "sandbox" where you can install programs which you don't fully trust, but you want to try them out anyway. When you're done testing, you can then erase "the sandbox" and there's nothing left at all, at this point...

Would be nice if this existed!

Alternatively: Perhaps I could create a "test"-user. This still doesn't solve the problem about .deb-packages that wants me to enter root password... But I would kind of the same effect by deleting /home/test, for programs that doesn't ask for root password for installing into /usr/local or similar...

---

### Post by jerrrys on 2011-07-29
virtualbox?
[http://www.google.com/search?client=ubuntu&channel=fs&q=sandbox&ie=utf-8&oe=utf-8#pq=sandbox%20linux%20ubuntu&hl=en&cp=9&gs_id=10&xhr=t&q=sandboxie+linux+ubuntu&qe=c2FuZGJveGllIGxpbnV4IHVidW50dQ&qesig=kWFAfJXzD8y30kKGo1J5tQ&pkc=AFgZ2tmoewjzf5DNpCuKQPEAL6AhYk0VjhpKWfqy2xBG6a2x8kULWL_d1i_Z0Eb0CoYocW2tRYbSeVhrJwSq-5zfZyBoA1dpFQ&pf=p&sclient=psy&client=ubuntu&hs=nJ1&channel=fs&source=hp&pbx=1&oq=sandboxie+linux+ubuntu&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=26e57aa7900464a7&biw=1024&bih=657](http://www.google.com/search?client=ubuntu&channel=fs&q=sandbox&ie=utf-8&oe=utf-8#pq=sandbox%20linux%20ubuntu&hl=en&cp=9&gs_id=10&xhr=t&q=sandboxie+linux+ubuntu&qe=c2FuZGJveGllIGxpbnV4IHVidW50dQ&qesig=kWFAfJXzD8y30kKGo1J5tQ&pkc=AFgZ2tmoewjzf5DNpCuKQPEAL6AhYk0VjhpKWfqy2xBG6a2x8kULWL_d1i_Z0Eb0CoYocW2tRYbSeVhrJwSq-5zfZyBoA1dpFQ&pf=p&sclient=psy&client=ubuntu&hs=nJ1&channel=fs&source=hp&pbx=1&oq=sandboxie+linux+ubuntu&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=26e57aa7900464a7&biw=1024&bih=657)

---

### Post by steve11911 on 2011-07-30
I agree.Virtualbox is easily an excellent recommendation. 
Actually,a sandboxing scheme has been present in linux since about 2005 and has been available in Ubuntu since at least Hardy Heron.

[https://wiki.ubuntu.com/Security/Features#seccomp](https://wiki.ubuntu.com/Security/Features#seccomp)

Additionally:

Reference to an actual linux sandbox proggy:

[http://linux-tipps.blogspot.com/2010/01/running-untrusted-programs-in-sandbox.html](http://linux-tipps.blogspot.com/2010/01/running-untrusted-programs-in-sandbox.html)

And this very interesting scheme:

Create a Linux user sandbox with chroot and unionfs:

[http://librenix.com/?page=Chroot](http://librenix.com/?page=Chroot)

There are additional methodologies.For the curious:

[http://en.wikipedia.org/wiki/Sandbox_%28computer_security%29](http://en.wikipedia.org/wiki/Sandbox_%28computer_security%29)

---

### Post by Khelben Arunsun on 2011-07-30
And Wine makes a great sandbox for windows programs, and there are several ways to use it as one.

I use the Chroot method myself.

---

### Post by kostkon on 2011-07-30
There's [Glimpse]("http://www.omgubuntu.co.uk/2011/07/glimpse-linux-offers-safe-sandboxed-testing-unstable-apps/").

---

