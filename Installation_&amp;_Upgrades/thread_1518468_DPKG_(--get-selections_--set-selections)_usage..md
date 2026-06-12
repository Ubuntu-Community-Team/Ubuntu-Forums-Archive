---
title: "DPKG (--get-selections --set-selections) usage."
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Nibinaear on 2010-06-26
Hi. I am trying to find a way of backing up my packages or at least the names of them and then reinstall them after a complete format and reinstall. 

I've found the dpkg function and have used the get-selections command to backup the package names. I'm now trying to run the set-selections command to test out the file but I get the error:

dpkg: need an action option

Here is what I'm trying to run:

dpkg &#8722;&#8722;set&#8722;selections < /home/daniel/get-selections

get-selections is my input file. So what am I doing wrong please?

---

### Post by oldfred on 2010-06-26
I had it in my home and just ran it without the /home/fred

# Finally, install all the packages from previous install
# must have saved ubuntu-files from previous install to this directory
dpkg --set-selections < ubuntu-files
apt-get -y update
apt-get dselect-upgrade

---

### Post by Nibinaear on 2010-06-27
> **oldfred said:**
> I had it in my home and just ran it without the /home/fred


Thanks oldfred. Seemed to work.

Just to clarify, I used cd to get to the right directory and then ran the --set-selections command without the full directory.

---

