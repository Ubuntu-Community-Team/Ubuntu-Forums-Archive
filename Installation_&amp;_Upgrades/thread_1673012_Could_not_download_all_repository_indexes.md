---
title: "Could not download all repository indexes"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by WaNaBePi on 2011-01-21
I get this when I use update manager or sudo app get update

```
Failed to fetch http://security.debian.org/dists/etch/updates/main/binary-amd64/Packages.gz  404  Not Found [IP: 149.20.20.6 80]
Failed to fetch http://security.debian.org/dists/etch/updates/contrib/binary-amd64/Packages.gz  404  Not Found [IP: 149.20.20.6 80]
Failed to fetch http://security.debian.org/dists/etch/updates/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 149.20.20.6 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

I have a samsung rf510. I'm pretty sure I should have these updating for the comp to operate smoothly.

How do i fix this issue?

---

### Post by gordintoronto on 2011-01-21
Are you using Ubuntu or Debian? If it's Ubuntu, you can delete those lines using Administration/Software Sources.

---

### Post by WaNaBePi on 2011-01-23
"Using Ubuntu 10.04 LTS- the Lucid Lynx - released in April 2010 and supported until April 2013." 64bit.

some of my usb ports work only some times, I cant figure out what causes them to stop working. I thought this update issue *may be* the culprit but it seems it would just be for the processor.

There is no harm in deleting those lines? Are you sure? If so, I can do that, I think.

---

### Post by gordintoronto on 2011-01-23
If you installed a Debian package, those repositories may have been added. They are not part of Ubuntu. I don't have anything like them in my software sources.

Do you use a virtualization application?

In my /etc/apt/sources.list I have:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

These are for Ubuntu 10.10, of course.

---

### Post by WaNaBePi on 2011-01-24
I don't know what a virtualization application is. If i did, it could have been while I was installing my half working java that has no sound.

Well I got rid of the "security" entry with Debian, and the issue went away. I still have Ubuntu security checked off, so I guess every thing is good because I have the same entires for my version.

Solved?

Thank you gordintoronto.

---

### Post by gordintoronto on 2011-01-24
Solved!

The only mystery is where those entries came from, but it's not worth worrying about.

---

