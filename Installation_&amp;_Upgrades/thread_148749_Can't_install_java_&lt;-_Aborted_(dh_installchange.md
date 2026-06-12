---
title: "Can't install java &lt;- Aborted (dh_installchangelogs)"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-03-22
As per [https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca) I'm trying to install Sun's java. When I do 
```

DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

```
I get the following error after a bunch of permission errors and the .deb isn't created: 
```

Done.

Testing extracted archive... okay.

Create debian package:
    dh_testdir
    dh_testroot
    dh_installchangelogs
dh_installchangelogs:

Aborted (dh_installchangelogs).

```

I checked the permissions and they are fine. There are no log files to read in /path/to/java[...].bin ; /tmp ; and /var/log

Does anyone know what to do with this? I reopened and subscribed to this bug: [https://launchpad.net/distros/ubuntu/+source/java-package/+bug/1370](https://launchpad.net/distros/ubuntu/+source/java-package/+bug/1370) but it's more or less hopeless (Dapper is coming out soon) and I got no response either. 

My searches ended up seeing other people having this problem but no solutions... I would appreciate any help. 

As a side note, I uninstalled Blackdown Java and currently using this thing in "alternatives":
```

  Selection    Alternative
-----------------------------------------------
***     1**        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java

```

---

### Post by towsonu2003 on 2006-03-23
bump...

---

### Post by adamkane on 2006-03-23
See:
[http://www.ubuntuforums.org/showthread.php?t=148758](http://www.ubuntuforums.org/showthread.php?t=148758)

---

### Post by towsonu2003 on 2006-03-23
[quote=adamkane]
See:
[http://www.ubuntuforums.org/showthread.php?t=148758](http://www.ubuntuforums.org/showthread.php?t=148758)
[/quote]that has the same instructions as the wiki does. 
```
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
``` doesn't work for me (plugins not found error) so I have to use ```
DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
``` which gives the above error...

---

### Post by adamkane on 2006-03-23
Are you running an Athlon system?

Also there is a note on the Wiki:
 Note: in above example, *i386* might have to be *i586*

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=adamkane]Are you running an Athlon system?

Did you do the following, because you were getting errors?
```

DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

```

Sorry for asking a bunch of dumb questions?[/QUOTE]
That's fine :) I'm running Celeron M (i686)... DEB_BUILD_GNU_TYPE=i386-linux was necessary due to the following error when I don't give that environment (source: wiki page)
```

Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

  No matching plugin was found.
```
If this error is received, the wiki page says "use DEB_BUI....... command instead"...

---

