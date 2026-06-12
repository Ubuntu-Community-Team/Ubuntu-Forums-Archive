---
title: "Problem with MergeList"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by Ken Kaniff on 2011-06-26
Hi

I'm running into the problem shown below, which prevents me from installing software.
 
Problem code:
[HTML]Reading package lists... Error!
W: GPG error: http://www.linuxfaq.pl i386/ InRelease: The following signatures were invalid: NODATA 1 NODATA 2
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.linuxfaq.pl_repo_i386_Packages
E: The package lists or status file could not be parsed or opened.[/HTML]

Numerous sources, including this forum, suggest trying:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

or

```
sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

None of them have worked for me. Has anyone found a different solution? Any suggestion would be much appreciated. 

Thanks.
KK

---

### Post by Rubi1200 on 2011-06-26
First step to try is change the download mirror from what is is to Main Server and then run apt-get update.

Post any error messages please.

---

### Post by Ken Kaniff on 2011-06-26
Thanks. After changing the sources to Main Server, I got the following error:

```
W: GPG error: http://www.linuxfaq.pl i386/ InRelease: The following signatures were invalid: NODATA 1 NODATA 2

```

---

### Post by Rubi1200 on 2011-06-26
Please post the output of the following:

```
cat /etc/apt/sources.list
```

Thanks.

---

### Post by Ken Kaniff on 2011-06-26
> **Rubi1200 said:**
> Please post the output of the following:

```
cat /etc/apt/sources.list
```

Thanks.

Rubi, here's the output of the command:

```
# deb-src http://pl.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://www.linuxfaq.pl/repo/ i386/

```

Thanks for help.

---

### Post by Rubi1200 on 2011-06-26
I am not sure why you have this enabled:
> [http://www.linuxfaq.pl/repo/](http://www.linuxfaq.pl/repo/) i386/
or even what it is supposed to connect to (it leads me to a website in Polish).

Here is what I suggest:

run these commands:

```
gksudo gedit /etc/apt/sources.list
```

Comment that line so it looks like this:

> #deb [http://www.linuxfaq.pl/repo/](http://www.linuxfaq.pl/repo/) i386/

Save and close the file and then run ```
sudo apt-get update
``` again.

---

### Post by Ken Kaniff on 2011-06-26
I'm based in Poland and during an update this source might have gotten enabled--I didn't mess with the file myself.

It worked! Rubi, you're the man. Thank you so much for helping out.

---

### Post by Rubi1200 on 2011-06-26
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

