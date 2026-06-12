---
title: "repository package list"
date: 2024-02-23
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2024-02-23
where can i get a complete list of all packages in the 20.04 and 22.04 repository?  and where should i expect to see the list for 24.04 when it is ready?

---

### Post by deadflowr on 2024-02-23
There are multiple repositories.
You can download the package lists gz files from here 
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
you'd need to go down a few levels.
First to the release (focal,jammy,noble) and whichever either the updates, securty, backports, etc.
then you need to drop down another level and select which main,universe,multiverse or restricted.
then in each you would need to select binary-amd64 and finally you'd select packages,gz, or .xz.
It'll be a lot of work, so good luck


If you happen to have any release installed the files for that release are installed on your system at /var/lib/apt/lists
apt happens to collate the files in here to make them easily readable in apt or other package management tools like synaptic.

---

### Post by Rubi1200 on 2024-02-24
I usually do this a different way:
1. first here [https://packages.ubuntu.com/](https://packages.ubuntu.com/)
2. then to the releases, for example, 20.04 [https://packages.ubuntu.com/focal/](https://packages.ubuntu.com/focal/)
3. scroll all the way down to the bottom and you can download a text of all packages [https://prnt.sc/2OrUMUZm5-Uh](https://prnt.sc/2OrUMUZm5-Uh)

Noble packages should also appear on the main page when relevant.

---

### Post by Skaperen on 2024-02-26
both results look good.  first one looks like it is all the database info.  a Python script should be able to get w3hat i want.  second one looks good, too.  the compress text list i succinct.

---

### Post by Rubi1200 on 2024-02-27
Glad we were able to help.

Please use Thread Tools to mark as Solved so others can also find the information.

---

