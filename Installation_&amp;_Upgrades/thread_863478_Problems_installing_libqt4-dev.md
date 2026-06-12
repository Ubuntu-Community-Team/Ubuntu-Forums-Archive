---
title: "Problems installing libqt4-dev"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by adelahunty on 2008-07-18
Hello all!

I'm running an Intel box with Hardy Kubuntu on it (8.04.1), and all is going well.  Sort of...

I want to do some coding in QT Ruby, so I have installed the QTRuby4 library (libqt4-ruby), as well as everything it asks for.  I want to install qt4-designer, but this tells me that libqt4-dev is needed, giving me the following error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  qt4-designer: Depends: libqt4-dev but it is not going to be installed


```


Of course, when I try to add libqt4-dev to the end, I get more issues:

```
The following packages have unmet dependencies.
  libqt4-dev: Depends: libglib2.0-dev but it is not going to be installed
              Depends: libpq-dev but it is not going to be installed

```

And this eventually leads us to:

 ```
 libglib2.0-dev: Depends: libglib2.0-0 (= 2.16.3-1) but 2.16.3-1ubuntu3 is to be installed
  libpq-dev: Depends: libpq5 (= 8.3.1-1) but 8.3.3-0ubuntu0.8.04 is to be installed

```

I've updated sources, but nothing doing - it still insists on the above not being installed as it introduces conflicts.  They're pretty minor updates in each case, that doesn't really matter, I know....

Can anyone help me on this one?  How do I fix this situation in order to get the libqt-dev packages installed, and finally get designer on-board?

Any assistance gratefully received!!!

---

### Post by Kevanx on 2008-09-05
It looks as though there is a weird dependency violation surrounding libpq5. It's over my head as to how/why this has happened, but there is a pretty in-depth discussion at this thread:
[http://ubuntuforums.org/showthread.php?t=909953]("http://ubuntuforums.org/showthread.php?t=909953")

Post #12 in that thread suggests that if your system is 100% usable (mine is), then ignore it until the next release (6-8 weeks), but if not, then downgrading libpq5 (to the gutsy "higher" version) might work. I suggest you read the thread.
Hope this helps!

---

