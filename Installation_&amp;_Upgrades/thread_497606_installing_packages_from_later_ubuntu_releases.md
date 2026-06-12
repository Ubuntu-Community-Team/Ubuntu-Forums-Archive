---
title: "installing packages from later ubuntu releases"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by noamt on 2007-07-10
Hi,

I have the latest LTS version of Ubuntu (actually Xubuntu) installed - 6.06. 

For some of the packages, I'm interested in a later version than the one available through Synaptic. In my example: I want the latest version of Subversion. The latest found via Synaptic is version 1.3.1, but for Ubuntu 7.04 version 1.4.3 is available.

Can I install the package from the newer Ubuntu release? If so, how?

Is there an alternative method for getting the latest version of some software, other than building from source (which is just too complicated for SVN)?

Noam.

---

### Post by moore.bryan on 2007-07-10
*if you try and install the latest versions meant for another release, there will/may be dependecy issues.  for example, subversion 1.4.3 may depend on more advanced libraries than available to dapper users.  in order to install it, you would have to make sure all of it's dependencies are met before installation.  even if you built from scratch, it would probably error out because one of the many dependencies was not the minimum version asked.  with that said, it's not impossible to do... many would just argue against it.  they would suggest you upgrade your distribution to feisty and then install.*

---

### Post by noamt on 2007-07-10
So basically what you're saying is, I'm stuck with old versions of software, unless I'm willing to upgrade to the latest version of the OS. This is kind of lame.

With Windows, I can run XP or even 2000, and I can still install whatever version of SVN that I like (always the latest) - without having to upgrade to Vista (thanks God for that). 

Why can't it happen in Linux?

Noam.

---

### Post by moore.bryan on 2007-07-10
[I]not exactly.  the release of ubuntu has certain libraries, packages, etc. already installed to work with different programs.  when you go "cutting edge" on a program, the libraries, packages, etc. it might require are more advanced than the release you're using.  there are a lot of things that go on behind the scenes, so to make everything function properly, sometimes we've got to bite the bullet.  but, like i wrote before, you can install the newer packages, just don't be frustrated by having to also install any new dependencies it requires.
i think because linux is so varied, this is the best way to keep things on the same page. 
[/I]

---

### Post by moore.bryan on 2007-07-10
*as an example, if you were trying to install one of the latest stable subversions and you traveled [here]("http://packages.debian.org/stable/devel/subversion"), you could get the .deb, but see the dependencies?  they may be more recent versions than in ubuntu as-is, so you'd have to update them and any dependencies on the dependencies...*

---

### Post by noamt on 2007-07-10
I understand the problem, believe me. What I don't understand is why it should be so hard to satisfy all dependencies. If SVN needs APR that needs LIBC6 that needs whatever, just install everything. 

In Windows, the SVN installation package is probably bigger than the .deb file - but it contains all the DLLs it needs. As an Open Source / Linux enthusiast, I find this behavior hard to defend. I hate it when Windows it better than Linux at something!

---

### Post by pistcivet on 2007-07-10
The fact that Microsoft bends over backwards to keep programs from previous
versions of Windows compatible, doesn't mean other operating systems have to (or should).
In fact, its the main reason Windows is such a buggy/insecure mess.

If MS is ever going to release a secure OS, they will have to drop legacy support
for older software.

The fact that Linux (and even Apple) don't follow Microsoft's example is a (very) good thing.

Disagree?

---

### Post by moore.bryan on 2007-07-10
> **noamt said:**
> What I don't understand is why it should be so hard to satisfy all dependencies. If SVN needs APR that needs LIBC6 that needs whatever, just install everything.
*it's more the versions of the dependencies...*
> In Windows, the SVN installation package is probably bigger than the .deb file - but it contains all the DLLs it needs. As an Open Source / Linux enthusiast, I find this behavior hard to defend. I hate it when Windows it better than Linux at something!
*the svn deb in the repos does... you want something which isn't in the repos and that's the catch.*

---

