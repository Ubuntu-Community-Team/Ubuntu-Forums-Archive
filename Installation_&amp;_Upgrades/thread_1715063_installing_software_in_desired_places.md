---
title: "installing software in desired places"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by el_diablo on 2011-03-26
Hello,

being happy with Ubuntu, I have a question about installing software.
Not having found an answer elsewhere, I ask here.

My system came with two partitions, one for the OS, one for its users.
I prefer to install software that is not part of the OS somewhere in the user-partition, e.g., /home/usr instead of /usr. Is possible to
choose the partition and directory where software is installed and how
is that done? If not, why this is not possible?

And so, everything installed in /usr. As /usr resides in the
OS-parition, the system begins to complain about the free space left
on that partition.

So, apart from wondering if installation to a non-default location is
possible, I would like to know how to move the downloaed applications
to a more convenient location in a transparent way.

Kind regards,

---

### Post by SeijiSensei on 2011-03-26
> **el_diablo said:**
> I prefer to install software that is not part of the OS somewhere in the user-partition, e.g., /home/usr instead of /usr.

It depends a lot on what software you're installing.  Packages from the Ubuntu repositories will be installed under /usr.  Tampering with that means that the packages won't be updated correctly so you should leave them alone.

If you're talking about pre-compiled binaries, you can create a directory under /home/username, call it /home/username/bin, and put them there.  Make sure they're marked executable.  Then edit $HOME/.bashrc and add the line

```
PATH="$HOME/bin:$PATH"
``` 

to the end of the file.  Don't create a /home/usr as /home should only contain the home directories associated with user accounts.

If you're compiling from source, you can unpack the tarball into your home directory and compile as an ordinary user.  However most well-behaved source packages will install to /usr/local if you run "sudo make install".  That's the [standard location]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for software that's installed outside the repository structure.

---

### Post by Cheesehead on 2011-03-26
You *can* choose where to install applications, if you are an expert. By manually installing everything, or be editing the control files of packages...of course you will break a lot of functionality that way. But if you know how to do that, you also know how to fix that.

There is no easy way to 'move applications' for beginners without severely damaging your system. Don't do it.

A much simpler solution is to resize your partitions using a LiveCD and the gparted package. Hot-shots will tell you that multiple partitions are great...until they run out of space in one. Multiple partitions made sense ten years ago when disk space was much more limited and expensive. The default install of Ubuntu installs everything to a single partition, and most users get along fine that way (and don't run out of space in their system partition anymore)



Your question ('Why is this not possible?') assumes that a line exists between the OS and applications that everyone agrees upon, that separating OS code and application code is desirable, that users will care enough so developers pay attention to such a difference, and that moving applications around is indeed the best solution.

None of those assumptions are true.

Ubuntu uses package management instead of separate directories. It's more flexible than your scheme and has lots of tools to take care of all the bookkeeping for you.

---

