---
title: "Installing .net framework 3.5 on ubuntu10.04 lts"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by 12averma on 2010-07-17
Hello there,
i am using ubuntu10.04 lts and i want to run .net framework 3.5 on  this operating system ...........so please help me........

---

### Post by pythonscript on 2010-07-17
I doubt that will work. the .NET framework is very strongly designed to be Windows only, and I don't think a version that recent will even run through Wine. There is the Mono project (available in the ubuntu repositories) that can provide compatibility for *some* windows applications that require the .NET framework, but not a version that recent. 

What specific application are you trying to run? I presume you're not JUST trying to run the .NET framework, since that's a dependency for applications (mostly) not so much an application in and of itself.

---

### Post by anglican on 2010-07-19
> **12averma said:**
> Hello there,
i am using ubuntu10.04 lts and i want to run .net framework 3.5 on  this operating system ...........so please help me........
Mono gives almost complete 3.5 support:
> The easiest way to describe what Mono currently supports is:
**Everything in .NET 3.5 except WPF and WF, limited WCF.**
See:

[http://mono-project.com/Compatibility](http://mono-project.com/Compatibility)

That's for mono 2.6. Users of Ubuntu 10.04 LTS (Lucid Lynx) can install **2.6.3** by  using Synaptic from the [badgerports]("http://badgerports.org/") (*[http://badgerports.org](http://badgerports.org)*)  repository. badgerports is an unofficial community project from one of  the Debian/Ubuntu Mono developers to ship latest Ubuntu packages for  Ubuntu LTS users.

H

---

