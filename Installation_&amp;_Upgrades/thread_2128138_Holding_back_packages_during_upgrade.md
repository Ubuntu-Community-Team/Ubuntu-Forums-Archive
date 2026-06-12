---
title: "Holding back packages during upgrade"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by johnbox on 2013-03-22
Hi,

I'm doing an upgrade on a ubuntu server (running sudo apt-get upgrade), but I don't want to upgrade any packages from a particular repository. I'm concerned with introducing dependency issues if I don't update them. I have two questions

1. In terms of dependencies is there a difference between removing the repository from sources.list.d, and running the hold back command for packages in that repository:
```
echo "<package_name> hold" | dpkg --set-selections
```

2. If I hold back a package I understand that other packages dependent on newer versions of the held back package will be prevented from being updated. Is the same true if the dependency is the other way. I.e. if the held back package is dependent on an older version of a package to be updated will it be prevented from updating?

Thanks

---

### Post by schragge on 2013-03-22
> **johnbox said:**
> 1. In terms of dependencies is there a difference between removing the repository from sources.list.d, and running the hold back command for packages in that repositoryYes, there is a difference, but not in terms of dependencies, see below about how dependencies work. Removing a repository doesn't prevent installing newer versions of same packages from another repositories if there are any. Obviously, if those packages were available only from the disabled repository, this would be equivalent to putting them on hold. Note also that *aptitude* may (and most probably will) ignore dpkg hold settings.

> **johnbox said:**
> 2. If I hold back a package I understand that other packages dependent on newer versions of the held back package will be prevented from being updated. Is the same true if the dependency is the other way. I.e. if the held back package is dependent on an older version of a package to be updated will it be prevented from updating? Yes, it's true, but only if versioned dependencies explicitly prevent it.

 Consider the following situation. You put package *foo* on hold. This won't prevent newer versions of *bar* from being installed:
```

Package: foo
Version: 1
Depends: bar (>= 0.5)

```

OTOH, this sure would prevent any version of *bar* newer than 0.5 from being installed:
```

Package: foo
Version: 1
Depends: bar (= 0.5)

```

The same is true for the reverse dependencies, too.
 
This dependency will be satisfied by any version of *foo*:
```

Package: baz
Version: 1.201303
Depends: foo

```

 The following dependency won't be satisfied by *foo* version 1, so this version of *baz* cannot be installed as long as *foo* v.1 is on hold:
```

Package: baz
Version: 1.201305
Depends: foo (>> 1)

```

---

### Post by johnbox on 2013-03-22
That's great, thanks very much for your reply.

---

### Post by schragge on 2013-03-22
BTW, if you want to put on hold all packages from a specific repository, you may consider following. Each repository puts its package index under */var/lib/apt/lists/*. The files there are named after deb strings in */etc/apt/sources.list* and/or */etc/apt/sources.list.d/*.list*. So, say if you have enabled the [Medibuntu]("http://www.medibuntu.org") repository and */etc/apt/sources.list.d/medibuntu.list* contains a string starting with
```
deb http://packages.medibuntu.org/...
``` there will be a corresponding package index for medibuntu under
```
/var/lib/apt/lists/packages.medibuntu.org_..._Packages
```

That means you can put all packages from Medibuntu on hold with
```
sudo apt-mark hold `sed -n s/^Package://p /var/lib/apt/lists/*.medibuntu.*Packages`
```
As long as you aren't mixing packages for different architectures (say amd64 and i386), the command above will work as expected. However, in a multiarch environment it will lock only packages for the native architecture. Setting on hold packages for a foreign architecture will require something like the following (provided that the foreign architecture is i386)
```
sudo apt-mark hold `sed -nr 's/^Package:\s*(\S+)/\1 \1:i386/p' /var/lib/apt/lists/*.medibuntu.*Packages`
```
Trying to put on hold only actually installed packages from a 3rd part repository further complicates the matter:
```

awk -F':[ \t]*' '/^Package:/,/^$/{
        if(/^Package:/){p=$2;a=""}
        if(/^Architecture:/&&$2!="all")a=":"$2
        if(/^$/)print p""a" hold"
}' /var/lib/apt/lists/*.medibuntu.*Packages|sort -uk1,1|
join - <(dpkg -l|awk '/^ii/{print$2}'|sort)|sudo dpkg --set-selections
sudo dpkg -Pa

```
Using [combine]("http://manpages.ubuntu.com/manpages/precise/en/man1/combine.1.html") provided by package *moreutils* together with *dctrl-tools* simplifies this task a bit:
```

sudo apt-get install moreutils dctrl-tools
alias _=combine
_ <(grep-dctrl -sPackage,Architecture '' /var/lib/apt/lists/*.medibuntu.*Packages|tbl-dctrl -Hd:) and <(grep-status -FStatus  -sPackage,Architecture 'ok installed'|tbl-dctrl -Hd:) _|
sed 's/$/ hold/'

```
The method used by [ppa-purge]("http://manpages.ubuntu.com/manpages/precise/en/man1/ppa-purge.1.html") to select all packages installed from a PPA is also worth mentioning:
```

sed -n s/^Package://p /var/lib/apt/lists/*.medibuntu.*Packages|sort -u|xargs -r dpkg -l 2>/dev/null|awk '/^ii/,$0=$2" hold"'

```
Using [aptitude]("http://manpages.ubuntu.com/manpages/precise/en/man8/aptitude.8.html") makes the task look quite straightforward. Unfortunately, aptitude's hold state has nothing to do with dpkg's hold state and won't be honored by any other package management tool. Still, if you manage your packages exclusively through aptitude, it may be convenient:
```
sudo aptitude hold ~i~OMedibuntu
```

Otherwise, the best available option is to feed the output of *aptitude search *either to *apt-mark hold* or directly to *dpkg*:
```

sudo apt-mark hold `aptitude --disable-columns -F%p search ~i~OMedibuntu`

```
or
```

aptitude --disable-columns -F'%p hold' search ~i~OMedibuntu|sudo dpkg --set-selections
sudo dpkg -Pa

```

---

