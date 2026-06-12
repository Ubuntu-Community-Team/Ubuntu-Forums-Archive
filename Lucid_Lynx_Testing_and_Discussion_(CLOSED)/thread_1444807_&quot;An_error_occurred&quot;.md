---
title: "&quot;An error occurred&quot;"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by arnab_das on 2010-04-01
This is the error I'm getting while I try to upgrade:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.1-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.1-0ubuntu1_all.deb)
  404  Not Found [IP: 111.91.91.34 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu2_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu2_amd64.deb)
  404  Not Found [IP: 111.91.91.34 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.2.2-1ubuntu2_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.2.2-1ubuntu2_amd64.deb)
  404  Not Found [IP: 111.91.91.34 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.12.192-2ubuntu2_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.12.192-2ubuntu2_amd64.deb)
  404  Not Found [IP: 111.91.91.34 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.12.192-2ubuntu2_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.12.192-2ubuntu2_amd64.deb)
  404  Not Found [IP: 111.91.91.34 80]


--------------------

[[IMG]http://img221.imageshack.us/img221/3707/updatemanager001.png[/IMG]](http://img221.imageshack.us/i/updatemanager001.png/)

nothing has "broken" as yet. but is this something serious?

---

### Post by VMC on 2010-04-01
The last time I had that '404' on an update was my chrome ppa. Look into '/etc/apt/sources.list.d' That was the area that got messed up.

---

### Post by arnab_das on 2010-04-01
> **VMC said:**
> The last time I had that '404' on an update was my chrome ppa. Look into '/etc/apt/sources.list.d' That was the area that got messed up.

i havent added chrome ppa as yet and that folder sources.list.d is absolutely empty. havent added any 3rd party repos as yet. any other ideas?

---

### Post by ranch hand on 2010-04-01
Try a different mirror.

---

### Post by VMC on 2010-04-01
Are they all failing or just a couple? I forgot to ask this in the beginning.

---

### Post by arnab_das on 2010-04-01
> **VMC said:**
> Are they all failing or just a couple? I forgot to ask this in the beginning.

it was just those 4 files.

surprisingly, all 4 files were updated today, and i didnt even change the mirror.

anyway, question is, should i update in situations where there is a 404 error for some files? (as the error message says "all files were not downloaded. do you want to install?")

---

### Post by lucid 10.4 on 2010-04-02
try

```
sudo apt-get upgrade
```

---

