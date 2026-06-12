---
title: "Automate installing a standard set of packages?"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by bgracian on 2010-05-12
My upgrade route with Ubuntu is to do a complete fresh install - then reacquire all my favorite applications and packages using a combination of Add/Remove and Synaptic. 

This is a time-consuming process, and I generally forget several packages the first time through.

Is it possible to automate the packages (and/or applications) installation so that I get everything rebuilt for the new os in a single pass?

Thanks,
b

---

### Post by BoneKracker on 2010-05-12
That should be a relatively simple scripting exercise.  One way would be something along these lines:
```
#!/bin/bash

apt-get install <<END
package1
package2
package3
END
```(Replace "package1, package2, package3, ..." with the packages you want to install.)


Or, you could just list the packages in a text file (say, for example, "pkglist.txt" -- one package name per line), and do something like:
```
while read package; do
    apt-get install $package
done < pkglist.txt
```

---

### Post by bgracian on 2010-05-12
Your suggestions are the type of elegant solution I was looking for. And I just realized that while a list of existing packages can be generated using dpkg-query, some packages include a version number in the name. 

If the dpkg-query method is used to make the list, would using that list force the installation of some older-version packages on the new os? Thereby causing conflicts or instability - or would apt-get be mindful and install the os-appropriate package?

---

### Post by BoneKracker on 2010-05-12
I don't know for sure (I haven't used Ubuntu or Debian for years).  Generally speaking, I would say yes, it could possibly cause a problem.

I would probably avoid using version numbers in the list.  If you want to generate a list using dpkg-query, it should be trivial to strip the version numbers using any number of means.  You basically just want to tell it delete everything beginning with "blah" (probably the first dash, if I remember Ubuntu's naming scheme, but you will want to think that through -- it might be something more complex like "delete everything beginning with the first dash that's followed by an uninterrupted string containing one or more digits but no slashes). :P

