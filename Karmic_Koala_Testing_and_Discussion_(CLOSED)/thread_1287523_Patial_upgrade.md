---
title: "Patial upgrade"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keithy on 2009-10-10
Hi,

Update manager has been offering me a partial upgrade for almost 20 hours now. I have read the warnings in the 'sticky' above and sensibly havent done it!  

Do I just need to wait longer for the various packages to be updated.

The greyed out ones in package manager seem to be a few epiphany bits, lots of python bits and generic linux kernel items (sorry I'm a clueless noob here!)

Any insight would be useful

Thanks

---

### Post by exploder on 2009-10-10
I would just wait. Why risk breaking something that is working. Check later and see if the situation has changed.

---

### Post by slakkie on 2009-10-10
Could you output the results of:

```

sudo aptitude -s safe-upgrade. 

```

Before you do this however, run sudo aptitude update (don't need the output of this).

The following packages have been kept back for a while now:
```

The following packages have been kept back:
  epiphany-browser{a}  epiphany-browser-data{a}  epiphany-browser-dbg{a}  epiphany-extensions{a}  epiphany-gecko{a}

```

When I tried installing them manually (so upgrade them in fact) it told me it would break some dependencies. This is mainly due to epiphany-extensions and epiphany-browser-dbg dependencies.

You can see this by doing

```

sudo aptitude -s install epiphany-browser

```

You will see something like:

```

The following packages have unmet dependencies:                                                                      
  epiphany-extensions: Depends: epiphany-gecko (>= 2.26) but it is not installable                                   
                       Depends: epiphany-gecko (< 2.27) but it is not installable                                    
  epiphany-browser-dbg: Depends: epiphany-gecko (= 2.26.1-0ubuntu3) but it is not installable or                     
                                 epiphany-webkit (= 2.26.1-0ubuntu3) but it is not installable                       

```

And webkit and gecko cannot be installed due to:

```

apt-cache policy epiphany-gecko epiphany-webkit
epiphany-gecko:
  Installed: 2.26.1-0ubuntu3
  Candidate: 2.28.0-4ubuntu1
  Version table:
     2.28.0-4ubuntu1 0
        500 http://nl.archive.ubuntu.com karmic/universe Packages
 *** 2.26.1-0ubuntu3 0
        100 /var/lib/dpkg/status
epiphany-webkit:
  Installed: (none)
  Candidate: 2.28.0-4ubuntu1
  Version table:
     2.28.0-4ubuntu1 0
        500 http://nl.archive.ubuntu.com karmic/universe Packages

```

Their versions are too high to meet the dependencies...

---

### Post by N_Nick on 2009-10-10
I just installed Karmic beta, tried to update and i got that message too so i went for it.

20 minutes after the "upgrade" and still no problems. *crosses fingers*

---

### Post by keithy on 2009-10-10
Thanks for the replies,

just trying to learn here :)

output of sudo aptitude safe-upgrade is

The following packages have unmet dependencies:
  epiphany-browser: Conflicts: epiphany-gecko but 2.26.1-0ubuntu3 is installed and it is kept back.
  epiphany-gecko: Depends: epiphany-browser-data (< 2.27) but 2.28.0-4ubuntu1 is to be installed.

---

### Post by slakkie on 2009-10-10
> **N_Nick said:**
> I just installed Karmic beta, tried to update and i got that message too so i went for it.

20 minutes after the "upgrade" and still no problems. *crosses fingers*

Well, epiphany is the gnome web-browser and it will not break your system. So very little harm can be done. With other packages you might break your machine, but this is a fairly innocent package.

---

### Post by N_Nick on 2009-10-10
Yes you are right, sounds like i got lucky this time.
I didn't check the sticky before installing Karming, i got excited after reading some positive reviews from other users. :)

Edit: By the way, what does "sudo aptitude safe-upgrade" actually do?

---

### Post by philinux on 2009-10-10
> **N_Nick said:**
> Yes you are right, sounds like i got lucky this time.
I didn't check the sticky before installing Karming, i got excited after reading some positive reviews from other users. :)

Edit: By the way, what does "sudo aptitude safe-upgrade" actually do?

```
man aptitude
```

Has it all. ;)

---

