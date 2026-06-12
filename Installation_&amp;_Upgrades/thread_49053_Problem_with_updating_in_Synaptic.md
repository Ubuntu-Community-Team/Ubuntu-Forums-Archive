---
title: "Problem with updating in Synaptic"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by jcwaldrop on 2005-07-14
I am very new to Linux and even moreso to this Synaptics Package Manager. I went through the updater thing and updated most everything except for Firefox and some libcairo file (??), because this error message is popping up:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)
  MD5Sum mismatch

What gives, any takers on helping me out here?

Thanks,
Jesse

---

### Post by javiadip on 2005-07-14
open a terminal and type in

sudo gedit /etc/apt/sources.list

and edit remove the us. from [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

save it and exit the file, then type sudo apt-get update

this should work :)

---

### Post by jcwaldrop on 2005-07-15
Thanks, it worked.

Jesse

---

