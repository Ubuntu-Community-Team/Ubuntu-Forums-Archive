---
title: "Group permissions not inheriting"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by duffny on 2007-11-07
I've been searching all night, but can't find anything that will work.  What I'm trying to setup is folder permission inheritance.  I have a shared folder with owner(rwx):group(rws):other(---) set the way I want it, and have set groupID and sticky and every possible combination of all the above to no avail.  When a folder/file is created within this shared folder, it gets:  owner=rw, group=r, other=r.  Period, no matter what.  The group is correct, but the permissions aren't the same.  Am I missing something or is there something buggy about permission inheritance in Ubuntu 7.10?

Some of the commands I've tried (honestly can't remember everything):

sudo chmod 2770 <path/folder>

sudo chmod g+s <path/folder>

sudo chmod g+rwxs <path/folder>

And everything else I've found scattered around the internet and here over the last several hours.  Thanks for any help, and sorry if this is just something stupid that I'm missing.

---

### Post by kidders on 2007-11-09
Hi there,

> **duffny said:**
> is there something buggy about permission inheritance in Ubuntu 7.10?Thankfully, bugs of this nature are (in my experience anyway) totally unheard of.

There is no concept of *permissions* inheritance in Linux. As you've noticed, you can override *ownership* on a per-directory basis, with the SGID bit, but the permissions assigned to a file as it's created are controlled by the umask set in the environment that creates it. To find out what yours is, just type "umask".

Creators of files essentially get total control over the permissions assigned to them ... although there are ways of enforcing stricter permissions than those a file appears to have, there is no mechanism for forcing looser access control, which is what you seem to want to do. To get the effect you're after...[LIST]
[*]Users will have to chmod g+rw things they create.
[*]Users could set their own umask (eg in a login script), and then start creating files.
[*]You could administratively set your users' umasks, so files they created were automatically made g+rwx as well as u+rw. Preventing a user overriding that setting would be tricky though.
[/LIST]

The reason for this is that users need to be able to trust that they can safely create files, without having to constantly check for reasons why more users than they intend might be able to access them.

I hope that helps.

---

### Post by duffny on 2007-11-09
Thank you very much for the explanation.  Now I get it and believe I have solved my dilema.  May not be the best practice, but it's only a personal home network behind a firewall, so security isn't a big concern.  I changed the umask in the /etc/profile script and seems to be doing what I want now.

---

### Post by kidders on 2007-11-09
Glad I could help. :-)

> **duffny said:**
> I changed the umask in the /etc/profile script and seems to be doing what I want now.That's perfectly acceptable, really ... at least on a home network. You shouldn't have any security issues, as long as you don't use your umask to grant "o+w".

All the best.

---

