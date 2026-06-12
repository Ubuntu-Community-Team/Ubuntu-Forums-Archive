---
title: "Failed to download repository information"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by JKarp84 on 2011-01-26
```
W:Failed to fetch http://archive.ubuntu.com/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.170 80]
, W:Failed to fetch http://archive.ubuntu.com/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.170 80]
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

not sure why its not allowing me to download these packages through the update manager. Im fairly sure these are default sources that come with Maverick and would very much like to have these packages. Any help?

---

### Post by gordintoronto on 2011-01-26
Change your download server in Software Sources.

---

### Post by JKarp84 on 2011-01-28
change them to what?

---

### Post by Fullmetal78 on 2011-04-10
> **JKarp84 said:**
> change them to what?

I have changed my server but still get an update error.

---

### Post by Old_Grey_Wolf on 2011-04-10
Fullmetal78,

Enter this command in a terminal. Then copy and post the output from the command to the forum.```
sudo apt-get update
```

Then,

Enter this command in a terminal. Then copy and post the output from the command to the forum.```
sudo apt-get upgrade
```

Also tell us what version of Ubuntu you are running. If you do not know, enter this command in the terminal and post the output to the forum.```
cat /etc/*release
```

---

### Post by KegHead on 2011-04-10
Have  LOOK HERE!

KegHead

---

