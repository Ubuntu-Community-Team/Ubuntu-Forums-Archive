---
title: "Random Reboots"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by Warlx on 2008-10-11
[SIZE="3"][SIZE="3"]Hello Ubuntu community. I am new(very new) to Ubuntu/Linux in general. I have been running Ubuntu Hardy 8.04 for about a month and just recently have been getting random reboots of the system. These reboots have no rhyme or reason and their is no pattern that I can see, they don't happen at any specific interval. I am running Ubuntu on an old Emachines T4155- Intel 1.5GHZ,256MB SyncDram,60GB HD/UltraDMA100,32MB APG 3D Geforce2 MX200. Any assistace anyone can provide will be helpful. I will continue to research on my end as well.[/SIZE]
                            Thanks in advance
                                        Warlx:confused:[/SIZE]

---

### Post by seldon77 on 2008-11-14
I was plagued by this as well with Hardy.

It seems like it is a rare problem with 8.04 & I discussed it & brought it up on Launchpad bugs.

There wasn't any solution but as soon as I upgraded to 8.10 (most recent version of Ubuntu) the problem went away. There have been some changed implemented in the shutdown routine via the Gnome developers.

You can upgrade to the next version by fiddling around with the Administration : Software Sources : Updates : Release Updates section and choosing it to let you know if a new version is now available. Then click the Update Manager and allow it to upgrade your version of Ubuntu to 8.10. Takes 15 minutes - fixed it for me.

---

