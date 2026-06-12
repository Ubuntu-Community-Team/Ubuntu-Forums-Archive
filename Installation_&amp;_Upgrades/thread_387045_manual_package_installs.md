---
title: "manual package installs?"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by rayj00 on 2007-03-17
I attempted to install a package manually (Yersinia).
Subsequently, i found out Ubuntu could do this automatically.
Apparently I screwed somthing up during my attempt and had
to re-install ubuntu.. no big deal.

My question is: There are a few packages that do not have the most
current version, for example Nessus.

How would one go about using ubuntu to install any newer software
using Synaptic or apt-get??

Thanks,

Ray

---

### Post by solar george on 2007-03-17
If you can get a .deb then you can use the gui to add it, just double click on it in your filemanager. It is generally best to stick to the software from the ubuntu repositories though.

---

### Post by phossal on 2007-03-17
> **solar george said:**
> If you can get a .deb then you can use the gui to add it, just double click on it in your filemanager. **It is generally best to stick to the software from the ubuntu repositories though**.

Why?

---

### Post by rocknrolf77 on 2007-03-17
At least you got a lot of newer packages at [www.getdeb.net](www.getdeb.net) made for different ubuntu releases. If you use dapper some times you want some newer packages. You can also get packages not in the repos. Like the newer games and things like that. :)

---

### Post by solar george on 2007-03-18
> 
Quote:
Originally Posted by solar george View Post
If you can get a .deb then you can use the gui to add it, just double click on it in your filemanager. It is generally best to stick to the software from the ubuntu repositories though.
Why?

I wasn't very clear there, what I should have said is stick to packages for ubuntu, not just any old .deb.

---

### Post by kidders on 2007-03-18
> **solar george said:**
> stick to packages for ubuntu, not just any old .deb.

That's true. Depending on the specific repository, packages provided by/for Ubuntu are known to work (to at least some degree), and are relatively unlikely to screw up your system. In general, users of distros like Ubuntu are more interested in keeping their systems as stable as possible, than at the bleeding edge of software development.

If you're the sort of person that likes to be running all the latest software within days/hours of release, Ubuntu is not the right distro for you. Something like Gentoo might be worth a look, but the disadvantage of such distros is that they are not built for inexperienced users.

On the other hand, the newest version of Yersinia may have a feature you really, really want, and aren't prepared to wait for. Given the caveat that you could theoretically botch up your system by doing so, you *could* download and compile the source code, roll your own .deb, and see what happens. If you're a confident Linux user, doing this with _one or two_ apps would probably be fine, since you wouldn't care too much about the following:

[LIST]
[*]Installing apps that haven't been vetted by (or tweaked for) Ubuntu can introduce instabilities in your system that can be hard to pin down, or make assumptions about system configuration that are incompatible with Ubuntu.
[*]Doing so tends to make people more reluctant to help you, should you encounter problems in the future ... even if they're unrelated.
[*]By failing to anticipate the presence of unexpected software on your system, installing Ubuntu system updates could have odd side-effects.
[*]Apps you install this way may need to be tweaked in order to work as expected. As a simple example, you'd need to be able to anticipate problems arising from things Ubuntu does differently than other common Linux distributions.
[/LIST]

**One additional comment:**
It may be the case that the latest versions of certain applications are being kept out of Ubuntu's repositories on purpose, because they are _known_ to cause problems.

Sorry for rambling ... I hope some of that is helpful!

---

### Post by rayj00 on 2007-03-18
I understand what you are saying.

But some packages that I need are a few versions behind.
Like nessus and Nmap. There are .deb packages available for
nessus, but only .RPM for nmap.

Do you see potential problems if I install these?

Thanks,

Ray

---

### Post by kidders on 2007-03-19
> **rayj00 said:**
> Do you see potential problems if I install these?

The only thing I could put my finger on off the top of my head that might be concerning about these two applications, is that they both tend to do a lot of work as root. If they contain bugs, you would encounter (potentially serious) problems.

If you're happy to think of your PC as a testing box (ie you're not running any mission-critical or otherwise important things on it), then you can try if you'd like to. The result *may* be completely drama-free, and work flawlessly.

As I'm sure you will appreciate though, posters to this forum will always be very reluctant to *recommend* installing untested software.

---

