---
title: "Content of Ubuntu 22.04 LTS installation"
date: 2023-06-30
forum: Installation &amp; Upgrades
---

### Post by rdnublx on 2023-06-30
How do I verify that all content required to be in the 22.04 LTS distribution is actually installed? Command lsb_release -a returns description Ubuntu 22.04 LTS. Is there a way or command to verify the actually installed content against the list of what is expected or supposed to be there?

---

### Post by QIII on 2023-06-30
There is a difference between what *should* be there and what *could* be there.

By the very nature of the installer, if your system is running, all that *should* be there is there.  That is to say that the basic OS with the default packages are installed.

Is everything that *could* be there installed already?  ***Not by a long shot***.  I can't see any case where you would ever want everything that *could* be there.  There may be any number of packages that you might like to add, but they aren't *required* and most were not installed.   There are hundreds or thousands of packages available to install from the repositories.  Just add what you think you might use.

---

### Post by TheFu on 2023-06-30
> **rdnublx said:**
> How do I verify that all content required to be in the 22.04 LTS distribution is actually installed? Command lsb_release -a returns description Ubuntu 22.04 LTS. Is there a way or command to verify the actually installed content against the list of what is expected or supposed to be there?

Different people have a different idea for what should be installed. There's no single "right" answer, since we all have different needs.  

While you could install "everything", the chances that you'd use it would be tiny.  Most people use only 10% of the installed software, if even that much.  For this reason, I much prefer to have the lightest install possible and add what I need, when I realize it isn't there already.  That's the magic of Linux repos and package managers.  Package management was a key reason why I choose to run Linux instead of other OSes.

