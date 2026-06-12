---
title: "Compiling Source from Ubuntu Offline?"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by lu6cifer on 2008-04-03
So, I installed ubuntu on a computer that has absolutely no internet...

I tried to install a source package on ubuntu just to see if I could--pingus-0-7.2.
I unpackaged it, went into the directory, and got as far as the "./configure" command. When I navigate into the pingus unpackaged folder, and type ./configure, it says, "./configure is not found" 

So, there are files like install and install.sh in there. So I do, "./install.sh" and it says, "Usage ./install.sh DIRECTORY" so I type "./install.sh DIRECTORY" but then it says, "Error: You have to compile pingus before you install it. To compile it, type, scons," but scons isn't installed, and I have to get online to install it.

I also tried cd'ing into the src folder, and tried "./make_docs.sh" but then it said that that file wasn't found. 

I searched, and there aren't any files named "configure" in the pingus folder. There are files that say config.cpp or config.hpp in the src folder, but those just returned error message too.

So, what do I do from here?

By the way, I have Ubuntu 7.10, Gutsy Gibbon. 

And P.S., I'm sorta noobish at Ubuntu, what's the command to go back only one directory in terminal? "cd" takes me back to desktop, but what takes you back just one directory?

---

### Post by zvacet on 2008-04-04
Did you read **install** file? In that file you will find what you have to do to compile package.Do you have build-essential installed?If not download it from [here.](http://packages.ubuntu.com/gutsy/build-essential)Be sure that you download all dependencies (marked with red ball) and install them first.

To go back just one step type** cd ..**

---

