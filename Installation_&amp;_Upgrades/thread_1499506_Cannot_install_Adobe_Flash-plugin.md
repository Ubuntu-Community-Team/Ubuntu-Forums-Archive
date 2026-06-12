---
title: "Cannot install Adobe Flash-plugin"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by skipperx on 2010-06-02
I have used another Linux for a couple of years and now trying out ubuntu.

I just did a clean install of 32-bit Lucid. When I tried to install the Adobe Flash Plugin for Firefox, I got an error message. 

```
$ sudo apt-get install  adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

```

Could someone please let me know how to fix this.

Thank you.

---

### Post by garvinrick4 on 2010-06-02
```
sudo apt-get install flashplugin-installer
```

---

### Post by garvinrick4 on 2010-06-02
You want to get all the stuff: Java, codec's, true type fonts, flash, and more.

```
sudo apt-get install ubuntu-restricted-extras
```

If some of it is already installed will not hurt, just install things you need for
video's, music, flash and things. Nice package. Should have more packages.

---

### Post by skipperx on 2010-06-02
Thanks very much. It worked.

---

