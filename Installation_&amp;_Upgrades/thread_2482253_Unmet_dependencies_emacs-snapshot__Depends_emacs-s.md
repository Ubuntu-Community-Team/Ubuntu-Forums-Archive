---
title: "Unmet dependencies: emacs-snapshot : Depends: emacs-snapshot-common"
date: 2022-12-26
forum: Installation &amp; Upgrades
---

### Post by asubscriber on 2022-12-26
Linux Ubuntu 22.04
Emacs 27.1
```
sudo apt install inxi
```
But get error:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 emacs-snapshot : Depends: emacs-snapshot-common (= 20221225:105176-48db8b68a8~ubuntu22.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by ActionParsnip on 2022-12-26
What is the output of
```

apt cache policy emacs-snapshot emacs-snapshot-common; lsb_release -a; uname -a

```

---

### Post by ActionParsnip on 2022-12-26
I smell a PPA

---

### Post by asubscriber on 2022-12-26
```
E: Invalid operation cache
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy
Linux laptop 5.15.0-56-generic #62-Ubuntu SMP Tue Nov 22 19:54:14 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by ActionParsnip on 2022-12-26
Apologies
```

apt-cache policy emacs-snapshot emacs-snapshot-common; lsb_release -a; uname -a

```

---

### Post by asubscriber on 2022-12-26
```
apt-cache policy emacs-snapshot emacs-snapshot-common; lsb_release -a; uname -a
emacs-snapshot:
  Installed: 20221225:105176-48db8b68a8~ubuntu22.04.1
  Candidate: 20221226:105180-2ffe1494e1~ubuntu22.04.1
  Version table:
     20221226:105180-2ffe1494e1~ubuntu22.04.1 500
        500 [https://ppa.launchpadcontent.net/ubuntu-elisp/ppa/ubuntu](https://ppa.launchpadcontent.net/ubuntu-elisp/ppa/ubuntu) jammy/main amd64 Packages
 *** 20221225:105176-48db8b68a8~ubuntu22.04.1 100
        100 /var/lib/dpkg/status
emacs-snapshot-common:
  Installed: (none)
  Candidate: 20221226:105180-2ffe1494e1~ubuntu22.04.1
  Version table:
     20221226:105180-2ffe1494e1~ubuntu22.04.1 500
        500 [https://ppa.launchpadcontent.net/ubuntu-elisp/ppa/ubuntu](https://ppa.launchpadcontent.net/ubuntu-elisp/ppa/ubuntu) jammy/main amd64 Packages
        500 [https://ppa.launchpadcontent.net/ubuntu-elisp/ppa/ubuntu](https://ppa.launchpadcontent.net/ubuntu-elisp/ppa/ubuntu) jammy/main i386 Packages
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy
Linux laptop 5.15.0-56-generic #62-Ubuntu SMP Tue Nov 22 19:54:14 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by ActionParsnip on 2022-12-26
Yep. A PPA. Remove the packages you installed from the PPA. Remove the PPA then use the default packages from the default repository. Alternatively you can contact the PPA maintenaner and report the issue.

---

### Post by asubscriber on 2022-12-27
I removed all PPA but it not help:
```

sudo apt install inxi
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 emacs-snapshot : Depends: emacs-snapshot-common (= 20221225:105176-48db8b68a8~ubuntu22.04.1) but it is not installable
 virtualbox-7.0 : Depends: libqt5core5a (>= 5.15.1) but it is not going to be installed
                  Depends: libqt5dbus5 (>= 5.14.1) but it is not going to be installed
                  Depends: libqt5gui5 (>= 5.14.1) but it is not going to be installed or
                           libqt5gui5-gles (>= 5.14.1) but it is not going to be installed
                  Depends: libqt5help5 (>= 5.15.1) but it is not going to be installed
                  Depends: libqt5opengl5 (>= 5.0.2) but it is not going to be installed
                  Depends: libqt5printsupport5 (>= 5.0.2) but it is not going to be installed
                  Depends: libqt5widgets5 (>= 5.15.1) but it is not going to be installed
                  Depends: libqt5x11extras5 (>= 5.6.0) but it is not going to be installed
                  Depends: libqt5xml5 (>= 5.0.2) but it is not going to be installed
                  Recommends: libsdl-ttf2.0-0 but it is not going to be installed
                  Recommends: gcc but it is not going to be installed
                  Recommends: make or
                              build-essential but it is not going to be installed or
                              dpkg-dev but it is not going to be installed
                  Recommends: binutils but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by coffeecat on 2022-12-27
@asubscriber, I've edited your posts to add code tags to your terminal outputs. See how that restores the columnar formatting that was lost by posting the output straight into the main body of the post, and makes the output much easier to read. I've also removed the font formatting that you used to highlight the output as the code boxes do a much better job.

Please enclose all terminal output between BBCode [noparse]```
 and 
```[/noparse] tags for readability. There's a link in my sig for how to do this if you need it.

Good luck with finding a solution.

---

### Post by tea for one on 2022-12-27
> **asubscriber said:**
> I removed all PPA but it not help:
```
emacs-snapshot : Depends: emacs-snapshot-common (= 20221225:105176-48db8b68a8~ubuntu22.04.1) but it is not installable

```
Was emacs-snapshot installed via the ppa?
As suggested previously by ActionParsnip - Remove the packages you installed from the PPA

---

### Post by asubscriber on 2022-12-27
I can't do anything. When I try something I get the next error (always):

```
sudo apt autoremove


Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 emacs-snapshot : Depends: emacs-snapshot-common (= 20221225:105176-48db8b68a8~ubuntu22.04.1) but it is not installable
 virtualbox-7.0 : Depends: libqt5core5a (>= 5.15.1) but it is not installed
                  Depends: libqt5dbus5 (>= 5.14.1) but it is not installed
                  Depends: libqt5gui5 (>= 5.14.1) but it is not installed or
                           libqt5gui5-gles (>= 5.14.1) but it is not installed
                  Depends: libqt5help5 (>= 5.15.1) but it is not installed
                  Depends: libqt5opengl5 (>= 5.0.2) but it is not installed
                  Depends: libqt5printsupport5 (>= 5.0.2) but it is not installed
                  Depends: libqt5widgets5 (>= 5.15.1) but it is not installed
                  Depends: libqt5x11extras5 (>= 5.6.0) but it is not installed
                  Depends: libqt5xml5 (>= 5.0.2) but it is not installed
                  Recommends: libsdl-ttf2.0-0 but it is not installed
                  Recommends: gcc but it is not installed
                  Recommends: make or
                              build-essential but it is not installed or
                              dpkg-dev but it is not installed
                  Recommends: binutils but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

---

### Post by asubscriber on 2022-12-27
I can't do anything. When I try to do something I get the next error (always):

```
sudo apt autoremove


Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 emacs-snapshot : Depends: emacs-snapshot-common (= 20221225:105176-48db8b68a8~ubuntu22.04.1) but it is not installable
 virtualbox-7.0 : Depends: libqt5core5a (>= 5.15.1) but it is not installed
                  Depends: libqt5dbus5 (>= 5.14.1) but it is not installed
                  Depends: libqt5gui5 (>= 5.14.1) but it is not installed or
                           libqt5gui5-gles (>= 5.14.1) but it is not installed
                  Depends: libqt5help5 (>= 5.15.1) but it is not installed
                  Depends: libqt5opengl5 (>= 5.0.2) but it is not installed
                  Depends: libqt5printsupport5 (>= 5.0.2) but it is not installed
                  Depends: libqt5widgets5 (>= 5.15.1) but it is not installed
                  Depends: libqt5x11extras5 (>= 5.6.0) but it is not installed
                  Depends: libqt5xml5 (>= 5.0.2) but it is not installed
                  Recommends: libsdl-ttf2.0-0 but it is not installed
                  Recommends: gcc but it is not installed
                  Recommends: make or
                              build-essential but it is not installed or
                              dpkg-dev but it is not installed
                  Recommends: binutils but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

---

### Post by tea for one on 2022-12-27
Open a terminal and enter:-
```
sudo apt remove emacs-snapshot
```
Is the package removed successfully?

---

### Post by asubscriber on 2022-12-27
Not help. Same error:

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 virtualbox-7.0 : Depends: libqt5core5a (>= 5.15.1) but it is not going to be installed
                  Depends: libqt5dbus5 (>= 5.14.1) but it is not going to be installed
                  Depends: libqt5gui5 (>= 5.14.1) but it is not going to be installed or
                           libqt5gui5-gles (>= 5.14.1) but it is not going to be installed
                  Depends: libqt5help5 (>= 5.15.1) but it is not going to be installed
                  Depends: libqt5opengl5 (>= 5.0.2) but it is not going to be installed
                  Depends: libqt5printsupport5 (>= 5.0.2) but it is not going to be installed
                  Depends: libqt5widgets5 (>= 5.15.1) but it is not going to be installed
                  Depends: libqt5x11extras5 (>= 5.6.0) but it is not going to be installed
                  Depends: libqt5xml5 (>= 5.0.2) but it is not going to be installed
                  Recommends: libsdl-ttf2.0-0 but it is not going to be installed
                  Recommends: gcc but it is not going to be installed
                  Recommends: make or
                              build-essential but it is not going to be installed or
                              dpkg-dev but it is not going to be installed
                  Recommends: binutils but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by ajgreeny on 2022-12-27
Have you tried running the command suggested in the much of the terminal output shown? ```
sudo apt --fix-broken install
```
If not do so now and tell us once again the output that you see.

---

### Post by asubscriber on 2022-12-27
Yes, this help.

sudo apt --fix-broken install


Now I success install:

sudo apt install inxi

---

### Post by ajgreeny on 2022-12-27
Brilliant!

Please mark the thread as SOLVED by clicking on the Thread Tools menu at the top right hand side of the thread.
It is a great help to other users searching the forum.

---

### Post by tea for one on 2022-12-28
@asubscriber
I think that your comment in post 14 [COLOR="#000080"]Not help. Same error[/COLOR]: is misleading.
You can see from the terminal output that [COLOR="#000080"]emacs-snapshot[/COLOR] has been removed.
There is no guarantee that [COLOR="#000080"]sudo apt --fix-broken install[/COLOR] would have been successful without removing emacs-snapshot first.

Also, in your original post, the error message did not contain any reference to Virtualbox and it appears that you had multiple dependency problems.

Anyway, as suggested by ajgreeny, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

