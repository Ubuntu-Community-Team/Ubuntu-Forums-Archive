---
title: "Error when adding repo for mythtv 0.26"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by wosc99 on 2013-08-18
Hi,

I am trying to update mythtv frontend from 0.25 to 0.26 on an Apple TV (1st gen) running Mythbunty 12.04.

I tried using mythbuntu-control-centre w/o luck so now I tried: sudo add-apt-repository ppa:mythbuntu/0.26

- but this results in error as shown:[COLOR=#111111]

[/COLOR]Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 53, in <module>
    from ppa import AddPPASigningKeyThread, expand_ppa_line
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 31, in <module>
    import pycurl
ImportError: librtmp.so.0: cannot open shared object file: No such file or directory




Any idea what I need to do?

Thanks

---

### Post by wosc99 on 2013-09-03
bump

Any suggestions?

Thanks

---

### Post by lindend on 2013-09-20
I've got the same problem w/librtmp.so.0 after upgrading from 10.04 to 12.04.  Did you ever find a solution to this problem?

---

### Post by lindend on 2013-09-20
The solution described in the thread below solved the problem for me.  [http://ubuntuforums.org/showthread.php?t=2079130](http://ubuntuforums.org/showthread.php?t=2079130)

---

