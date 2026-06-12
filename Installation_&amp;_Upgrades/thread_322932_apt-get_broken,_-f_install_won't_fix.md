---
title: "apt-get broken, -f install won't fix"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by soundguy24 on 2006-12-21
apt-get is recommending an update to "python-uno", but the install fails. I would try to reinstall my python2.4 installation, but when I do that, it stops and tells me to run apt-get -f install instead, which is the command that produces this output:

```

Preparing to replace python-uno 2.0.4-0ubuntu2 (using .../python-uno_2.0.4-0ubuntu4_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/python-uno_2.0.4-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ukch on 2006-12-21
Hmm... Try completely removing python-uno and then reinstalling it.

---

### Post by soundguy24 on 2006-12-21
Well, I cant use apt-get at all. When I remove python-uno, it says:

```

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  openoffice.org-writer: Depends: python-uno (>= 2.0.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by billybag on 2006-12-21
I am having a similar problem with updating openoffice. it is bugging the hell out of me and i can't figure out how to fix it. [http://ubuntuforums.org/showthread.php?t=322610](http://ubuntuforums.org/showthread.php?t=322610)

---

### Post by soundguy24 on 2006-12-21
Fixed. I found [the bug on launchpad]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/75557") and ran
```
sudo rm /var/lib/dpkg/info/python-uno.prerm 
```
to restore apt-get operations. Don't know what effect that will have for me in the long term, but it's fixed now.

---

