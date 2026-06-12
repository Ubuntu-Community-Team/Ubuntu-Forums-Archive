---
title: "package error....reinstall?"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by NeoLithium on 2006-12-27
Heya,
Alrighty, this is fun now, this was the last thing that I needed to do; however...I can't do it.  Below is what I run, and what I get fun. Not really, I've searched the forums and google, there's similar ones, but their solutions don't work, so I decided that i needed to post.  

I do have a seperate /home partition from when I installed (Thankfully, since I only have DVD-R disks.); is there way way to fix this, or should I just reinstall and move the /home.  Should that be the case, I haven't done that kind of reinstall yet; aside from just skipping formatting of my current /home, do I create the usual / swap and /home for the new install, and then just cp from /dev/hda3 to the new one...?

Man, I haven't done it in a while; but I ****ed somthing up good ;)
Thanks, 
Neo

```

neo@linux-notebook:$ sudo apt-get --purge remove postfix
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  postfix*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 2224kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152369 files and directories currently installed.)
Removing postfix ...
/var/lib/dpkg/info/postfix.prerm: line 29: /etc/init.d/postfix: No such file or directory
dpkg: error processing postfix (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

