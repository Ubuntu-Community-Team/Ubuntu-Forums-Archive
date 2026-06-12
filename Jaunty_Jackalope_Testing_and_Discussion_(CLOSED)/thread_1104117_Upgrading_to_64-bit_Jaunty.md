---
title: "Upgrading to 64-bit Jaunty"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by FraggedLocust on 2009-03-23
At the moment, I have the 32-bit 8.10. I'm wondering if I upgrade to the 64-bit Jaunty at release, will the 32-bit home partition files cause any problems when I try to read/write them?

---

### Post by oldos2er on 2009-03-23
There's no upgrade path for switching to 64-bit; you'd need to do a fresh install of the OS.

---

### Post by FraggedLocust on 2009-03-24
but if I do a fresh install of jaunty on the root partition, will it work well with my two partition setup (root and home)? Will the home files be read alright?

---

### Post by kpatz on 2009-03-24
Yes, your filesystems can be accessed from either a 32-bit or 64-bit OS.

---

### Post by misterfixit on 2009-03-25
> **kpatz said:**
> Yes, your filesystems can be accessed from either a 32-bit or 64-bit OS.

But, will 32-bit applications stop working?? The last time I had 64-bit on my work station, Firefox's add-ons (java, flash, etc.) all stopped working.  That was my #1 reason for going back to 32-bit.  IT is my understanding that this is one of the Dirty Little Secrets of the 32-bit versus 64-bit paths, that 64-bit still lacks capability to run most of the ordinary user applications.  My reason for going back to 64-bit is to have more RAM for VM and other apps always running.

---

### Post by bpollen on 2009-03-25
> **misterfixit said:**
> [COLOR="Blue"]Firefox's add-ons (java, flash, etc.) all stopped working.[/COLOR]


Both Java and Flash have 64bit versions available.....

---

### Post by oldos2er on 2009-03-25
> **misterfixit said:**
> But, will 32-bit applications stop working?? The last time I had 64-bit on my work station, Firefox's add-ons (java, flash, etc.) all stopped working.  That was my #1 reason for going back to 32-bit.  IT is my understanding that this is one of the Dirty Little Secrets of the 32-bit versus 64-bit paths, that 64-bit still lacks capability to run most of the ordinary user applications.  My reason for going back to 64-bit is to have more RAM for VM and other apps always running.

 In the x86_64 forum, there are ongoing threads on both Java and Flash, both of which now have 64-bit versions available, but not in the repositories yet. I found installing 64-bit Flash simple, 64-bit Java a bit more involved. 

 See [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/) and [http://johnbokma.com/mexit/2008/11/25/64-bit-adobe-flash-ubuntu.html](http://johnbokma.com/mexit/2008/11/25/64-bit-adobe-flash-ubuntu.html)

---

