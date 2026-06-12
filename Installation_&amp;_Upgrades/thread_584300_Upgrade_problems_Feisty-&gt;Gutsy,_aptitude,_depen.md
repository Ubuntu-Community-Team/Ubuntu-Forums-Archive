---
title: "Upgrade problems: Feisty-&gt;Gutsy, aptitude, dependencies, &quot;Score is -139&quot;"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Russellkhan on 2007-10-20
Hi, 

I'm trying to upgrade to Gutsy from Feisty on a Kubuntu box with a 686 kernel. Here's what I did:

[LIST]
[*]sudo aptitude update
[*]sudo aptitude upgrade (just to get my feisty fully up to date before starting the upgrade process)
[*]Open /etc/apt/sources.list, replace all occurrences of "feisty" with "gutsy"
[*]sudo aptitude update
[*]sudo aptitude dist-upgrade
[/LIST]

Here I ran into some problems. Here's the relevant terminal output:
```

813 packages upgraded, 239 newly installed, 15 to remove and 0 not upgraded.
Need to get 830MB of archives. After unpacking 655MB will be used.
The following packages have unmet dependencies:
  linux-restricted-modules-686: Depends: linux-restricted-modules-generic (= 2.6.20.16.28.1) but 2.6.22.14.21 is to be installed.
  linux-image-686: Depends: linux-image-generic (= 2.6.20.16.28.1) but 2.6.22.14.21 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
kscreensaver [4:3.5.6-0ubuntu1 (now)]
ksmserver [4:3.5.6-0ubuntu20.7 (now)]
linux-image-generic [2.6.20.16.28.1 (now)]
linux-restricted-modules-2.6.20-16-generic [2.6.20.5-16.29 (now)]
linux-restricted-modules-generic [2.6.20.16.28.1 (now)]

Score is -139

Accept this solution? [Y/n/q/?] ?

```

I'm not sure if it's safe to go on from here or if I should back out and go back to Feisty for now. I've left the terminal in that state for now until I figure out what the best next step is. 

If anyone can give me a clue, I'd sure appreciate it. 

Thanks,

Russ

---

### Post by Pumalite on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by Russellkhan on 2007-10-21
Hi, thanks for the response, but could you tell me more about gksu and update-manager? Neither one seems to have a manpage, and the only place I find gksu on my system is at /usr/share/icons/mono/scalable/apps/gksu.svgz .

Specifically, if I were to go with this approach, should I undo what I've already done with my previous approach? What exactly do each of these do? If update-manager runs into the same problems that aptitude did, what does it do to resolve them? 

According to the second post in the thread you linked, the method I used only causes problems when there are external repositories. I don't have any.

---

### Post by Russellkhan on 2007-10-22
Hi, sorry for the bump, but I could really use some help with this problem.

A bit of googling tells me that gksu is a gnome app, which would be why it isn't on my Kubuntu machine. I'm not sure what the process for installing it would be since I'm already halfway to an upgrade via aptitude. 

A solution that works from terminal would be far preferable since I'm accessing the machine in question via ssh from a Mac. 

Does anyone know anything about this to help me out?

Thanks,

Russ

---

