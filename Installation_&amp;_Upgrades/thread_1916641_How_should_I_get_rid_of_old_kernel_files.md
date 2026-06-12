---
title: "How should I get rid of old kernel files"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by WasMeHere on 2012-01-28
Hi friends,

> **coffeecat said:**
> Just to add - a side issue, but important:

My guess is that you accidentally deleted a current kernel file. Once you have your new system up and running and if you find yourself in the position of needing to clean out old kernels, it's not a good idea to delete them directly from /boot. There are other kernel files in /lib/modules and /usr/src. Use a package manager to clean out old kernels. That way the grub menu is automatically updated for you. When you need to do this, and if you need help, start a new thread and someone will help you with this.

I usually keep only two kernel versions, and I have been deleting the old files from /boot manually with for example
```
sudo rm *-36-generic
``` keeping versions 37 and 38. So far I have been lucky, but I understand that there are tools for that. Please let us know, *coffeecat*!

---

### Post by oldos2er on 2012-01-28
The answer is in your quote: "Use a package manager to clean out old kernels."

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by JRV on 2012-01-28
There is a system cleaner in ubuntu-tweak that will remove old kernels.
```

#code to install ubuntu-tweak.
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

### Post by Karlchen on 2012-01-28
Hello, Olle Wiklund.

As is often the case: many ways lead to Rome. Here is one of them:

[LIST]
[*]Launch Synaptic Package Manager, e.g. by executing ```
gksu synaptic
``` in a terminal. Enter your password when prompted to do so by gksu.
[*]Inside Synaptic, I always list the software packages by [Status] (All, Installed, Not Installed)
[*]Click on *Installed* software, because we want to remove installed kernel software that is outdated.
[*]Click on the column *Package* in order to sort the installed packages by name, sorting order ascending
[*]_Note:_
The example which I am using is what I actually did only a few days ago on Lucid Lynx after installing kernel 2.6.32-38. In this case kernel 2.6.32-37 will be kept, but 2.6.32-36 will be removed.
[*]Locate and mark the following packages:
+ linux-image-2.6.32-36-generic
+ linux-headers-2.6.32-36
+ linux-headers-2.6.32-36-generic
(The version numbers will vary depending on the kernel versions in question. Be extra careful to mark the right 3 packages only. - No need to tell you, I guess.)
[*]Right-click and select **Select for complete removal**
[*]Left-click on the button [Apply]
[*]**dpkg** will be launched and perform the appropriate steps in order to unconfigure and remove the selected packages.
At the end **update-grub** will be invoked. update-grub will update the list of boot options which will be presented by grub at boot time in order to make it reflect that 2 kernels have been removed.
[*]Once dpkg and update-grub have finished their jobs, you will return to Synaptic. You may simply close it now.
[*]Task accomplished
[/LIST]

I know that the same task can be accomplished more efficiently using the appropriate apt-get commandlines. Yet, I love to use Synaptic: Do not worry about commandline usage and typing errors. :)

HTH,
Karl

---

### Post by mikewhatever on 2012-01-28
The old kernel lines represent installed kernels with headers and possibly other components. Each takes about 200MB of disk space, so the best solution would be to uninstall them, which can be somewhat tedious.

Here is a script that will remove all but the current kernel+headers:
```

#!/bin/bash
# rmkernel.sh
#Based on original command found here:http://ubuntuforums.org/showthread.php?t=1658648

#remove all the unused Linux Kernel headers, images and modules
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

```

---

### Post by Elfy on 2012-01-28
I always use synaptic to do it - mostly so I don't make a mistake I can't afford to with apt-get.

I'd not go to the trouble of installing something else to do so - but that's me ...

---

### Post by WasMeHere on 2012-01-28
Thank you *all* for the answers :KS

Now I have not only a cook-book way to do it, but also some understanding of the tools and what they actually do. I hope it will be useful for several other people too :-)

Olle

---

### Post by Chatoyer on 2012-02-02
Let me thank you as well.

---

### Post by simplr on 2013-02-11
Thank you @mikewhatever - that mighty one-liner freed up 40% of my Aspire One 8Gb drive!

---

### Post by codemaniac on 2013-02-11
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thread closed.

Thanks!

---

