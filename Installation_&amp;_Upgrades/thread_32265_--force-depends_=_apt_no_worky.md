---
title: "--force-depends = apt no worky"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by donkey on 2005-05-06
I just installed Enlightenment DR17 and had to use "dpkg -i --force-depends" to get some libraries to install ( because they said they needed the debian version of a package rather than an ubuntu one).  Anyways, now that I get this stuff whenever I try to "apt-get install," I can't install anything:

The following packages have unmet dependencies:
  emotion0-test: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
(and so on and so on)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

"apt-get -f install" of course removes all the libraries.  So my questions is, how do I tell apt not to worry and just proceed as normal?

btw, enlightenment is **sweet**  [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG]

---

### Post by az on 2005-05-06
You remove the offending package.

You should not mix repositories, nor should you use force-depends.

That is all.


Compile it from source by installing the source packages from Wherever you got the binary (Sid?)  
apt-get build-deb XXX
apt-get -b source XXX

Then you will have a package that will not bork your system.

---

### Post by donkey on 2005-05-06
Well, the source of the problem is that the libraries require libc6_2.3.2.ds1-21_i386.deb (debian) to install and ubuntu uses libc6_2.3.2.ds1-20ubuntu13.deb

The libs would work fine (at least for my uses) with the ubuntu one.  Is there any way around this?

---

### Post by az on 2005-05-06
No.

Dependancies work one way.  An app build in c last year uses function calls that were  made last year.  When I make an app this year, I can make my c stuff compatible with last year's stuff, but last year's stuff does not know about the changes that were made this year.  If last year's app runs into something it does not know about in the newer version of the c libraries, your system will crash.

You need to install a greater or equal version of libc6 that your app (DR 17) is compiled with.  Since there is none in Hoary, you have no choice but to dump everything, or just the incompatible app.

That's the way it is.  

So, you asked " Is there any way around this?"  Compile  DR 17 with the libc6 you are using in Hoary.

---

### Post by rwabel on 2005-05-08
have a look here to get around the libc6 problem
[http://ubuntuforums.org/showthread.php?t=548&page=3](http://ubuntuforums.org/showthread.php?t=548&page=3)

it worked for me too and haven't had any problems. I know it's not the best solution to do that. I guess the differences are so minor that it's safe to do that. But no guarantee from my side

---

