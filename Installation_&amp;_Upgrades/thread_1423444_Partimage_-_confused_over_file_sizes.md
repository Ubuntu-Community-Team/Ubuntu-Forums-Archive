---
title: "Partimage - confused over file sizes"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2010-03-06
I'm trying to use partimage to create an archive of an Ubuntu version I'm no longer using.

When I run partimage, it tells me that the used space on the partition is 6.10 Gigs.  This seems odd because other tools (df, du, disk usage analyzer) say that used space is around 2.5 Gig.  The compressed (with gzip) partimage file is 861M, which of course isn't meaningful.  So I ran it again uncompressed, and the result was 6282M - consistent with what partimage told me.

Does this make sense?  Why the big difference?  Is this caused by thousands of files each with large block sizes?  I'd like to know that I have a good archive before I go to the next step - replacing the Ubuntu version with a later one.

Thanks
Mike

---

### Post by psusi on 2010-03-06
Could be... what does sudo du -bsh say?

---

### Post by 5circles on 2010-03-06
> **psusi said:**
> Could be... what does sudo du -bsh say?

2.1G.

(For the partition I'm running the OS from, I get 
```
du: cannot access `./.gvfs': Permission denied
``` before the result.  That's always confused me.

---

### Post by psusi on 2010-03-06
du says 2.1 gigs with, or without the -b?

The .gvfs directory is a virtual directory created by the gnome filesystem and is only accessible to you, so when you run du as root it can't look in there.

---

### Post by 5circles on 2010-03-07
> **psusi said:**
> du says 2.1 gigs with, or without the -b?

```
sudo du -bsh
2.1G	.
```

> **psusi said:**
> The .gvfs directory is a virtual directory created by the gnome filesystem and is only accessible to you, so when you run du as root it can't look in there.
Thanks for the reminder.  I find it confusing that there are files that are inaccessible to root.

---

