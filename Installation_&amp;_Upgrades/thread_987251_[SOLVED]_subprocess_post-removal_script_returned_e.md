---
title: "[SOLVED] subprocess post-removal script returned error exit status 127"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by ulver on 2008-11-19
Hi, I cant install anything right now because of this error (open office installation was not completed) 

Removing openoffice.org-hyphenation-en-us ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried purge with apt-get / aptitude none of it did help, any ideas?

---

### Post by ulver on 2008-11-23
*bump*

---

### Post by ulver on 2008-11-27
The problem fixed itself somehow :s

---

### Post by suffice on 2008-11-28
I still get this subprocess error everytime i do an update or install...its really tickin me....though things still seem to work...any idea what you did?

---

### Post by Floft on 2009-01-12
I just encountered the same problem. I'm not an expert or anything, but I did successfully fix the problem. This is how I did it (in a terminal...):

> sudo aptitude install dictionaries-common
sudo apt-get remove openoffice.org-hyphenation-en-us

---

### Post by afotey on 2009-01-18
thanks i also had the same problem. but now it's fixed.

---

### Post by Baboontu on 2009-04-24
Please Help
I want to upgrade to jaunty from intrepid but I can't even install a single package
I get :" /var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: 6: update-openoffice-dicts: not found".
I tried the solutions offered above but to no avail.:(
Thanks

---

### Post by Floft on 2009-04-24
Do either of these work?

```
sudo aptitude install dictionaries-common
```

OR

```
sudo apt-get install dictionaries-common
```

---

### Post by Baboontu on 2009-04-25
> **Floft said:**
> Do either of these work?

```
sudo aptitude install dictionaries-common
```

OR

```
sudo apt-get install dictionaries-common
```

I had to edit /var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm and give it "exit 0" value and then do what you advised me.
Thanks :)

---

### Post by scouser73 on 2009-05-20
> **Floft said:**
> I just encountered the same problem. I'm not an expert or anything, but I did successfully fix the problem. This is how I did it (in a terminal...):

Thanks for the tip, it's now sorted the problem, much appreciated.

---

### Post by _khAttAm_ on 2009-08-12
I got into this problem and solved it. But I was in search for something generic. And managed to do it by editing /var/lib/dpkg/status. I think it works for any packages. I have written it in my blog:
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

---

### Post by Lockheed on 2009-08-28
> **Baboontu said:**
> I had to edit /var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm and give it "exit 0" value and then do what you advised me.
Thanks :)

How exactly do you do that? I tried all other listed methods but it didn't help.

---

### Post by Lockheed on 2009-08-29
> **_khAttAm_ said:**
> I got into this problem and solved it. But I was in search for something generic. And managed to do it by editing /var/lib/dpkg/status. I think it works for any packages. I have written it in my blog:
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)
This one worked for me. Thanks!

---

### Post by vckeating on 2009-09-03
> **Lockheed said:**
> How exactly do you do that? I tried all other listed methods but it didn't help.

I'm also interested in how this works.  Can you describe for us non-programmers what you did?

---

### Post by vckeating on 2009-09-03
After looking around a little more, I found that the instructions from this page fixed the problem:

[https://bugs.launchpad.net/openoffice/+bug/274556](https://bugs.launchpad.net/openoffice/+bug/274556)

- V

---

