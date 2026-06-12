---
title: "keep track of manually installed packages"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by vinboy on 2007-02-23
hi
i'm wondering if there is a way to keep track of manually installed packages.

For example,
```
sudo apt-get install frozen-bubble
```

then the frozen-bubble package is recorded somewhere (maybe in a text file), discard the dependencies such as frozen-bubble-data package.

thanks in advance :guitar:

---

### Post by Kateikyoushi on 2007-02-23
It is not exactly what you want but you can see in synaptic installed auto removeable and obsolate packages which seems to list most, if not all my hand installed packages.

---

### Post by Yoooder on 2007-02-23
You're right that apt will record all packages installed through it.  Kateikyoushi is correct that synaptic can be used to view them.

Here's a little different take on Kateikyoushi's answer.  Synaptic (a GUI apt frontend) will show all packages available to you through your set repositories/sources.  It will mark packages that you have installed (the checkbox to the left of the package name will be filled in green).

I haven't used Synaptic much, and haven't tried to see *just* the packages I have installed, or installed manually, however I'm sure if you get familiar with it then it should serve your needs.

The one issue is that is sounds like you want to see *only* the packages you've manually installed.  I might be incorrect, but my understanding is that when you do an "apt-get install packageabc" it will add it to the list of installed packages, and not a list of ones that didn't come with Ubuntu, so it may be hard to get the view of things just as you want it.

---

### Post by vinboy on 2007-02-23
thanks guys.

what about this, write a script such as:

aptins kubuntu-desktop
the aptins record the {argument} into a file and invoke apt-get install {argument}

aptrem kubuntu-desktop
the aptins remove the {argument} from a file and invoke apt-get remove {argument}

does anyone know much about scripting?

---

### Post by Yoooder on 2007-03-06
Here's a page that deals with cleaning up packages from Ubuntu, I noticed the "Installed (local or obsolete)" status in the listings, and it made me think that it *may* help you out.  The Status view of packages is something I haven't worked with before, and might just be the answer your question

> [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

