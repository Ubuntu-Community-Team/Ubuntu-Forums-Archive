---
title: "copy home folder to new version"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by Priswell on 2007-04-09
I would like to tar my home folder in Ubuntu 6.10 so I can untar it in Ubuntu 7.04. Could someone please tell me how to do that?

---

### Post by moffa on 2007-04-10
If you are just upgrading your home folder shouldn't change.  Your home folder would be under /home/[username]

---

### Post by jiminid on 2007-04-11
How would you copy /home to your new version (i.e. feisty) if you wanted to do a clean install of feisty into your edgy partitions? Is that what you're asking about?

Hope so, casue that's what I would like to know. :)

---

### Post by Priswell on 2007-04-12
OK, what I've been trying to do is tar my personal folder from Edgy and untar the folder into my home directory in Feisty. I've been able to tar the folder now, but have been unable to untar it into my home folder. I've become root, and am in the home directory. I'm using the command:

tar -xvfz home.tar.gz

I get the following result in terminal:

tar: home.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

help?

---

### Post by bashologist on 2007-04-12
Here's an example of how you might be able to do this:
```
neko@debian:~/test$ ls -a
[COLOR="Silver"].  ..  a  .a  fff  .j[/COLOR]

neko@debian:~/test$ tar -cvvf "backup.tar" .
[COLOR="Silver"]drwxr-xr-x neko/neko         0 2007-04-12 13:52 ./
drwxr-xr-x neko/neko         0 2007-04-12 13:42 ./.a/
tar: ./backup.tar: file is the archive; not dumped
-rw-r--r-- neko/neko         0 2007-04-12 13:42 ./fff
-rw-r--r-- neko/neko         0 2007-04-12 13:41 ./.j
-rw-r--r-- neko/neko         0 2007-04-12 13:42 ./a[/COLOR]

neko@debian:~/test$ ls -a
[COLOR="Silver"].  ..  a  .a  backup.tar  fff  .j[/COLOR]

neko@debian:~/test$ mkdir extractmehere

neko@debian:~/test$ mv backup.tar extractmehere/

neko@debian:~/test$ cd extractmehere

neko@debian:~/test/extractmehere$ tar -xvvf "backup.tar"
[COLOR="Silver"]drwxr-xr-x neko/neko         0 2007-04-12 13:52 ./
drwxr-xr-x neko/neko         0 2007-04-12 13:42 ./.a/
-rw-r--r-- neko/neko         0 2007-04-12 13:42 ./fff
-rw-r--r-- neko/neko         0 2007-04-12 13:41 ./.j
-rw-r--r-- neko/neko         0 2007-04-12 13:42 ./a[/COLOR]

neko@debian:~/test/extractmehere$ ls -a
[COLOR="Silver"].  ..  a  .a  backup.tar  fff  .j[/COLOR]
```

---

### Post by Priswell on 2007-04-12
I'm sorry, I didn't understand. Too much code to read and sort through. I'm still rather new to linux. Let me try again.

I have Edgy running in a virtual machine under Windows. I used it long enough to get things configured the way I wanted them. Then I created another virtual machine of Feisty Fawn, liked it, and decided I'd just move into it. I wanted to move my settings and the few files I'd created to Feisty. So, I went into terminal, became root, moved to my Edgy home directory, and tarred my personal folder using:

tar -cjf home.tar.gz mydirectory

I copied this to my flash drive, closed down Edgy, booted up Feisty and copied home.tar.gz to the desktop. I went into terminal became root, moved the file to my home directory, and tried to untar it into mydirectory on Feisty.

tar -xvfz home.tar.gz

When I did so, I got the following error message:

tar: home.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

The funny thing is that I had just done this a couple of days ago on another machine, and now I can't recreate what I did.

---

