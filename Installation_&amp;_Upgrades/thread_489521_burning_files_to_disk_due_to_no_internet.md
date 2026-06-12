---
title: "burning files to disk due to no internet"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2007-07-01
Hi
Can the files needed for adding programs to ubuntu FF be burned to a disk and then loaded into synaptic ?
my kids pc is not online, but i would like to add programs such as crystalspace and others.

thanks

---

### Post by Levander on 2007-07-01
Yeah, this is done often when people want to install an application from a repository, but they don't want to include the repository itself in the /etc/apt/sources.list file.

If you have another machine that is on the internet, search for the package.  I don't use synaptic, so can't tell you.  But, you need to find the URL of the file that contains the package your looking for.  You can download that one file.

You also have the problem of dependencies.  Like if Ubuntu has to install other packages that your desired package depends on.  Again, I don't use synaptic, but on the command line, with aptitude, you can "sudo aptitude install --simulate <package name>" to simulate the install of a package on the computer that is on the internet.  That simulation will tell you in the output what other files need be downloaded and installed to be able to install your desired package.

It's kind of a vague guess that if you're other machine already has all the dependencies, your son's machine will too.

If there are some unmet dependencies, you just have to manually download those also and carry them to your son's computer.

There may be a better way of checking dependencies that I can't think of right now though.  What you need to do on your son's machine is synaptic's equivalent of a "sudo aptitude update" to just get the list of what all packages are out there.  But, since he's not on the internet, I don't know how to accomplish that.

---

### Post by kystorms on 2007-07-02
thank you so much for the help, its great to know that it can be done!

:-)

---

### Post by Levander on 2007-07-02
Oh yeah, when you have got the .deb files over to your son's PC, you use the dpkg command to install them.

I think the command is like: "dpkg -i <file name>"

---

