---
title: "dvd rip generic from repo"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-06-26
your going to need to add a few things

```

mkdir /home/$USER/dvdrip-data

```

going to need to install rar, unrar, xvid4conf,  from synaptic.

then edit > preferences > check all settings to see if its complaining for more backends....

then set for cluster mode for as many cores as your computer has and good to rip

:guitar:

further inspection shows that this package is very nitty gritty, but its ok, ive built this one from scratch before...


must set up the cluster, it has its own diagnostics panel to ensure your setup completely correctly.

i will configure this for my 4+ ht processor 
```

export MAKEFLAGS="-j 5"

```
 style in program, completely ensuring im running full blast for transcoding, because its slow to process video.

in cluster click control, then add node then name the node
```

nodea
nodeb
nodec
nodee
nodef

```

host
```

localhost

```

local data directory
```

~/dvdrip-data

```


speed index
```

100

```

click yes for both the buttons, then test settings
and you should be good to rip full speed on that core, repeat this several times until you have the 5 nodes

close the cluster config

then control d

then in dvd rip click "rip title"
then read dvd table of contents

then rip selected title
then have so many problems you start investigating hand brake ppa lol

ppa:stebbins/handbrake-releases
synaptic handbrake-cli handbrake-gtk

looks like im missing libdvdread-dev

?????

im begining to remember a bug in dvd::rip that the source ISO cannot have spaces in the title, (this program runs GREAT for dvd, and like **** for a file converter but it can do file conversions)

mkdir /home/$USER/dvdrip-iso

again this package does not like \ escaped directories, no spaces! or freaky charicters like ('s

---