[https://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop](https://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop)

If you never use a program, why have it installed at all?  When you need it, install it. That usually takes 5 seconds for most end-user applications.  Installing and configuring some server software can be from 30 seconds to multiple days of effort, just depends.  

I'm trying to setup a software-defined VPN network to connect about 10 different applications spread all around the internet.  The learning curve for me on this is steep, but the promise for what it can do and how it will allow friend and family access to easy, specific, network services is why I'm doing it.  Basically, for $60/yr, I can provide cloudy services to my extended family so they get the privacy they deserve for no cost.

---

### Post by rdnublx on 2023-06-30
Thank you both! Not sure what symbol to use to address a user here directly, have not used Ubuntu forum for a while.
Anyway, totally understand the logic of &#8220;install as needed&#8221;, will do. My question was particularly driven by the fact that there was no browser included with my newly installed 22.04 LTS. It is T2 Mac modified distribution, which works fantastically so far. There was some notion that it was possibly minimized for the purpose of size, hence my question. I believe I am good now, just going to take it package by package as needed, starting with browsers. I am thinking about installing Brave rather than a major one, always meant to try it, never did.
Again, thank you, appreciate your help!

---

### Post by TheFu on 2023-06-30
A few years ago, I complained to the packaging team that a browser was being included in a minimal install. 

That complaint was rebuffed, though they did remove a few other large programs in my list of unneeded programs for a minimal install.  I suggested that rather than a huge, bloated, browser, that a small, tight, minimal browser be included instead.  That failed, I suspect because the small, minimal browsers don't support javascript and Canonical's websites all require JS to work.  In general, I disable JS for most websites and do without. Websites that don't work at all with out it, I don't use.

I suspect the lack of a browser may have more to do with the platform not having a snap package for the release alpha yet than their final intentions for October.

---

### Post by rdnublx on 2023-07-01
Ok, understood, thank you. The other day, I looked at FF installation instructions, one of them was snap package approach. I was not sure whether it was the preferable way to using apt? I am not clear on that, anyway I will figure it out. Thank you

---

### Post by TheFu on 2023-07-01
> **rdnublx said:**
> Ok, understood, thank you. The other day, I looked at FF installation instructions, one of them was snap package approach. I was not sure whether it was the preferable way to using apt? I am not clear on that, anyway I will figure it out. Thank you

To snap or not to snap, that is the question.

Canonical clearly wants people to snap. No question. They've made a few programs only available via snap in their ecosystem.  Chromium and Firefox browsers are in that list.

There's a huge group of ubuntu and former ubuntu users who dislike the snap packages for a number of reasons. There are many threads here about it.  For most programs, there are alternatives.  For example, I installed Firefox ESR from the mozilla PPA and don't use the snap package version.  Additionally, I moved my main desktop from ubuntu to Linux Mint to avoid snaps altogether.  However, until a few weeks ago, the only way to get Canonical's excellent LXD/LXC container management software was to use the lxd snap package, so on my servers where I want to use linux containers and lxd, there was little choice but to allow the snap package subsystem.  FYI, lxd is comparable to "docker", which you've probably heard about, even if you don't know anything else.  LXD is miles better than Docker in many ways. It just isn't as popular.  Fortunately, the new Debian 12 release includes a stable version of lxd without using a snap package, so there's an alternative.

Whether you find snaps useful or not depends on many things. On many of my systems where I use centralized user management, snap packages don't work at all. It is a design flaw that the snap team refuses to address.  For many workflows, snap package constraints get in the way, preventing anything from working.  Don't forget the bloat of the packages and lack of local control over the constraints.  For my needs, flatpaks are a better choice and Redhat only uses flatpaks for end-user programs, not for server stuff. This is very different than Canonical's intent with snaps.

Anyway, you can read the threads here on snaps to see the pros and cons.  Usually the pros are "it works for me", but not much else. That isn't really fair, since snaps bring constraints to prevent programs from accessing parts of the OS that the snap-program shouldn't need access to 99% of the time, unless your HOME isn't under /home/.  The list of cons is long. #1 is the lack of local control over the constraints.

---

### Post by rdnublx on 2023-07-02
Thank you, it takes time and energy to write up this kind of  perspective, I do appreciate it! I'll have to read on snap technology,  not familiar with it, your insights are helpful for stepping into it.  Docker and Docker management are of particular interest to me. Thank you  for the details and suggestions on that as well.

---

### Post by TheFu on 2023-07-02
> **rdnublx said:**
> Thank you, it takes time and energy to write up this kind of  perspective, I do appreciate it! I'll have to read on snap technology,  not familiar with it, your insights are helpful for stepping into it.  Docker and Docker management are of particular interest to me. Thank you  for the details and suggestions on that as well.

The main problem I have with docker is that the containers run as root by default. That sorta defeats the purpose for using Linux Containers and is a huge reason why all the other container management tools are better, objectively.  Docker has a way to not run their containers as root, but almost nobody seems to use it. We've known for 30 yrs that running processes as root is dangerous.  Apache hasn't done it for a long time, yet almost every docker container retains that flaw.  Crazy, right?  Docker needs to fix that and make the default to run as non-root (called _unprivileged containers_). They've been capable of this for a long time, but they decided, it was a management choice, not a technical choice, that it was too hard.

Other, similar, management choices have destroyed some programs.  Remember Flash and Shockwave?  Adobe could have migrated those to more secure solutions, but decided not. This harmed an entire industry.

---

### Post by rdnublx on 2023-07-02
Can't comment on your Docker point at this point, but certainly will keep it in mind. I am planning to use Kubernetes for docker management. Thank you.

---

### Post by vidtek on 2023-07-03
Regarding snaps- when I do an install the very first thing I install is a .deb package of Firefox or Opera, then the next thing to do is to remove the complete snap ecosystem.

The snap system limits my productivity, doesn't allow multiple users to use an application without jumping through multiple hoops - it just takes way too much time to administer it.

Just my 2 penneth worth.

Cheers Tony.

---

### Post by rdnublx on 2023-07-03
Thank you, Tony. This is definitely worth each of the 2 pennies :-) I  have not experienced the pain yet, but I am starting to feel it on the  back of my head. I am sure I will thank you for the advice when I get  there.

---

### Post by vidtek on 2023-07-04
No worries, just ensure you install a browser of some sort (via apt or .deb) **BEFORE** you remove the snap ecosystem!

---

