---
title: "How can I install software with all dependencies?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by KonfuseKitty on 2011-02-27
I can't find the answer to this one anywhere... I'm using Ubuntu 10.04 and want to install Inkscape 0.48, the latest stable version, which on Launchpad is packaged for Ubuntu 10.10. Is there a way of installing software with all its missing dependencies? I used to do this manually, just by following the warnings, but this time I'm overwhelmed and looking for an automated solution.

---

### Post by mcduck on 2011-02-27
Most likely there's at least one PPA repository that provides updated packages for Inkscape....

edit:
[https://launchpad.net/~ricotz/+archive/ppa]("https://launchpad.net/~ricotz/+archive/ppa")
[https://launchpad.net/~inkscape-nightly/+archive/ppa]("https://launchpad.net/~inkscape-nightly/+archive/ppa")

here's a HowTo, in case you need one:
[http://www.webupd8.org/2010/08/install-inkscape-048-vector-graphics.html]("http://www.webupd8.org/2010/08/install-inkscape-048-vector-graphics.html")

---

### Post by KonfuseKitty on 2011-02-28
Is this the only way of doing it, using a third party PPA? I was hoping to avoid that. Is there really no command that would install missing dependencies of a package?

---

### Post by Arand on 2011-02-28
Using the PPA is probably the easiest method.

If the dependencies you need are available in you current repository you should be able to install the .deb with gdebi, which has automatic dependency retreival.

Otherwise I've heard that you can simply do the dpkg -i (possibly with forcing) And then have apt-get resolve the broken dependencies by doing apt-get -f install, thus pulling in all necessary deps, if they are available in your current repos, of course.

- arand

---

### Post by KonfuseKitty on 2011-02-28
Hmm... I take it then that both the gdebi and the dpkg/apt-get methods depend on my "current repository". This seems to be where the problem lies, because it's with gdebi-gtk, the GUI version of gdebi, that I'd been trying to install latest software packaged for Ubuntu 10.10, such as Inkscape 0.48, and being told with a red warning that dependencies were missing. So am I right in thinking that the whole of Launchpad doesn't equate to my current repository, but only those parts that are targeted at the system I'm running, 10.04? If this is the case, how can I make the whole of Launchpad my current repository?

---

### Post by mcduck on 2011-02-28
> **KonfuseKitty said:**
> Is this the only way of doing it, using a third party PPA? I was hoping to avoid that. Is there really no command that would install missing dependencies of a package?

Any of the package management tools in Ubuntu will do that, if the dependency packages are available in any of the configured repositories. If the dependencies are not available in the repositories you are using, then no. You need to add a source that has the dependency packages. No tool can get you the required packages unless you tell it where to get such packages... ;) Using a PPA repository is the easiest and simplest (And pretty much the best in every other sense as well) way to do that.

---

### Post by Arand on 2011-02-28
Since the new Inkscape is built against newer versions of the build dependencies, it will automatically depend on newer versions of the corresponding utilities, the way you normally get around this is by backporting, i.e. building against the build-deps of the older system.

a) Which is exactly what has been done in the above linked PPA: Use it.

b) Otherwise: Rebuild yourself.

c) (...or try to install the newer versions of the utilities, with the risk of messing up the system due to mismatching versions of utilities, an easy way to do this would be adding the natty repositories, which will likely break your system, just so you know).

- arand

---

### Post by mcduck on 2011-02-28
> **KonfuseKitty said:**
> Hmm... I take it then that both the gdebi and the dpkg/apt-get methods depend on my "current repository". This seems to be where the problem lies, because it's with gdebi-gtk, the GUI version of gdebi, that I'd been trying to install latest software packaged for Ubuntu 10.10, such as Inkscape 0.48, and being told with a red warning that dependencies were missing. So am I right in thinking that the whole of Launchpad doesn't equate to my current repository, but only those parts that are targeted at the system I'm running, 10.04? If this is the case, how can I make the whole of Launchpad my current repository?

*None* of the default software repositories are at Launchpad. :D

As far as I know the only repositories you *would* have at Launchpad are the PPA repositories. And no, there's no way to automatically add every PPA repository to your software sources, not that doing such thing would really work or that you'd ever really want to do such thing.

---

### Post by KonfuseKitty on 2011-02-28
Ah now I think I get it! Still avoiding untrusted PPAs... All I need to do to install software packaged for 10.10 on 10.04 is to add 10.10 repositories, right? How dow I do that? Once I got the software installed, I just remove the 10.10 repos, and all is sweet and just as it would be had I done the installation manually, which is what I used to do without problems.

---

### Post by mcduck on 2011-02-28
> **KonfuseKitty said:**
> Ah now I think I get it! Still avoiding untrusted PPAs... All I need to do to install software packaged for 10.10 on 10.04 is to add 10.10 repositories, right? How dow I do that? Once I got the software installed, I just remove the 10.10 repos, and all is sweet and just as it would be had I done the installation manually, which is what I used to do without problems.

You *definitely* should use a PPA instead, using repository for wrong release version (or other Linux distribution) will most of the time cause lots of problems. On the other hand most of the PPA's are well maintained and definitely can be trusted, and adding a PPA would easily give you exactly the packages you want, packaged for the Ubuntu version you are using, and together with reliable updates in future as well.

(If you are trying to avoid using a PPA because of getting some "untrusted source" warning in the past or something like that, that's usually user error, result from adding a PPA repository but *not adding* it's signing key so the package authenticity can't be checked. Such problems are easily solved by adding the key, or using the *apt-add-repository* command to add the PPA repository in the first place.)

---

### Post by KonfuseKitty on 2011-03-03
OK, if Launchpad says "untrusted PPA" then it's untrusted and I ain't using it.


So I finally found out how to add the 10.10 repository, by guessing it, replacing "lucid" in its name with "maverick". Hey presto, all the latest versions of software, packaged for 10.10 started showing up in Software Center. Neat! The danger or course being that some of my existing software may be broken by new dependencies being installed, but that risk would exist also if I had installed them manually, as I had been doing.


The fact that I now had access to 10.10 repository enabled me to quickly check the missing dependencies for Inkscape 0.48, 36 of them. Mostly lib files, so not too scary, but some updated gtk stuff, which would be more risky. I installed the software, and all is well, except my Software Center doesn't lauch anymore. I know it's based on gtk, so clearly the update broke it. The snag is, I can't seem to find this program on Launchpad to update it, not too surprisingly as it's part of the system. Not that big a deal, as I used it only for research, I prefer to install/remove software with gdebi and apt-get.


There you go, it can be done, with caveats.*:)

---

