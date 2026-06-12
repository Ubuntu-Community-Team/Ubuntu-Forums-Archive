---
title: "Undetermined package name"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by gnostlos on 2013-07-07
I cannot download emacs23 to U12.04. Following a tip to another user, I tried "apt-get clean" and then "apt-get update". Update failed after some activity with this message:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 2,019 kB in 36s (56.0 kB/s)                                            
Reading package lists... Error!
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This was followed by alerts: "...12.04 has experienced an internal error...Could not determine the package or source package name."

What can be tried next?

---

### Post by kleenex on 2013-07-07
Hi. Please try:

```
sudo apt-get clean  
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

On the net there is a bunch of similar problems. Best regards.

---

### Post by Bashing-om on 2013-07-07
gnostlos; Hi !

In addition to kleenex's advisement:
Add the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2B3F92F902D65EFF
```
substituting the alpha-numeric string from your (each) errors output.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by gnostlos on 2013-07-08
Problem solved! I did what kleenex said, and it worked fine, unblocking the download. I did not see Bashing-om's added suggestion before I tried it, but appreciate that too. When kleenex says there are similar problems on the Net, I am not sure where, but am well satisfied.

---

