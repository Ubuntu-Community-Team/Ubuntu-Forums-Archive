---
title: "An error occured. Please try package manager"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by Pushpalanka on 2011-03-28
This what i got when tried to run package manager


[B][FONT=Georgia]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/FONT][/B]

I still did not see any effect of this. But wanna solve it.:confused:

---

### Post by Sean Moran on 2011-03-28
> **Pushpalanka said:**
> This what i got when tried to run package manager


[B][FONT=Georgia]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/FONT][/B]

I still did not see any effect of this. But wanna solve it.:confused:
This is one I've never had before, but two possible guesses if you haven't tried already:

sudo apt-get update
AND/OR
sudo apt-get -f check

The first command is meant to retrieve the current package lists for apt from the online repositories, including security.

The second one will attempt to fix and [s]clean[/s] check (sorry) what is already there.  The order isn't all that important, but check to see if one or the other works, and please let me know so that I can help other people more readily if this problem arises again.

---

