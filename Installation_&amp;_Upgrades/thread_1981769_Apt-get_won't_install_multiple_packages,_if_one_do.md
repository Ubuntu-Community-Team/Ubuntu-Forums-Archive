---
title: "Apt-get won't install multiple packages, if one doesn't exist"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by danwizard208 on 2012-05-17
Goal: Install a list of packages with apt-get via commandline. E.g.
```
sudo apt-get install pack1 pack2 ... packn
```

Problem: If one package doesn't exist, then the entire command fails, even if the rest of the packages exist.

Desired Result: Install all possible packages, ignoring those that don't exist.

Description:
I'm sure some thread to this effect already exists, but a few quick searches don't seem to turn it up, possibly because I don't know how to describe the problem. 
At any rate, what I was trying to do, in my case, was install a list of libraries store in a text file (see attached libs.txt), with one package name per line. The command I attempted to use was
```
xargs -a libs.txt sudo apt-get install
```

The problem is, some of the package names I was given are not actually valid package names, so apt-get can't find them. I don't have access to the output right now (I am in the middle of running an upgrade on the machine with the files, so I can't run apt-get, and I didn't save the output earlier), but basically it was complaining about the packages not existing, and then exiting.

I'm completely fine with apt-get not installing packages which don't exist, obviously, but I would like to install the ones that do exist. There's two workarounds I can think of, one of which I tried and succeeded with:
```

for lib in `xargs -a libs.txt` ; do
    sudo apt get install $lib
done

```
The other is just to delete the bad names from the list (or create a new list with only the good names). These workarounds are fine (although the second would be a pain with a large amount of bad packages) but it seems like there should be an option I can pass to apt-get to tell it to ignore pacakges it can't find. '-m' didn't work.

Any thoughts?

---

### Post by dabl on 2012-05-17
I made a text file named "List of Useful Packages.txt", which I try to keep up to date.  It has probably 3 dozen of my commmonly-used packages that aren't included in my favorite distro by default. The package names are in alphabetical sequence with one space between the file names, so I can copy it from kate and paste it into a terminal immediately following "sudo apt-get update && sudo apt-get install".

When a package is missing, I just hit the up-arrow, then back-arrow to the point where I get to the missing package, and backspace over it, then forward-arrow and "Enter".

Not the world's most elegant solution, I know ... but it works every time.  :lolflag:

---

### Post by danwizard208 on 2012-05-22
Yeah, I eventually made the command work with the workaround listed in the original post. So I know there are various solutions to the problem. But the obvious solution, a command-line argument, isn't present, and this bothers me. :(

Unless I didn't RTFM properly, and it was hidden somewhere in there.

Thanks for the suggestion. :)

---

