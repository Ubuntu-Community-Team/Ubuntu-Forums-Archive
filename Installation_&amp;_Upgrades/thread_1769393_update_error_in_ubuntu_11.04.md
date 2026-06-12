---
title: "update error in ubuntu 11.04"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by bipinbaglung on 2011-05-27
I have installed Ubuntu 11.04 some days ago. Now when i try to run synaptic package manager it terminates with this error:

[COLOR="Red"]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.mitra.net.np_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/COLOR]


then i tried to update from my terminal. With some provided information i tried this in terminal:

[COLOR="Purple"]sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update[/COLOR]

then it run for some packages then ends with this error:

[COLOR="Red"]W: GPG error: [http://archive.mitra.net.np](http://archive.mitra.net.np) natty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.mitra.net.np](http://archive.mitra.net.np) natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.mitra.net.np/ubuntu/dists/natty/restricted/source/Sources](http://archive.mitra.net.np/ubuntu/dists/natty/restricted/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]



Thus i cannot update with any way. What is the solution?? :confused:

---

### Post by Rubi1200 on 2011-05-28
Hi,

you could try the methods mentioned here to fix this:
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Good luck and let me know what happens please.

---

### Post by ezwages on 2011-05-28
Method two from the site mentioned above worked for me...thanks

---

### Post by Rubi1200 on 2011-05-28
> **ezwages said:**
> Method two from the site mentioned above worked for me...thanks
No problem, you are more than welcome and glad it worked :-)

---

