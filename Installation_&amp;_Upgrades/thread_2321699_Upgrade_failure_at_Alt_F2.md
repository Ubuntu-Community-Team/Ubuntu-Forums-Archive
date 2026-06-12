---
title: "Upgrade failure at Alt F2"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by mchlmcquown on 2016-04-23
Every time I try to do the upgrade via update, I get as far as clicking Alt F2. An icon of three gear wheels appears, but then nothing happens. If I hit ENTER, nothing; if I double-click the icon, nothing.
On the second try, I somehow ended up installing 15.10, but -- it opened in the kernel, and I couldn't get out of there. I tried Alt F7, but nothing. Finally, I reinstalled 14.04, but I am back to the same upgrade problem. I get as far as typing in 'Update manager' at the top of the screen and and I get the icon, then nothing.

---

### Post by deadflowr on 2016-04-24
alt+F2 is what is known as a run dialog.
Which runs commands, as they would be run in a terminal.
so where as *Update manager* won't do anything.
*update-manager* will.

But to add a quick question, is the intent to upgrade from 14.04 to 16.04?

---

### Post by mchlmcquown on 2016-04-24
Yes.

---

### Post by mchlmcquown on 2016-04-24
So far, no good. I tried update-manager, but got the usual checking for updates, "this computer is up to date" response.
How do I get a CD?

---

### Post by deadflowr on 2016-04-24
It's no good, because the update channel from 14.04 to 16.04 is not officially open to users.
It's still under development for that particular upgrade method.
Unlike an upgrade from 15.10 to 16.04, an upgrade from 14.04 to 16.04 will make a lot more changes to the system, so they still need to make sure nothing breaks.
(Or at the very least try to minimize breakages)
there is also the fact that most mission-critical production machines are running LTS releases, so they do not want to hamper users running those.
So that upgrade path might not be considered stable at the moment.

You can access it, though.
By doing the same thing as you have done, except instead of just *update-manager* in the run dialog, run
```
update-manager -d
```
the -d stands for development.
This should give you the option to upgrade to 16.04 in the updater window, after it finishes it's checking.

If you do try this method, please read through the release notes, which will be linked 
(usually the relase notes are linked in that first page that will open, but just in case here
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes")
in particular, look at the sections below the KNOWN ISSUES, to make sure nothing about your setup has a known problem.

---

### Post by mchlmcquown on 2016-04-24
Thanks. I'll give it a go. I love Linux, I love Ubuntu, but it often leaves me feeling stupid. I really need an Ubuntu 101.

---

### Post by mchlmcquown on 2016-04-24
Nope. Just says my computer is up to date. I read the release notes. Could be in Greek for all I understand it.

---

### Post by deadflowr on 2016-04-24
Inside the program Software and Updates, in the Updates tab, what is the status of the Notify me of a Ubuntu version say?

---

### Post by mchlmcquown on 2016-04-26
For long-term support versions.

---

### Post by deadflowr on 2016-04-26
Hmm,
perhaps the command line method might show something
What does
```
do-release-upgrade -d
```
show you?
No need to enter sudo or a password when that is prompted, this is just for checking it.

---

### Post by bappy2 on 2016-04-26
please try by

Alt+F12

it will work

---

### Post by mchlmcquown on 2016-04-26
It gives me an icon of three gear wheels, but when I hit ENTER, it vanishes

---

### Post by mchlmcquown on 2016-04-26
I get an icon of three gear wheels with do-release-upgrade -d  underneath it. When I hit ENTER, it just disappears

---

### Post by deadflowr on 2016-04-27
Sorry, I thought a mentioned the do-release-upgrade command needs to run inside a terminal.
it should output something like this:
```
john@doe:~$ do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,265 kB]                                                  
Fetched 1,265 kB in 6s (141 kB/s)                                              
authenticate 'xenial.tar.gz' against 'xenial.tar.gz.gpg' 
extracting 'xenial.tar.gz'
[sudo] password for john:
```
just press ctrl +c to cancel it.

---

### Post by mchlmcquown on 2016-04-28
I get an icon consisting of three gear wheels with the label "do-release-upgrade  -d"

---

### Post by mchlmcquown on 2016-04-28
I keep posting this and not seeing it on the page. When I type in the command, I get an icon of three gear wheels with the command underneath it.

---

### Post by deadflowr on 2016-04-28
> **mchlmcquown said:**
> I keep posting this and not seeing it on the page. When I type in the command, I get an icon of three gear wheels with the command underneath it.

?

The command needs to run in a terminal.
Not the alt+f2 run dialog.

press ctrl + alt + T to quickly open a terminal.

---

### Post by mchlmcquown on 2016-04-29
'tar' or 'tahr'?

---

### Post by mchlmcquown on 2016-04-29
Aha!  Upgrade seems to have worked. Thank you very much!

---

