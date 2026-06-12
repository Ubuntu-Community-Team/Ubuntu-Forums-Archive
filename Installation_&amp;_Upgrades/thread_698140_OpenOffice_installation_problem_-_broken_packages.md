---
title: "OpenOffice installation problem - broken packages"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Nathan Bell on 2008-02-15
I am trying to get my open-office packages back to a pristine state after a botched install (BTW: I think that the ubuntu OpenOffice packages are broken, where do I report a bug after I gather more details about seems broken?)

I started with a pristine install of Ubuntu 7.10, and then attempted to apt-get install openoffice-write and openoffice-calc.  Things blew up, and now I'd like to clean up so I can try again a different way.

Problem is, none of apt-get's cleaning utilities seem to do anything, and I'm new to Linux so I don't understand what I should be cleaning up myself.  Here's what apt-get tells me when I try to force install:

```
# apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  openoffice.org-hyphenation
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 999kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 84695 files and directories currently installed.)
Removing openoffice.org-hyphenation ...
/var/lib/dpkg/info/openoffice.org-hyphenation.postrm: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**updatedb; locate update-openoffice** returns an empty list.  I 'fixed' one openoffice package removal by "touch"ing and "chmod +x"ing the file it claimed was missing.  Seems pretty dirty to me, but it worked.  This error doesn't provide a path, so I'm a little lost.

By the way, I've run into broken packages a few other times and had no idea how to fix them... what's the rule of thumb here?  Is there anything I can read up on?

Thanks in advance,
Nathan

---

### Post by Partyboi2 on 2008-02-15
You could try reinstalling dictionaries-common. From what I understand update-openoffice-dicts is part of dictionaries-common
```
sudo apt-get install --reinstall dictionaries-common
```

To report a bug you can do it [here]("https://bugs.launchpad.net/")


---

### Post by Nathan Bell on 2008-02-16
Thank you, I just gave that a shot.  However, apt-get won't get past the failing packages (openoffice.org-hyphenation in this case).  Is there anyway to tell it to stop trying to remove it so I can install other packages?  It seems once it finds a failure in hyphenation, it doesn't attempt to do any others.

I read the man pages for apt-get, and I saw a command (-m) that I thought would tell it to ignore, but  apt-get was unconvinced.

> **Partyboi2 said:**
> You could try reinstalling dictionaries-common. From what I understand update-openoffice-dicts is part of dictionaries-common
```
sudo apt-get install --reinstall dictionaries-common
```


---

### Post by Partyboi2 on 2008-02-16
try this
```
sudo mv /var/lib/dpkg/info/openoffice.org-hyphenation.postrm /var/lib/dpkg/info/openoffice.org-hyphenation.postrm.bak
```
then
```
sudo apt-get install --reinstall openoffice.org-hyphenation
```

---

