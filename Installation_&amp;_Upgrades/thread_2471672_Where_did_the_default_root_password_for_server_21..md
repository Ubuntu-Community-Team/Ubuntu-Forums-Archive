---
title: "Where did the default root password for server 21.10 go"
date: 2022-02-06
forum: Installation &amp; Upgrades
---

### Post by foxsquirrel on 2022-02-06
Did not realize it was an issue until now. Installing a git server and cannot change directory permissions on a new user "git". Really did not want that "git" account to have sudo and do not want to install it on the main account that has sudo access. Any suggestions because "git gui" is having problems connecting to server.

---

### Post by TheFu on 2022-02-06
There is no root password. Ubuntu uses sudo.

If you are using a VPS, then you'll need to check the local information, since there isn't any root password on Ubuntu Server or Desktop.

---

### Post by foxsquirrel on 2022-02-06
> **TheFu said:**
> There is no root password. Ubuntu uses sudo.



Yes, problem is I don't want to add "git" user to the sudo group. While logged in as user "git" I cannot change some of the file permissions. To change all directories would require adding "git" to the sudo group. The issue with connecting "git gui" to 21.10 server is a permission error from the error messages.

---

### Post by schragge on 2022-02-06
Make user **git** member of the group that owns the directories in question, and make them group-writable.

---

### Post by TheFu on 2022-02-06
> **schragge said:**
> Make user **git** member of the group that owns the directories in question, and make them group-writable.

Exactly.

Don't forget the setgid flag in the permissions for all the directories under git.

There's a free book - ProGIT.  I vaguely remember reading about half a page to understand setting up a centralized git repo for the first team of programmers.

I've never used "git gui", whatever that is.  Git from a client uses ssh and honors all expected UNIX file and directory permissions.  Setup ssh-keys and the file/directory group permissions correct and it "just works."  It must be 12 yrs since I setup my first git server for a company. If an end-user wants a GUI, that's fine. I only setup the normal, expected, git-over-ssh connection.  I've seen some of the devs using IDE integrations to our git server(s). They didn't need anything extra.  They get git and only git.  Project leaders get full ssh into the system, so they can setup more repos with git.  Of course, only people with write authority can alter the code repos.

We already put each team member into a team-specific group here, so that's usually the group we use for the git project directory ownership too.
[Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) explains how to setup directories for teams to work together. Hope it helps.

---

### Post by foxsquirrel on 2022-02-06
> **TheFu said:**
> Exactly.




I've never used "git gui", whatever that is. 

 Thank you very much for assisting me with this.

Just got it going, removed everything on client and server and started over again, reinstalled again and now it works.... Don't have a clue in the world what went wrong. 
[https://www.git-scm.com/docs/git-gui](https://www.git-scm.com/docs/git-gui)

---

