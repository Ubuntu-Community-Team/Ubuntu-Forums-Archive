---
title: "which command can completely remove a package"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-03-14
Which command can completely remove a package when dpkg, apt-get, and aptitude all fail to?

---

### Post by Hippytaff on 2011-03-14
purge
 
```
sudo aptitude purge *packagemane*
```

---

### Post by mikewhatever on 2011-03-14
If dpkg, apt-get, and aptitude all fail to remove a package, it must either a special case, or something is broken. You should provide more detailed info on the problem.

---

### Post by doas777 on 2011-03-14
'apt-get remove' removes an app, but leaves any config files in system space. 
'apt-get purge' removes the app, and any systemspace config files, but leaves most userspace config files (since those are created at runtime, not at install time so the installer doesn't know they exist.)

---

### Post by Skaperen on 2011-03-14
> **mikewhatever said:**
> If dpkg, apt-get, and aptitude all fail to remove a package, it must either a special case, or something is broken. You should provide more detailed info on the problem.
On 10.04.2 LTS amd64 server edition, freshly installed, installing package "nsd3" using "apt-get install nsd3" will fail.  At this point all attempts to remove the package, including doing "purge" will fail.  Apparently those attempts depend on the package being fully installed and/or the nsd daemon being runnable.

Dare to try installing it yourself?  It works OK on 9.10 server edition.

So far the only thing I have found to do is re-install Ubuntu, which makes it very hard to figure out what can be given to this package to make its install successful.

I suspect the nsd3 package is broken.  But that's another issue.  I do believe that there should be a way to remove a failed install, as long as what files it did put in place do not go beyond the set of files the package is designated to installed.  This kind of forced remove might be best with a --force option or such.  But something should be available.  If the package installed a stray file somewhere, and that isn't in any list, then I would not blame the removal code for not getting it all removed (the focus is now on the installer which should have watched what all was installed).

[SIZE=1]BTW, I eventually did figure out how to get around the install problem with the "nsd3" package.  By creating a zone file and compiling it on another system (did it on a 9.10 server system here), and making a config file that correctly references it so no startup errors happen to the daemon, and putting that zone file in place (at "/etc/nsd3/nsd.conf"), it can be made to work.  There is a sample zone file provided by the package (named differently) that is not complete enough to be used as is.  Maybe the "nsd3" package needs to have a config file installed (it doesn't).  But the existing sample one won't do the job.
[SIZE=2]
[/SIZE] [/SIZE]

---

### Post by mikewhatever on 2011-03-14
Hi Skaperen, I've reported the problem to launchpad.
[https://bugs.launchpad.net/ubuntu/+source/nsd3/+bug/735128](https://bugs.launchpad.net/ubuntu/+source/nsd3/+bug/735128)

The way I was able to get rid of it was by removing the scripts that produced errors.
```
sudo rm /var/lib/dpkg/info/nsd3.prerm
sudo rm /var/lib/dpkg/info/nsd3.postrm
```

then purge the package:
```
sudo apt-get purge nsd3
```

That leaves some files behind that can be located with 'locate nsd3' and removed manually.
This is what's left behind:
```
$ locate nsd3
/etc/nsd3
/etc/cron.d/nsd3
/etc/init.d/nsd3
/etc/rc0.d/K20nsd3
/etc/rc1.d/K20nsd3
/etc/rc2.d/S20nsd3
/etc/rc3.d/S20nsd3
/etc/rc4.d/S20nsd3
/etc/rc5.d/S20nsd3
/etc/rc6.d/K20nsd3
/usr/share/doc/nsd3
/var/cache/apt/archives/nsd3_3.2.4-1_i386.deb
/var/crash/nsd3.0.crash
/var/lib/nsd3
/var/lib/dpkg/info/nsd3.conffiles
/var/lib/dpkg/info/nsd3.list
/var/lib/dpkg/info/nsd3.md5sums
/var/lib/dpkg/info/nsd3.postrm
/var/lib/update-rc.d/nsd3

```

to remove most of it:
```
sudo update-rc.d -f nsd3 remove
```

Now, with the nsd3 package gone, I still get the following error when installing updates:
```
dpkg: unrecoverable fatal error, aborting:
 syntax error: invalid uid in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Removing the three nsd related lines from /var/lib/dpkg/statoverride fixes it.

---

### Post by Skaperen on 2011-03-15
Thanks.  I don't know enough about Debian packaging to have known what to do with those files.

---

