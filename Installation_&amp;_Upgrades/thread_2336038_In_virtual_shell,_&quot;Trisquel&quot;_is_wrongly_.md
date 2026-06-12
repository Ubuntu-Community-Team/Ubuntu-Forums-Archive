---
title: "In virtual shell, &quot;Trisquel&quot; is wrongly shown as my OS"
date: 2016-09-03
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2016-09-03
Somehow -- I think as an artifact or by-product of my having installed the GNU IceCat web browser -- whenever I drop into the virtual shell, using the Ctrl-Alt-F1 command, what I see displayed at the top of the black screen is:

[B]Trisquel GNU/Linux 6.0.1 jbox tty1

[/B]However, I am not running or using Trisquel in any way as far as I'm aware of, and I've deleted everything I could find with that name.  What it should say is:

Ubuntu 16.04 LTS jbox tty1

(or, maybe, "Ubuntu Mate 16.04 LTS jbox tty1").

Would anyone know:

 (a)  How it got there, but more importantly, 

(b) How I should I get rid of it and replace it with the correct name of the OS I'm actually running?

I'd also like to just make sure there's nothing else going on with Trisquel (& that there are no other consequences, functions or appearances of it) in my system.

(I ***think* **I've deleted everything, or almost everything, having to do with it.)  Thanks!

---

### Post by mook765 on 2016-09-04
Look in /etc/lsb-release

---

### Post by watchpocket on 2016-09-04
That doesn't seem to offer any clues. /etc/lsb-release is apparently as it should be:

```
* --> cat /etc/lsb-release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
```

---

### Post by watchpocket on 2016-09-04
So what then could possibly be causing the "Trisquel" line?  Is there a system-banner-type text-file somewhere that got overwritten with this?

---

### Post by steeldriver on 2016-09-04
What's in /etc/issue ?

---

### Post by watchpocket on 2016-09-04
Bingo.   /etc/issue just happens to be:```
Trisquel GNU/Linux 6.0.1 \n \l
```

Thank you.  I gather I should simply replace that with what's in /etc/lsb-release ?

I.e., with the text between quotation marks from this line of /etc/lsb-release:
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS" ?

Actually, I notice also that the file /etc/issue.net has the exact same wrong line.  I'm guessing there's no more to it than replacing the line in each file with the correct system name.
Would there be any reason not to go ahead and do that, and, would this or any other change need to be made in any other file(s)? Thanks.

---

### Post by steeldriver on 2016-09-04
You probably want to retain the \n and \l 

FWIW here's what mine says

```

Ubuntu 16.04.1 LTS \n \l

```

The file is part of the base-files package - so you could always re-install that, I guess

---

### Post by watchpocket on 2016-09-04
Yes, I retained the space-**\n**-space-**\l ** 
Thanks.  I made the same change to /etc/issue.net (though it doesn't have the " \n \l")
If anything appears to be weird with it I'll re-install the base-files package.  Thanks loads.

---

