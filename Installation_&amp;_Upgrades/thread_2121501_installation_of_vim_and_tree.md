---
title: "installation of vim and tree"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by ayutrip on 2013-03-02
When i type this command (in order to install vim):

sudo apt-get install vim

the terminal says:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'vim' has no installation candidate"

Similar is the case when i run the command to install tree

Please help me to fix this

---

### Post by malish on 2013-03-02
Try running

sudo apt-get update

before your command, if it didn't work, let us know the output of the following command:

cat /etc/apt/sources.list

Wishes,
[Mohammad Ali Sharpasand]("http://m.a.sharpasand.com/")

---

### Post by sudodus on 2013-03-02
Welcome to the Ubuntu Forums :-)

> **malish said:**
> Try running

sudo apt-get update

before your command, if it didn't work, let us know the output of the following command:

cat /etc/apt/sources.list

Wishes,
[Mohammad Ali Sharpasand]("http://m.a.sharpasand.com/")

+1

Try also
```
 sudo apt-get upgrade
```
and then
```
sudo apt-get install vim
```
again

---

### Post by sudodus on 2013-03-02
Maybe you have not enabled recommended uppdates 'precise-updates'. Run
```
sudo synaptic
```
select
Settings -- Program Sources (or similar, I don't use English)
and the tab Updates
and tick Recommended updates (precise-updates)

Click on Reread, and now when you type **vim **in Synaptic's search window and it should be found, and you can install it either with Synaptic (right-click and select for install) and confirm by clicking the tick icon at the top of the Synaptic window, or with the original command line that you tried before.

---

### Post by schragge on 2013-03-02
+2 to what **malish**  and **sudodus** said.

Looks very much as if your */etc/apt/sources.list* is corrupted in some subtle way. If this is the case, you'll get a more precise error message on *sudo apt-get update*. But instead of *cat /etc/apt/sources.list*, I'd suggest you run
```
grep '^[^#]' /etc/apt/sources.list{,.d/*}
``` This will also display contents of any APT sources in */etc/apt/sources.list.d/* that usually get installed by PPAs. The corrupt line may be there.

BTW, do you use some apt caching proxy like [apt-cacher(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/apt-cacher.1.html") or [apt-cacher-ng(8)]("http://manpages.ubuntu.com/manpages/precise/en/man8/apt-cacher-ng.8.html")?

---

