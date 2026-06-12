---
title: "Skype installation Problems"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by geek in training on 2010-01-15
Hi all, I'm running 9.10 64-bit ubuntu. I'm fairly new to Linux, so this might be completely simple and I'm just overlooking the cause of the problem.

I've downloaded Skype 2.1.0.47-1 from [http://www.skype.com/go/getskype-linux-beta-ubuntu-64]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64")

When I try double clicking the .deb file to run it, it doesn't work. I get the print out of **Could not open 'skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb** The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

I don't understand why this won't work for me now. I installed this about a week ago on an identical machine without any hiccups at all.

When I tried to install from terminal, I got the readout

```
Selecting previously deselected package skype.
(Reading database ... 178035 files and directories currently installed.)
Unpacking skype (from skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/bin/skype')
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
```

Thanks in advance!

---

### Post by x33a on 2010-01-15
try another copy of the deb. or try,
```
sudo gdebi <filename>
```

---

### Post by geek in training on 2010-01-16
The new deb file worked fine. Installation was smooth. Thanks!

---

