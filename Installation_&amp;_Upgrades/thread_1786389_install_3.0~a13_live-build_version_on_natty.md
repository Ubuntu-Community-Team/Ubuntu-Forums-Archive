---
title: "install 3.0~a13 live-build version on natty"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by cccc on 2011-06-19
hi

I've the following **live-build** version installed on my ubuntu natty:```

$ lb -v
live-build, version 2.0.12-1
This program is a part of 

Copyright (C) 2006-2011 Daniel Baumann <daniel@debian.org>
```

Howto install **3.0~a...** version on natty?

---

### Post by cccc on 2011-06-19
I've installed **live-build_3.0~a18-1_all.deb**, but get this problem:```


# lb config -p xubuntu-desktop --mode ubuntu --distribution natty -b usb-hdd 
# lb build

........................................................
P: Begin executing preseed...
P: Begin executing local preseeds...
P: Begin queueing installation of package lists...
W: Unknown package list 'xubuntu-desktop'
P: Begin queueing installation of local package lists...
P: Begin queueing installation of packages...
P: Begin queueing installation of local packages...
P: Begin installing packages...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package live-config
E: Unable to locate package live-config
P: Begin unmounting filesystems...
```

So I've tried to install **live-config-systemd_3.0~a18-1_all.deb**, but get this problem:```

# dpkg -i live-config_3.0~a18-1_all.deb
(Reading database ... 145178 files and directories currently installed.)
Preparing to replace live-config 2.0.14-1 (using live-config_3.0~a18-1_all.deb) ...
Unpacking replacement live-config ...
Setting up live-config (3.0~a18-1) ...
Processing triggers for man-db ...
```

but sysvinit seems to be already installed:```

# dpkg -l | grep sysvinit
ii  sysvinit-utils                        2.87dsf-4ubuntu23                          System-V-like utilities
```

Howto solve this?

---

### Post by cccc on 2011-06-25
I still cannot find any solution.
BTW Has someone already tried to install live-config-systemd_3.0~a... on your Ubuntu?

---

### Post by AndreOrbe on 2012-06-07
live-config needs universe area.
Just add --parent-archive-areas "main universe" in live configuration.

---

### Post by cccc on 2012-06-07
> **AndreOrbe said:**
> 
Just add --parent-archive-areas "main universe" in live configuration.

Thx a lot, but can you pls give me an example of --parent-archive-areas?

---

### Post by AndreOrbe on 2012-06-07
I had to modify live scripts as explained in [http://live.debian.net/gitweb?p=live-build.git;a=commitdiff;h=40a8a8ee7523240f4657b768909a9ed92fcfebc5](http://live.debian.net/gitweb?p=live-build.git;a=commitdiff;h=40a8a8ee7523240f4657b768909a9ed92fcfebc5) and use this config (I dont know the meaning of parent-* configurations but i added too).

lb config noauto \
    -m "http://your_ubuntu_repository" \
    --parent-mirror-binary "http://your_ubuntu_repository" \
    --parent-mirror-binary-security "http://your_ubuntu_repository" \
    --parent-mirror-chroot-security "http://your_ubuntu_repository" \
    --mirror-chroot-security "http://your_ubuntu_repository" \
    --mirror-bootstrap "http://your_ubuntu_repository" \
    --mirror-binary "http://your_ubuntu_repository" \
    --mode "ubuntu" \
    --package-lists "standard" \
    --archive-areas "main universe multiverse" \
    --parent-archive-areas "main universe multiverse" \
    --parent-distribution "precise" \
    -d "precise" \
    "${@}"
I added others packages (like gnome, ...) in a text file (something.chroot.list) in the config/package-lists folder.

---

### Post by cccc on 2012-06-07
> **AndreOrbe said:**
> I had to modify live scripts as explained in [http://live.debian.net/gitweb?p=live-build.git;a=commitdiff;h=40a8a8ee7523240f4657b768909a9ed92fcfebc5](http://live.debian.net/gitweb?p=live-build.git;a=commitdiff;h=40a8a8ee7523240f4657b768909a9ed92fcfebc5) and use this config (I dont know the meaning of parent-* configurations but i added too).

lb config noauto \
    -m "http://your_ubuntu_repository" \
    --parent-mirror-binary "http://your_ubuntu_repository" \
    --parent-mirror-binary-security "http://your_ubuntu_repository" \
    --parent-mirror-chroot-security "http://your_ubuntu_repository" \
    --mirror-chroot-security "http://your_ubuntu_repository" \
    --mirror-bootstrap "http://your_ubuntu_repository" \
    --mirror-binary "http://your_ubuntu_repository" \
    --mode "ubuntu" \
    --package-lists "standard" \
    --archive-areas "main universe multiverse" \
    --parent-archive-areas "main universe multiverse" \
    --parent-distribution "precise" \
    -d "precise" \
    "${@}"
I added others packages (like gnome, ...) in a text file (something.chroot.list) in the config/package-lists folder.

BTW how do you use this script?

---

### Post by AndreOrbe on 2012-06-07
Take a look the examples: [http://live.debian.net/manual/html/live-manual.en.html#749](http://live.debian.net/manual/html/live-manual.en.html#749)

---

### Post by cccc on 2012-06-08
Thx

---

