---
title: "Help me ! i got this when i try to install browser"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by alhisham on 2011-07-26
alhisham@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-mozilla-daily/firef&#8203;ox-aurora
[sudo] password for alhisham: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 70, in <module>
    if not sp.add_source_from_line(line):
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 647, in add_source_from_line
    (deb_line, file) = expand_ppa_line(line.strip(), self.distro.codename)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 49, in expand_ppa_line
    ppa_owner, ppa_name, distro_codename)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 55: ordinal not in range(128)

what does it mean ? why i can't install aurora ? last time before i reinstall 11.04, it was ok. yesterday, my friend try to install it and it's worked

---

