---
title: "Software &amp; Updates broken"
date: 2020-12-26
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2020-12-26
Ever since I upgraded from 18.04 to 20.04 I've been plagued by the failure of the Software Updater. It will fail with the "check your Internet connection" error. This a bogus because my Internet connection is just fine. Whenever this happens, I go into Software & Updates to the "Other Software" tab and (after password check) I clear the boxes pertaining to Canonical and let the system reload the software cache. It runs just fine after that with no error.

However, if I re-enable Canonical, the software cache reload hangs right at the end and never completes. I've left it overnight and still it won't complete. The task manager shows it not using the CPU at all and eventually I have to Kill it to make it go away, then go back into Software & Updates and disable Canonical to make it work again.

Is this a problem I need to fix, or is this something having to do with the upgrade to 20.04? As far as I can remember, Canonical has always been enabled with no hangups. Do I need this setting set?

Bill

---

### Post by #&amp;thj^% on 2020-12-26
Is this the offending repo?
```
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

```
EDIT: The Canonical Partner repository offers some proprietary applications that don't cost any money to use but are closed source. They include software like Adobe Flash Plugin. Software in this repository will appear in Ubuntu Software search results but won't be installable until this repository is enabled.

---

### Post by grahammechanical on 2020-12-26
I might be useful to see the internet addresses of the repositories (sources) that updater is trying to connect to. You can do this two ways.

1) Open gedit at /etc/apt/sources.list

2) Run this command

```
cat /etc/apt/sources.list
```

Regards

---

### Post by WB0HYQ on 2020-12-26
Don't know for sure. It only says "Canonical Partners" and "Canonical Partners (Source Code)" Right at the top of the list.

Bill

---

### Post by WB0HYQ on 2020-12-26
This is what I get when I uncomment those two repositories and run "apt update":

```
sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]     
Ign:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise InRelease                    
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [109 kB]      
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security InRelease [109 kB]   
Get:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release [8,180 B]            
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]   
Get:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release.gpg [181 B]          
Ign:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release.gpg       
Reading package lists... Done
W: GPG error: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
E: The repository 'http://archive.canonical.com/ubuntu precise Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Bill

---

### Post by #&amp;thj^% on 2020-12-26
Bingo>>>Just remove this ": [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) _**precise Release**_: "
Update again.
If needed add:
```
deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner
```

---

### Post by deadflowr on 2020-12-26
If the entry does not show in the sources.list file double check the /etc/apt/sources.list.d directory.
In weird cases the partner repository gets a special list file like 3rd party repos  PPAs do.
(I don't know why or when this behavior started, but I have seen it here and in my own system before, so...)

---

### Post by #&amp;thj^% on 2020-12-26
> **deadflowr said:**
> If the entry does not show in the sources.list file double check the /etc/apt/sources.list.d directory.
In weird cases the partner repository gets a special list file like 3rd party repos  PPAs do.
_(I don't know why or when this behavior started, but I have seen it here and in my own system before, so_...)

Good to know I've never seen it, so your input offers me something new. :)

---

### Post by WB0HYQ on 2020-12-26
The only items in the sources.list.d directory are the ones NOT enabled in the Software Updater list.

Bill

---

### Post by WB0HYQ on 2020-12-26
If I uncomment these two, and then run 'apt update', it will fail those two repositories.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


If I comment these, am I missing any important updates? If not, then I'll leave them as they are and forget about them.

Bill

---

### Post by deadflowr on 2020-12-26
> **WB0HYQ said:**
> If I uncomment these two, and then run 'apt update', it will fail those two repositories.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


If I comment these, am I missing any important updates? If not, then I'll leave them as they are and forget about them.

Bill

You can delete the whole section.
No updates will ever come from those, ever.

Or...
Do as 1fallen already suggested and edit the contents and change the entry from precise to focal,
which will fix the issue entirely.

---

### Post by WB0HYQ on 2020-12-26
That sounds reasonable. I'll give that a try.

And, it worked just fine. Thanks so much for everyone's help. The two Canonical entries are checked and I can update without the hang.

Bill

---

