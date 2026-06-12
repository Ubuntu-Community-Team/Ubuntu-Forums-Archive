---
title: "Difficulty upgrading - I'm being told that there's no release available"
date: 2024-09-08
forum: Installation &amp; Upgrades
---

### Post by misc-daminator on 2024-09-08
One of my machines is running 22.04.4 LTS

The settings are to upgrade to new LTS versions.

The other day, when running the Software Updater, I was told that a new LTS version was available.

It wasn't a good time, so I clicked the 'Ask Later' button.

Now is a good time, but I can't get either the Software Updater app, of the "do-release-upgrade" command line prompt to start the upgrade.

'do-release-upgrade' returns ...
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.

I don't know why it mentions a 'development' version. I didn't use -d.

Can anyone tell me what I'm doing wrong?

---

### Post by deadflowr on 2024-09-08
The release upgrade option was pulled back.
Why?
Issues were found.

So, not your fault.

---

### Post by coffeecat on 2024-09-08
It's probably to do with this: [https://lists.ubuntu.com/archives/ubuntu-release/2024-September/006225.html](https://lists.ubuntu.com/archives/ubuntu-release/2024-September/006225.html)

And presented in a more user-friendly way on OMGUbuntu: [https://www.omgubuntu.co.uk/2024/09/canonical-halts-ubuntu-24-04-lts-upgrades-again](https://www.omgubuntu.co.uk/2024/09/canonical-halts-ubuntu-24-04-lts-upgrades-again) 

Give it a few days.

---

### Post by misc-daminator on 2024-09-08
Great. Thanks for the quick response!

Looks like I was saved from a problematic upgrade!

---

