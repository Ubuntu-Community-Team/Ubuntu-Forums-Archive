---
title: "Has anyone started Ubuntu from init switch?"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-03-22
Ultimately, I need to install Ubuntu in a customized way on a machine I won't have physical access to.  But I do have a bootable USB memory stick that I can login to from remote.  The ideal I have is to install Ubuntu on a local machine, and replicate it to the hard drive on the remote machine via being logged in to the bootable USB memory stick.

But here's the issue.  I'd like to be able to boot over into the installed Ubuntu system while that USB memory stick is still in place.  I'm thinking of one of these possibilities:

1.  Reconfigure init to, instead of halting the system when it shuts down, to mount the root partition of the installed hard drive system as root, and execute its init program in place of the current one in PID 1.

2.  Use Kexec to boot into a whole new kernel (from the hard drive).

I will be installing 12.04 LTS Desktop version (because it needs to have X server running) when it comes out (can test the betas before then).  The USB memory stick has a modified Slackware64 13.37 on it.

---

