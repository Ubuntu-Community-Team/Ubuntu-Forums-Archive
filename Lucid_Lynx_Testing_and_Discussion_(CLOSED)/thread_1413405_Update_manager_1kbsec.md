---
title: "Update manager 1kb/sec?"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jackzor on 2010-02-22
Is it my college connection?? or is it heavy usage on the server?

---

### Post by konqueror7 on 2010-02-22
it could be, but try changing your server...

System > Administration > Software Sources, then in the 'Ubuntu Software' tab, select 'Select Best Server' in the 'Download from' field. afterwards, reload your cache.

---

### Post by zika on 2010-02-22
Problem is that servers other than Main server are not up-to-date. Main server is, it seems, overloaded. I'm having slow update speed using it for quite some time. Funny thing is that I have alias sudo aptitude update && sudo aptitude safe-upgrade and when first part finishes second part waits for password again... That can tell You how long does it take to update on 16M connection... If only, at least US server, was less loaded... But, it seems, it isn't...

---

### Post by ranch hand on 2010-02-22
I would try another route (apt, aptitude or synaptic) to see if they are the same before switching your mirror.  I am using, on various installs of 10.04) the US and CA archives and my speeds are much better than that.

I do not use Update Mangler at all though so I do not know about speeds through it.  Could be an update recently buggered something there.

---

### Post by zika on 2010-02-22
As I said earlier, it doesn't matter which method of update-upgrade is used. Connection is deadly slow. US server, or Main server, it doesn't matter. It seems we've all gave up local server for the fact that they are not up-to-date and we're all attacking these two servers... Definitely that doesn't depend on the SW used. At least at my location...

---

### Post by emarkay on 2010-02-22
> **zika said:**
> Problem is that servers other than Main server are not up-to-date. 


Is this true?  Then what's the point of the other servers - re-runs? :)

---

### Post by Darkshade on 2010-02-22
I use a local mirror on my stable install and the main server on my alpha/beta in order to get the updates faster. Most of the time downloading at 4500-5000kb/s (my connection's limit) is not a problem though it goes all the way down to 20-30kb/s when beta 1 comes out and the server overloads.

---

### Post by Seventh Reign on 2010-02-22
> **emarkay said:**
> Is this true?  Then what's the point of the other servers - re-runs? :)

They're not "that" far out of date.  They might be a few hours to a few days behind the main server.  It all depends on your patience level... no wait scratch that .. obviously if we are installing an Alpha system almost 6 months before its actual release, then we have NO patience ..

---

