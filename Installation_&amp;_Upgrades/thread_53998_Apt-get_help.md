---
title: "Apt-get help"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by redcamel on 2005-08-03
When trying to apt-get install "anything" I get the following
I'm really not sure how to fix this problem...


Setting up ttf-baekmuk (2.2-1ubuntu1) ...
/etc/defoma/hints/ttf-baekmuk.hints: Unable to open, or empty.
dpkg: error processing ttf-baekmuk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ttf-baekmuk; however:
  Package ttf-baekmuk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-baekmuk
 ubuntu-desktop

---

### Post by heimo on 2005-08-03
I'd try (prefix commands with sudo when neccessary):

 ```
apt-get update
apt-get install -f
apt-get upgrade
dpkg --configure -a

```

---

### Post by redcamel on 2005-08-03
That didn't help???

---

### Post by heimo on 2005-08-03
[QUOTE=redcamel]That didn't help???[/QUOTE]

I don't know. ;) If it didn't help, I'd try next:
 ```

sudo apt-get remove --purge ttf-baekmuk
sudo apt-get install ttf-baekmuk

``` 
Any errors?

---

### Post by redcamel on 2005-08-03
Yes....Still more errors


Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ttf-baekmuk* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 28.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 63856 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing ttf-baekmuk ...
/etc/defoma/hints/ttf-baekmuk.hints: Unable to open, or empty.
dpkg: error processing ttf-baekmuk (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 ttf-baekmuk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by heimo on 2005-08-03
Hmm... Could this be borked dpkg database... (just thinkin out loud here) Somewhere under (sorry, can't verify at the moment) /var/ is kept database for dpkg (lots of files) and... there's also probably files for that ttf-baekmuk package ... you should move away those broken files and try to purge-remove and reinstall that package again. Sorry, can't give better, detailed instructions just now. If you can't find those files, I'll be glad to help later.

---

### Post by redcamel on 2005-08-03
I've looked but, not sure where the files are.  Can you offer some more details when you have a chance?

---

### Post by heimo on 2005-08-03
[QUOTE=redcamel]I've looked but, not sure where the files are.  Can you offer some more details when you have a chance?[/QUOTE]

Something like:
```

sudo rm /var/lib/dpkg/info/ttf-baekmuk.*
sudo apt-get remove --purge ttf-baekmuk
sudo apt-get install ttf-baekmuk

```

---