For example, if it's simple, you could just pipe the output of your query through a BASH "parameter expansion" expression (string parsing):
[http://ask.metafilter.com/80862/how-split-a-string-in-bash](http://ask.metafilter.com/80862/how-split-a-string-in-bash)
A more thorough explanation is in the BASH man page under the heading "PARAMETER EXPANSION".

Or, you could redirect the query to a text file, and then process the text file using a sed command:
[http://www.faqs.org/docs/abs/HTML/sedawk.html](http://www.faqs.org/docs/abs/HTML/sedawk.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

If you haven't done either before, it's probably easier to figure out BASH parameter expansion.  If it's something "more complex" like I said above, you'll probably want to use sed so you can use a Regular Expressions to define the part that should be deleted.  If you haven't used Regular Expressions before, the man page for grep gives a good run-down on them, or you can google for a tutorial.

If you're doing some of this for the first time, it might seem like a pain, but these are powerful tools you will probably find useful many times in the future.

Also, you really probably don't want to have such a script issue a command to install each and every package on your current system.  It would probably be better to just have it install the packages that have no dependencies.

In other words, 80% or more of the packages are not things that you selected for installation; they are things that were automatically installed by apt because they were needed.  Exactly what is needed by a given package sometimes changes (like when a new version comes out).

So if you run a script manually installing everything that was once on your computer, you're probably going to install unnecessary things.

So I suggest you look at the query functions of the package manager (dpkg, apt, or whatever), and see if there's a way to determine which packages on your system have absolutely zero other packages depending on them.  These would be the items you want to include in your script -- the rest will be installed automatically at the appropriate time.

---

### Post by bgracian on 2010-05-12
Wow! Thanks. Your references for the text-editing scripts are great and will require some study.

Your point about not blindly forging ahead is well taken. I certainly don't have the background to resolve dependencies manually and will happily leave that to the experts.

The best route seems to be to make a reminder list of my "must have" aps and packages, use that to guide my selection of packages in Synaptic, and let Synaptic do the heavy lifting of dependencies and versions.

I had assumed this would be such a common situation that a method for replicating the software constellation from one version of Ubuntu to the next would be readily available. 

Thank you so much for your well thought out responses and suggestions. I appreciate that someone with your expertise would take the time to help me with this "simple idea" that turned out to be so complicated. :) 

b

---

### Post by oldfred on 2010-05-12
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

When I copied my system to my portable I tried to do as much from the command line as possible:
  431  dpkg --set-selections < ubuntu-filesport2010Mar
  432  sudo dpkg --set-selections < ubuntu-filesport2010Mar
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgrade
  437  history
 
I then listed history and now have converted it to a bash file, so when I do a new install I can just run the bash file. (some of commands above)

---

### Post by BoneKracker on 2010-05-12
Personally, I wouldn't do it that way, for the reasons mentioned above (but to each his own).  Actually, that method would be okay for duplicating a healthy system, but would be less desirable as a means to re-create a borked system (which I believe is your requirement).

If you do use that method, make sure to minimize the age of your captured selections list (generate it at the end of every package management session so it's always up to date).

I'll bet there's a way to use your package management system to generate a simple list of top-level packages only (those upon which nothing depends).  Installing from such a list, without version numbers, would be the ideal way to go (in my opinion).  This should enable use of a simple script, as I demonstrated above.

The distro I use generates such a list automatically.  I include it in my hourly snapshots and backup rotation.  It's about 10% the size of the list of all packages.  I have used it to "rebuild" or "migrate" systems on numerous occasions.

---

### Post by oldfred on 2010-05-12
the dpkg selection does create a huge list and I have tried looking for a top level list only. there must be one somewhere as that is mostly what the Ubuntu Software Center is. I tried looking at the python code it is based on but could not tell how it works.

BoneKracker, how does your distro list top level only packages?

---

### Post by BoneKracker on 2010-05-12
I use Gentoo.  When you issue a command to install ("emerge") a package, the name is added to a text file (/var/lib/portage/world).

When the package manager automatically installs a package because it is needed (a dependency of something else you installed), it does not get added to this list. The list includes only packages you have chosen.

There is a separate clean-up command that will uninstall everything on the system that's not either in the list or a dependency of something in the list.  I'm sure apt must go through the same sort of routine after you uninstall something (cleans off un-needed dependencies).

So apt is probably keeping track of what you selected yourself (versus what it selected because it's a dependency).  If you can locate and copy that first, smaller list, that's what you want.

If not, there must be a way to query to see what dependencies a given package has.  Given that, you can identify those packages having no dependencies.  Those packages would comprise your list of stuff to install (although you'd probably not want it to include the packages comprising the base system, but they are likely under separate management by the system, as they are in Gentoo).

This list can be surprisingly small.  Here's the whole list for my firewall/router machine (41 packages -- my desktop has 72).

But, if there is no easy way to just copy a file or query the package management system to construct such a list, then the alternative which has been suggested would be fine, provided the list is current.  I don't know enough about Debian to advise how to do so.

---

### Post by bgracian on 2010-05-13
Thanks to both BoneKraker and oldfred! 

Having now read every post/thread that you have suggested here, I may have learned some things.

Packages can be restored a couple of ways when doing a complete reinstall of the same os (e. g., 9.04 to 9.04). Use:

1) Synaptic's "Save Markings" and "Read Markings" system to restore the packages, OR

2) dpkg --get-selections    and    dpkg --set-selections 

Interestingly, "Save Markings" yields a total of 1663 installed packages, while "dpkg --get-selections" shows 1671 on my machine.

At present I'm running Ubuntu 9.04 and getting ready to do a fresh/clean install of 10.04 LTS, probably to a new hard drive. I had hoped to automate package installation to 10.04 LTS using a list of packages currently used with 9.04. My concern is that either option 1) or 2) might install wrong versions of packages and make the new system crazy.

If Ubuntu maintains a top level list (i. e., user-installed packages) similar to that in Gentoo, it seems that would solve the problem. Does anyone know of such a list in Ubuntu?

---

### Post by oldfred on 2010-05-13
The dpkg list does not include versions so it will reinstall the current version. But I had several older versions of python in my old system and it reinstalled python 2.5 which I did not want or need, so some programs are top level even with versions.

If you run this you will also see the versions you currently have.
List with explanations of programs
dpkg -l > ~/Desktop/installed_programs.txt

Inside my list was this:
```
ii  python                                2.6.4-0ubuntu1                             An interactive high-level object-oriented language (def

ii  python2.5                             2.5.4-1ubuntu6.1                           An interactive high-level object-oriented language (ver
ii  python2.5-minimal                     2.5.4-1ubuntu6.1                           A minimal subset of the Python language (version 2.5)
ii  python2.6                             2.6.4-0ubuntu3                             An interactive high-level object-oriented language (ver
ii  python2.6-dev                         2.6.4-0ubuntu3                             Header files and a static library for Python (v2.6)
ii  python2.6-minimal                     2.6.4-0ubuntu3                             A minimal subset of the Python language (version 2.6)
```

I do not know why the python and pyton 2.6 have different versions of 2.6?

---

### Post by oldfred on 2010-05-13
A little research and I found this, which looks more like a top level list:

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

I think it lists everything not installed by default so when Ubuntu removes a program like gimp will it be not reinstalled?

I also run a script to install somethings, which may be redundant, part of it I got from someone here but I do not know who to credit, the rest I added as my own way of configuring my system:

---

### Post by BoneKracker on 2010-05-13
[QUOTE=oldfred]aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'[/QUOTE]

That sounds like you're on the right track.

---

### Post by bgracian on 2010-05-14
Following oldfred's research recommendations I ran:
```
 aptitude search '~i!~M' 
```
result: a list of 1300 packages.

Then followed up with the command that both oldfred and BoneKracker recommended:
```
 aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)' 
```
which gave 251 packages. Some of them appear to be dependencies that Synaptic included when I selected various packages manually. 

Thanks oldfred for your "newinstall" script. It is impressive. I haven't done any Linux scripting and probably will never try anything that complicated. But with the pared-down list of packages, can I use BoneKracker's script to establish my chosen software constellation on Ubuntu 10.04?
```
 #!/bin/bash

apt-get install <<END
package1
package2
package3
END 
```
If the package list includes something that is already installed, will apt-get simply skip over that entry?

Another option occurred to me. It isn't as elegant as the coding that you two use, more of a training-wheels approach.
The output from the second "aptitude" command (above) looks like this:
> 
no_dependents celestia-common-nonfree
no_dependents celestia-gnome
no_dependents clamav-docs
no_dependents clamtk
no_dependents command-not-found
no_dependents compiz
no_dependents compizconfig-settings-manager
no_dependents computer-janitor-gtk
no_dependents conky


Which, with two "find-replace all" calls in gedit, becomes this:
> 
celestia-common-nonfree	install
celestia-gnome	install
clamav-docs	install
clamtk	install
command-not-found	install
compiz	install
compizconfig-settings-manager	install
computer-janitor-gtk	install
conky	install

Synaptic's "Read Markings" utility should be able to use this to install everything (I haven't actually tried this part yet). 

Thanks to you both for all your help.

---

### Post by BoneKracker on 2010-05-14
> **bgracian]can I use BoneKracker's script to establish my chosen software constellation on Ubuntu 10.04?
```
 #!/bin/bash

apt-get install <<END
package1
package2
package3
END 
```[/QUOTE]

It occurs to me that this technique will only work (I think) if the "apt-get install" command will accept the package name on stdin.  In other words, if this will work

echo "package1" | apt-get install

Then that technique will work.  If not, then you should probably do the other thing I suggested, which is to put the package names in a file and then read them using a loop.  I.e., this way:
```
while read package said:**
> If the package list includes something that is already installed, will apt-get simply skip over that entry?
Good question.  The Ubuntu/Debian experts will have to answer.  Some package managers will reinstall by default, some will not reinstall by default.  If it reinstalls by default, there should be an option not to reinstall if the package is already installed.

I tried to give some general guidance which I hope was helpful (i.e. using a script and trying to work with a top-level list of the packages having no dependencies).  I'll let the guys that know the Ubuntu package management system advise you from here.  Have fun.

---

### Post by bgracian on 2010-05-16
BoneKracker, you have been extremely helpful, and I have enough to go forward with. Thank you!

---

