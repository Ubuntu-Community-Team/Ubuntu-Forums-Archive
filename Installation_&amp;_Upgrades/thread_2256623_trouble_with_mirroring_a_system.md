---
title: "trouble with mirroring a system"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by lance bermudez on 2014-12-13
I have 2 amd64 systems I did 

sudo dpkg --get-selections > package_list

then I moved the file package_list to the 2 computer
then I did

sudo dpkg --set-selections < package_list

and i get 

dpkg: warning: package not in database at line 1124: xfonts-mathml
dpkg: warning: package not in database at line 1124: xfonts-scalable
dpkg: warning: package not in database at line 1129: xmount
dpkg: warning: package not in database at line 1131: xorg-sgml-doctools
dpkg: warning: package not in database at line 1131: xrdp
dpkg: warning: package not in database at line 1131: xresprobe
dpkg: warning: package not in database at line 1131: xscreensaver
dpkg: warning: package not in database at line 1131: xscreensaver-data
dpkg: warning: package not in database at line 1131: xscreensaver-data-extra
dpkg: warning: package not in database at line 1131: xscreensaver-gl
dpkg: warning: package not in database at line 1131: xscreensaver-gl-extra
dpkg: warning: package not in database at line 1131: xsel
dpkg: warning: package not in database at line 1131: xsensors
dpkg: warning: package not in database at line 1165: xtrans-dev
dpkg: warning: package not in database at line 1167: yelp
dpkg: warning: package not in database at line 1167: yelp-xsl
dpkg: warning: package not in database at line 1167: youtube-dl
dpkg: warning: package not in database at line 1167: zeitgeist-core
dpkg: warning: package not in database at line 1169: zenmap
dpkg: warning: package not in database at line 1171: zlib1g:i386
dpkg: warning: package not in database at line 1171: zlib1g-dev:amd64
dpkg: warning: found unknown packages; this might mean the available database
is outdated, and needs to be updated through a frontend method

sudo apt-get install dselect
sudo dselect update
sudo dpkg --set-selections < Package.list && sudo apt-get -u dselect-upgrade

still not working still getting same error

please help

sudo apt-get install dselect
sudo dselect update
sudo dpkg --get-selections < Package.list && sudo apt-get -u dselect-upgrade

---

### Post by ibjsb4 on 2014-12-14
Try synaptic, see if does any better.
[ATTACH=CONFIG]258573[/ATTACH]

---

### Post by ian-weisser on 2014-12-14
Software Center has a feature for syncing package lists between machines to avoid all that mucking about in dpkg.

---

### Post by JimParker on 2015-01-07
I recently ran into this problem, and I believe the issue is a change in dpkg.  See discussion at these sites
[http://debian.2.n7.nabble.com/Bug-703092-dpkg-set-selections-ignores-available-packages-never-installed-or-removed-by-dpkg-td2891633.html](http://debian.2.n7.nabble.com/Bug-703092-dpkg-set-selections-ignores-available-packages-never-installed-or-removed-by-dpkg-td2891633.html)
[http://www.reddit.com/r/linuxquestions/comments/2qjg8m/why_hasnt_my_dpkg_script_worked_xpost_linux4noobs/](http://www.reddit.com/r/linuxquestions/comments/2qjg8m/why_hasnt_my_dpkg_script_worked_xpost_linux4noobs/)

The issue is that if a package is not already marked on your system as installed or removed, it cannot be added by the method that had worked for years.  Only packages already installed can be upgraded by the --set-selection < foo.list command, which completely destroys one's ability to mirror a system--the idea is to get stuff you don't have yet!

The solution is to install another tool "dselect" which will read the foo.list file and mark the database appropriately so that the new packages get included.
So, new workflow on the new machine is
```

sudo apt-get update
sudo apt-get install dselect
sudo dpkg --set-selections < package_list
sudo dselect upgrade
sudo dselect install

```

Cheers,
--Jim

---

### Post by ian-weisser on 2015-01-07
> **JimParker said:**
> I recently ran into this problem, and I believe the issue is a change in dpkg.

The discussion in Debian Bug#703092 seems pretty clear that it's not a change to dpkg.
It's just that dpkg isn't psychic. It needs a database to work with.

Here it is in the bug report:
> Version: 1.17.0
[...]
 * Clarify that dpkg --set-selections needs an up-to-date available db, 
     by documenting it on the dpkg(1) man page, and warning whenever dpkg 
     finds unknown packages while setting the selections. Closes: #703092

And here it is in the Reddit thread:
> dpkg: warning: found unknown packages; this might mean the available database is outdated, and needs to be updated through a frontend method

In your workflow, enabling the proper repositories and doing a normal apt-get update should be all you need to prepare for --set-selections.

---

