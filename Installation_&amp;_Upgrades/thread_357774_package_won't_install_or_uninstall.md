---
title: "package won't install or uninstall"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by one_stinky_bum on 2007-02-10
I'm running edgy and I tried to install the package k3d in synaptic but I get the following error:

```
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now I can't remove it either (error code 1 again).  Could someone please help me figure this one out? I just don't want error messages to appear when I run apt-get upgrade.

Thanks.

---

### Post by gradedcheese on 2007-02-10
you could try to remove it like this:

sudo dpkg --remove k3d

and if that still fails:

sudo dpkg --force --remove k3d

---

### Post by one_stinky_bum on 2007-02-10
Thanks for the quick reply. I tried either of those commands and I still got an error: 
```

dpkg: unknown force/refuse option `--remove'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

I looked at the --force- options but there doesn't seem to be something to just remove the file ignoring errors, and the potential options all have a note saying "WARNING - use of options marked [!] can seriously damage your installation."

Any more help?

---

### Post by gradedcheese on 2007-02-10
I'm sorry, it's actually "sudo dpkg --force-remove k3d"

---

### Post by one_stinky_bum on 2007-02-12
Yep, tried that too, didn't work. I ended up editing the file that dpkg uses to keep track of installed files in /var/lib/dpkg/status. I know it's not the best way to do it, but none of the force commands worked for me. I kept getting that python error. Now it's gone.

---

