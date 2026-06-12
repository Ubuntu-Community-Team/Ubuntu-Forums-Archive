---
title: "How to find Package Dependencies while compiling?"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by pedja_portugalac on 2009-11-29
Hi there

I am building some packages from source and I can't find what it depends on. I have installed them with apt-get build-dep command but I have to know now what was installed to put it in my package information. Using command: sudo apt-get build-dep -V x264 I get just
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
How can I find what are those 8 not upgraded packages as they are dependencies I have to put in my new .deb binary file?

Anyone? ;)

---

### Post by lykwydchykyn on 2009-11-29
The upgrades have nothing to do with your build dependencies.  Anytime apt is run, it reports the total numbers of packages installed/removed/upgraded/not-being-upgraded. 

You basically have 8 updates that need to be installed, so run 
```

sudo apt-get upgrade

```
And they should install.

They don't have anything to do with your build dependencies.  If no packages were installed as a result of that command, it means either the dependencies are already installed, or apt couldn't determine any to install.

Have you tried running ./configure on the source to see if it will configure?  If it configures successfully, you should have all the build dependencies.

---

### Post by pedja_portugalac on 2009-11-29
> **lykwydchykyn said:**
> They don't have anything to do with your build dependencies.  If no packages were installed as a result of that command, it means either the dependencies are already installed, or apt couldn't determine any to install.

Have you tried running ./configure on the source to see if it will configure?  If it configures successfully, you should have all the build dependencies.

You are right. Those 8 packages have nothing to do with my dependencies, I find it with command: sudo apt-get upgrade --simulate. Thank you for that explanation.
I have all dependencies installed on my PC but I would like to put their description in binary file for the future installs. For example, on the fresh install of ubuntu I want to install mplayer without all -dev files. My binary creation will download all the -libs mplayer depends on and that's all. But I forgot to note all this files while apt was building deps. Now I am wondering if there is a command to list files it depends on. apt-get build-dep show them only first time and ask you for the confirmation but later it just say nothing to be updated or installed. Do you understand what I mean? ;)

---

### Post by jpaugh64 on 2009-11-29
I don't know yet how to check the dependencies of a package from the command-line (Surely there must be a way, yes?), but I do know that you can access that information from within Synaptic. Just run 'sudo synaptic' and search for the package; then, right click on it, and open it's properties. There is a 'Dependencies' tab that lists the dependencies. If you really want to, you can just search through the contents of the .deb file itself, which is simply an archive.

---

### Post by pedja_portugalac on 2009-12-01
> **jpaugh64 said:**
> I don't know yet how to check the dependencies of a package from the command-line (Surely there must be a way, yes?), but I do know that you can access that information from within Synaptic. Just run 'sudo synaptic' and search for the package; then, right click on it, and open it's properties. There is a 'Dependencies' tab that lists the dependencies. If you really want to, you can just search through the contents of the .deb file itself, which is simply an archive.
Yeah, it could be found there in synaptic. Thank you.

---

