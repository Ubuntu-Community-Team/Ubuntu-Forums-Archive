---
title: "dist-upgrade packages missing after today updates"
date: 2008-06-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by razmakati on 2008-06-16
For the past week I have been waiting for some of the dist-upgrade packages
dependencies to be solved. After todays last set of updates involving OpenOffice.org packages and evolution packages I can no longer see the dist-upgrade packages available. I did interrupt a download of the dist-upgrade packages once because of a hasty key stroke. 

Attatched is a aptitude log of my last 3 update

did I do something wrong?

thanks for any help

---

### Post by psyke83 on 2008-06-16
> **razmakati said:**
> For the past week I have been waiting for some of the dist-upgrade packages
dependencies to be solved. After todays last set of updates involving OpenOffice.org packages and evolution packages I can no longer see the dist-upgrade packages available. I did interrupt a download of the dist-upgrade packages once because of a hasty key stroke. 

Attatched is a aptitude log of my last 3 update

did I do something wrong?

thanks for any help

First of all, it's probably better to attach logs from apt-get or aptitude, as it may give more information. From looking at the log, however, I think I know the problem. You dist-upgraded from Hardy to Intrepid, but before doing so you upgraded packages from the "hardy-proposed" and/or "hardy-backports" repository, is that true?

If so, then you need to manually downgrade openoffice.org, evolution and some other packages, or wait until Intrepid catches up. You may be waiting some time, since Intrepid may wait for a couple of months and push through version 3 (beta) instead of series 2.4.x of openoffice.org.

Resolving this will take some manual downgrading and patience (or else you can reinstall Hardy and perform a dist-upgrade to Intrepid *before* upgrading any packages).

---

### Post by razmakati on 2008-06-16
> **psyke83 said:**
> First of all, it's probably better to attach logs from apt-get or aptitude, as it may give more information. From looking at the log, however, I think I know the problem. You dist-upgraded from Hardy to Intrepid, but before doing so you upgraded packages from the "hardy-proposed" and/or "hardy-backports" repository, is that true?

If so, then you need to manually downgrade openoffice.org, evolution and some other packages, or wait until Intrepid catches up. You may be waiting some time, since Intrepid may wait for a couple of months and push through version 3 (beta) instead of series 2.4.x of openoffice.org.

Resolving this will take some manual downgrading and patience (or else you can reinstall Hardy and perform a dist-upgrade to Intrepid *before* upgrading any packages).

You are correct i did update Hardy before upgrading to Intrepid

/home is a separate partition so..

I will re install as per your suggestion

Thank you

---

### Post by ShirishAg75 on 2008-06-16
There are few times when aptitude does tell that it needs to downgrade a specific package but don't really remember how that happens.

---

### Post by Gina on 2008-06-17
I have the same problem.  I think I'll leave it until Alpha 1 comes out though.  Intrepid is working alright ATM and I know nothing much is happening with that currently.

---

### Post by psyke83 on 2008-06-17
> **Gina said:**
> I have the same problem.  I think I'll leave it until Alpha 1 comes out though.  Intrepid is working alright ATM and I know nothing much is happening with that currently.

Try updating your repository lists (for the main mirror) - I'm seeing a big push of new packages, including openoffice.org and evolution.

---

### Post by Gina on 2008-06-17
I'll have another go shortly and see how things are - thank you :)

---

