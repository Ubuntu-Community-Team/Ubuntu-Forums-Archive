---
title: "Can't install ANY APPLICTION!"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by Partian on 2011-07-15
Can't install 'OpenJDK Java 6 Runtime'
I really don't know why :(

---

### Post by Toz on 2011-07-15
What happens when you try? Are you getting any error messages?

---

### Post by Partian on 2011-07-15
Yeah, I do infact.

There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

and I have 'Details'

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

---

### Post by Partian on 2011-07-15
bump

---

### Post by Rubi1200 on 2011-07-15
Hi and welcome to the forums Partian :)

Open a terminal with Ctrl+Alt+T and run the following commands (copy and paste to avoid typos):

```
sudo apt-get clean

sudo apt-get install -f

sudo dpkg -- configure -a

sudo apt-get update
```

If there are errors, for any of the commands post the exact message please.

---

### Post by Partian on 2011-07-15
> **Rubi1200 said:**
> Hi and welcome to the forums Partian :)

Open a terminal with Ctrl+Alt+T and run the following commands (copy and paste to avoid typos):

```
sudo apt-get clean

sudo apt-get install -f

sudo dpkg -- configure -a

sudo apt-get update
```

If there are errors, for any of the commands post the exact message please.

Thanks, but it shows a disclaimer, but I can't click on '<Ok>' i'm not sure why.
EDIT: I would show you disclaimer but I can't install ANY program without the message popping up, thus means I can't install ANYTHING at all.
EXIT #2: No worries, I pressed the third button (scroll) and it worked, thanks.

---

### Post by Rubi1200 on 2011-07-15
Okay,

let's step back a minute and try just this in the terminal:

```
sudo apt-get update
```

If it reports errors, you should be able to copy it and post the message here.

If there are no errors, then try this command:

```
sudo dpkg --configure -a
```

Same procedure as before for error message.

Still nothing? Then post the contents of the following file:

```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2011-07-15
> **Partian said:**
> Thanks, but it shows a disclaimer, but I can't click on '<Ok>' i'm not sure why.

Use the Tab key to highlight 'Ok', then press Enter.

---

