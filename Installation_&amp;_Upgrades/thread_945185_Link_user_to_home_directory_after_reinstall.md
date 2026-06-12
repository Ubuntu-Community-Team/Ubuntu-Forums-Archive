---
title: "Link user to home directory after reinstall"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by robwales on 2008-10-12
I have a partitioned drive with the OS on one partition and the home directories in another. I have just reinstalled Hardy (including reformatting the drive) after having some problems and the main account linked to the home directory with no problems.
When I set up the other users I can't link them to their home folders in the same way.
Initially, when adding the user, (rhonda) I got a message saying that that home directory (/home/rhonda) already exists. I then gave the user a new directory (/home/rhonda2) and then went back in to User maintenance and could change the link back to the original (/home/rhonda) which was accepted.
[I]When I tried to log in as rhonda I received a message;
Users $home/.dmrc is being ignored. This prevetns the default session...[/I]
On clicking okay the message:
[I]Your session lasted less than 10 seconds
[/I]
Details showed:
[I]/etc/gdm/Xsessions: Beginning session setup...
Can't save user-dirs.dirs ... Permission denied
[/I]
I have checked and changed the permissions in the terminal to read
[I]drwxr-xr-x 39 rhonda rhonda  4096 2008-10-12 15:54 rhonda
[/I]
but still have the problem.

Any help with this is most appreciated
Rob

---

