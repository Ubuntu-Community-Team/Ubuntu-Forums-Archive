---
title: "lib_apt problem, server upgrade"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by pnmoslo on 2011-05-09
Attempt to upgrade 10.10 to 11.04 server installation (more or less plain vanilla) gives:


~$ sudo do-release-upgrade
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 5, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 21, in <module>
    import apt_pkg
ImportError: libapt-pkg-libc6.9-6.so.4.7: cannot open shared object file: No such file or directory

The python file is there:

~$ sudo find / -name apt_pkg* -print
/usr/lib/python2.6/dist-packages/apt_pkg.so
/usr/local/lib/python2.6/dist-packages/apt_pkg.so

Tried reinstalling the obvious packages related to this, no change. Aptitude updates to 10.10 function without problems.

Can anyone point me in the right direction?

---

### Post by pnmoslo on 2011-06-17
Is there really no-one who can help with this problem?

$ sudo do-release-upgrade
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 5, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 21, in <module>
    import apt_pkg
ImportError: libapt-pkg-libc6.9-6.so.4.7: cannot open shared object file: No such file or directory

(attempting to upgrade from maverick to natty)

Normal use of apt (and aptitude) works just fine -- its the do-release-upgrade that bombs. I've run apt-get install --reinstall on every package I think might be relevant, but am a little wary about purging and reinstalling this particular group of packages (what happens if you purge apt?).

The file should presumably be here:

$ ls -l /usr/lib/libapt*
lrwxrwxrwx 1 root root    20 2011-06-17 20:21 /usr/lib/libapt-inst.so.1.2 -> libapt-inst.so.1.2.0
-rw-r--r-- 1 root root   74K 2011-04-26 23:13 /usr/lib/libapt-inst.so.1.2.0
lrwxrwxrwx 1 root root    20 2011-06-17 20:29 /usr/lib/libapt-pkg.so.4.10 -> libapt-pkg.so.4.10.1
-rw-r--r-- 1 root root 1003K 2011-04-26 23:13 /usr/lib/libapt-pkg.so.4.10.1

---

### Post by pnmoslo on 2011-06-27
FWIW:

sudo find / -name apt_pkg* -print
/usr/lib/python2.6/dist-packages/apt_pkg.so
/usr/local/lib/python2.6/dist-packages/apt_pkg.so

The second of these was an old version, presumably not removed during an update -- the python path had this being read before the correct (/usr/lib) file.

---

