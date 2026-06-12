---
title: "Adept Unable to install"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by JFo NZ on 2007-09-09
Hi there. Earlier today I ran Adept Updater to install the latest updates and the install process failed. The error shown read "*There was an error committing changes. Possibly there was a problem  downloading some packages or the commit would break packages*"

Now I am unable to install anything with Adept. I have tired changing repositories. I have run apt-get clean. But Adept still wont install and I get the error message above.

When I run "sudo apt-get install" I get the following output:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am running KUbuntu 7.4

Any ideas?

---

### Post by Pumalite on 2007-09-09
This is a 'bum' fix, but is better than no apt-get.

To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
__________________

---

### Post by JFo NZ on 2007-09-10
Thanks that helped point me in the right direction. Changing the status didn't work but I played around and managed to fix it.

The problem package was tzdata. This is how I fixed it.

(Back up file /var/lib/dpkg/status just in case)
Remove the entire section of text for the package tzdata in the file /var/lib/dpkg/status. This makes apt-get think that it is not installed I guess.

Run "sudo apt-get install tzdata". This downloaded and installed a fresh copy of the package and installed with no problems.

Problem fixed! :)

---

### Post by Pumalite on 2007-09-10
Good for you. Congrats!

---

