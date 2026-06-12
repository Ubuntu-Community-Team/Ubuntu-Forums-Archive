---
title: "private apt repository with ssh access"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by PutzFrau on 2012-03-05
Hi all!
I want to create a private apt repository that is accessed via ssh. I have been following these instructions: [http://www.debian-administration.org/articles/513](http://www.debian-administration.org/articles/513).

The problem I stumble upon is that even with everything set up for rsa authorization I still have to enter my password on apt-get update. I tried several combinations:

client and repository on the same machine (ubuntu 11.04) (deb ssh://repo@localhost:/path/to/repo ./)
repository running in virtual machine (ubuntu 11.04 and mint 12) (deb ssh://repo@<ip address>:/path/to/repo ./)
both client and repository running in virtual machine (ubuntu 11.04 and mint 12)

With every configuration I have to enter the password for repo, when I sudo apt-get update, even though there is no password on my client's rsa keys and I can ssh repo@host without password prompt.

If you have any idea what could be wrong with my configuration, please let me know.
Thank you!

---

### Post by Lars Noodén on 2012-03-05
Check that ~/.ssh/authorized_keys on the repository machine's account has the following:

1) it exists, 
2) is in the directory ~/.ssh which has the permissions 0700
3) itself has the permissions 0600

In other words, be sure that you can log in via the key manually first.

---

### Post by PutzFrau on 2012-03-05
Thanks for the answer, but unfortunately it didn't help.

I installed a debian Virtual Machine and from that Virtual Machine I can access the repository on my Host. I can also create another user with a repository on that Virtual Machine and access it in Debian within that Virtual Machine.

Unfortunately it does not work the other way round (Ubuntu accessing a repository on the Debian Machine), because that's what I need.

---

### Post by PutzFrau on 2012-03-05
Ok, finally solved it myself:
I didn't copy the key located in /root/.ssh but in ~/.ssh
And that caused me hours of work and installing OSs on VM. Well, I guess you learn the most from stupid mistakes.

---

### Post by Lars Noodén on 2012-03-05
Edit: never mind.

---

