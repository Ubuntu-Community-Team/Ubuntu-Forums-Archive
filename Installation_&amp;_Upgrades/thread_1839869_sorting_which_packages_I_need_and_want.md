---
title: "sorting which packages I need and want"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2011-09-06
I know that I can use **dpkg --get-selections ...** to learn which packages I have installed on any of the apt based (Ubuntu and Debian family) distributions.

I know that I can use **dpkg --set-selections ...** to restore that same set of packages to the same or another workstation.

[highlight]Q1a. What happens with set-selections when the stored package edition is older than whatever is already installed?[/highlight]

[highlight]Q1b. What happens with set-selections when there are differences in dependencies stored vs. new?[/highlight]

WAIT!! "dpkg" does not process dependencies only absolute package references. 
[highlight]Q1c. What can I use instead of "dpkg" that handles the same level of package list detail AND handles dependencies?[/highlight] 
I've tried both "synaptic" and "apt" lists without success. (I suspect a loose nut in the ops chair.)

Everyone recommends "fresh install" vs. "update" but there seems to be precious little in the way of utilities to aid migration from one running workstation's package set to a "fresh installed but newer" workstation's package set -- other than hours of select-->apply and
similar geeky-tinker work.

[highlight]Q2. How do larger organizations accomplish this?[/highlight] (I suspect hours of geeky-tinker to make one-off, then replicate, but I can hope{sic} for something better...)

I have a workstation running Ubuntu Lucid (v10.04 LTS) with all of the updates and lots of add-on packages. I plan a move to a different edition of Ubuntu, maybe even Kubuntu, or even jump ship to Mint. I believe in working smart, not hard, and so I want some semi-automatic way to sift the list of packages and reconcile them against the change is distro edition or base distro.

Thanks in advance,
~~~ 0;-Dan

---

### Post by SecretCode on 2011-09-06
Q1a - dpkg --get-selections only lists package names, not versions, so --set-selections will always install the latest version.

Q1b/c - the web suggests that ```
sudo apt-get dselect-upgrade
``` after dpkg --set-selections will resolve dependencies, but I'm not 100% clear on that.


If you are moving to a different DE (like Kubuntu), bear in mind that --get-selections will list lots of packages that are installed for your current distro and might be not needed / bloat on the new system. Best results would always be got via manually tinkering with the list.

What I've done is manually edit the list from the previous install and build a few 'sudo aptitude install x y z' commands with a few tens or hundreds of packages at a time.

Consider using an aptitude command like
```
aptitude search ?installed ?not(?automatic)
```
to exclude automatically installed dependencies.

---

### Post by oldfred on 2011-09-06
I have used dpkg without issue other than installing things not really required any more like python2.5 was on my list well after everone converted to 2.6. I manually houseclean some known old packages. If package is totally obsolete it will not install it (since it is not there to reinstall).

If you want a list with versions:
List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt


Alternative way with aptitude:
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install

Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/ch02s03s05.html")

HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

