---
title: "[SOLVED] Need to downgrade subversion and can't work out how"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by phasmal on 2008-11-18
I have the [[COLOR="Blue"]_same issue as a previous poster_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=382249").

Basically I need an old version of Subversion to match one (1.4.x) I'm deploying against (don't get me started on how annoying it is we're using old versions of things!) and I couldn't get the from-source installation to work.  Although I'd rather have a separate version I use for this stuff I'm forced to consider downgrading my main version of subversion so that my code works...

So I tried "Force Version..." in Synaptic Package Manager, but it's greyed out/disabled.  I briefly looked at [[COLOR="Blue"]_'pinning'_[/COLOR]]("https://help.ubuntu.com/community/PinningHowto") but it seems to me that I'd need to know which release of ubuntu had the version I'm after, and I've no idea how to work that out - or if its even feasible...

So I'm out of ideas...

Phasmal

---

### Post by Partyboi2 on 2008-11-18
[[COLOR=Blue]Here[/COLOR]]("http://packages.ubuntu.com/search?keywords=subversion&searchon=names&suite=all&section=all") is the different versions of subversion.

---

### Post by phasmal on 2008-11-18
OK, so that means I need the version from 'hardy'

So I've put the following in my [FONT="Courier New"]/etc/apt/preferences[/FONT] file as the [article on pinning]("https://help.ubuntu.com/community/PinningHowto") implied, and updated my [FONT="Courier New"]/etc/apt/sources.list[/FONT] file (basically I just took any line that had 'intrepid' and duplicated it while substituting 'hardy' for 'intrepid')

So my [FONT="Courier New"]/etc/apt/preferences[/FONT] file now looks like the following.

```

Package: subversion
Pin: release a=intrepid
Pin-Priority: -10

Package: subversion
Pin: release a=hardy
Pin-Priority: 900

```

I then (bravely I think :) ) removed my subversion install and tried to reinistall...

```

sudo apt-get update
sudo apt-get install subversion
[CODE]


... but it don't work.. :(

I get the following error

[CODE]
The following packages have unmet dependencies.
  subversion: Depends: libsvn1 (= 1.4.6dfsg1-2ubuntu1) but 1.5.1dfsg1-1ubuntu2 is to be installed
E: Broken packages

```

Does this mean I need to pin some other packages as well?

---

### Post by phasmal on 2008-11-18
OK, i clearly answered my own question here.

I was thinking that subversion was trying to install at 1.5.x, but it seems that libsvn1 was ... I guess...

anyway, I added libsvn1 to my preferences file to be pinned, and it worked!

```

> sudo apt-get install subversion

...
...
...

The following NEW packages will be installed
  subversion
The following packages will be DOWNGRADED:
  libsvn1

...
...
...


> svn --version
svn, version 1.4.6 (r28521)
   compiled Mar 11 2008, 08:26:35

```

Note that it actually told me that it was going to downgrade a package... perhaps I could have done this without removing the package in the first place...? Assumedly by doing an "apt-get upgrade"...

Anyway, now my [FONT="Courier New"]/etc/apt/preferences[/FONT] file looks like:

```

Package: subversion
Pin: release a=intrepid
Pin-Priority: -10

Package: subversion
Pin: release a=hardy
Pin-Priority: 900

Package: libsvn1
Pin: release a=intrepid
Pin-Priority: -10

Package: libsvn1
Pin: release a=hardy
Pin-Priority: 900

```

---

### Post by phasmal on 2008-11-18
Oh, and I fiddled with the Synaptic gui at one point while doing this, and the "Force Version..."  option was enabled.. so perhaps all i had to do to use the gui to solve this was add the hardy sources in the software sources gui...  It wasn't smart enough to work out the libsvn1 thing, though, so I would probably have needed to force both of the packages anyway.

---

### Post by Partyboi2 on 2008-11-18
Having hardy and intrepid entries in your sources.list is not advised as this can cause breakages. The better way would have been to download the hardy deb package for subversion then manually try installing the package, once it was installed then go to Synaptic and lock version. :)

---

