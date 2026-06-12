---
title: "Ubuntu 16.04 Update Manager Repeatedly Asks for Partial Upgrade"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by allan.w.macdonald on 2019-01-28
The GUI Update Manager keeps asking for a partial upgrade.  This started happening recently.  sudo apt-get update and upgrade yields:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Why is the GUI Update Manager disagreeing with the command line tool apt-get?  Are these two programs relying on different data?  Shouldn't these two programs work the same behind the scenes?

How to I rationalize these two?  Is one of these programs broken?  Which one should I trust?  What can I do to correct the issue?

As an aside, the GUI window is confusing.  There is a "Continue" button and a "Partial Upgrade" button.  Why the choice?  I get different (and even more confusing) results depending on which button I click:

If I click "Partial Upgrade", and enter my password at the prompt, eventually I see "The software on this computer is up to date.
There are no upgrades available for your system. The upgrade will now be canceled."

However, if I run the Updates Manager tool again, and, when the Partial Upgrade dialog appears again, click "Continue", I see a notice saying, "Software index is broken  It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

I do not have "Synaptic" installed so I did not try this suggestion but the other suggestion, "sudo apt-get install -f" yields the following:
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by #&amp;thj^% on 2019-01-28
I always trust the terminal output first but >>>You can check the difference (if Any)) with:
Open a terminal and run this:
```
xprop | awk '($1=="_NET_WM_PID(CARDINAL)") {print $3}' | xargs ps h -o cmd

```

Now click on a running instance of the GUI (Software updater).

The command used to run it should then be printed in the terminal.

One other offer here is:
```
sudo apt install -f
sudo dpkg --configure -a
sudo apt dist-upgrade
```

---

### Post by allan.w.macdonald on 2019-01-28
"Now click on a running instance of the GUI (Software updater)."

Click where?  Anywhere in the window?  On a particular button?

---

### Post by #&amp;thj^% on 2019-01-28
Anywhere in/on the Software updater
EDIT: apt-get will NOT consider "suggested" packages as updates, while Update Manager does. It <Update Manager> also includes packages which apt-get would only install/upgrade with "dist-upgrade". Additionally, I believe Update Manager maintains its own package cache which is only automatically updated daily and thus may not always be synchronized with the APT package cache.
As a result I don't use "apt-get" any more, I only use "apt" with 16.04 and higher

---

### Post by allan.w.macdonald on 2019-01-28
Here are the outputs of the commands you suggested:
```
username@computer:~$ xprop | awk '($1=="_NET_WM_PID(CARDINAL)") {print $3}' | xargs ps h -o cmd
/usr/bin/python3 /usr/bin/update-manager
username@computer:~$ sudo apt install -f
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
username@computer:~$ sudo dpkg --configure -a
username@computer:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
username@computer:~$
```

@1fallen, I do not understand what your suggestions are intended to provide.  I get the same results from apt as I get from apt-get and printing out the name of the gui application does not, to me, appear to provide any information as to what the problem might be.  Besides, what is the difference between apt and apt-get anyway?  I have seen many forum postings that reference one or the other without explanation.  What is the definitive update management tool for this version of Ubuntu?

Furthermore, I still do not understand why Update Manager is behaving the way it is.  How can I force Update Manager to "update" its "package cache", so that it is truly "synchronized with the APT package cache", whatever that means?

Does anybody have another suggestion?

---

### Post by #&amp;thj^% on 2019-01-28
So that all looks good! :)
I'm strictly a CLI (Terminal) guy.

---

### Post by allan.w.macdonald on 2019-01-28
Thanks for trying, 1fallen!

Anybody else out there who knows about the GUI?  Should I post a bug and, if so, where?

Thanks in advance!

---

### Post by deadflowr on 2019-01-28
You don't happen to have -proposed enabled?
(Or maybe -backports, or other extra repositories?)
Similar issue here, 
[https://askubuntu.com/questions/913574/update-manager-keeps-asking-for-partial-upgrade]("https://askubuntu.com/questions/913574/update-manager-keeps-asking-for-partial-upgrade")
Though no definitive answer.

---

### Post by #&amp;thj^% on 2019-01-28
Along with deadflowr's advice: Even though I thought I was clear, and sorry if I wasn't.
Now to update the cache with:
```
sudo /usr/bin/python3 /usr/bin/update-manager
```

---

### Post by allan.w.macdonald on 2019-01-28
I turned off backports and the problem still exists.
Anyway, I've reported a bug:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1813626](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1813626)
and referenced this discussion in the bug report.

> **1fallen said:**
> Along with deadflowr's advice: Even though I thought I was clear, and sorry if I wasn't.
Now to update the cache with:
```
sudo /usr/bin/python3 /usr/bin/update-manager
```

This action results in the same behaviour.

---

### Post by gnwiii on 2019-01-30
On the difference between apt and apt-get, 
[https://debian-handbook.info/browse/stable/sect.apt-get.html]("https://debian-handbook.info/browse/stable/sect.apt-get.html") says "apt is a second command-line based front end provided by APT which overcomes some design mistakes of apt-get."

---

### Post by allan.w.macdonald on 2019-01-30
Important to know!  Thanks!

---

