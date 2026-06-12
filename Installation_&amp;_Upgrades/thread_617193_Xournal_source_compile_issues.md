---
title: "Xournal source compile issues"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by embrodak on 2007-11-19
Grrr!!! I'm going crazy!  I am trying to compile xournal from source because I changed some of the code. However, when I run ./autogen.sh, I get package requirement errors:

```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libgnomecanvas-2.0 >= 2.4.0 libgnomeprintui-2.2 >= 2.0.0) were not met:

No package 'gtk+-2.0' found
No package 'libgnomecanvas-2.0' found
No package 'libgnomeprintui-2.2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I *know* it's just looking for the dev files, but for some reason, I can't install those either!  Output for apt-get install libgtk2.0-dev:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages

```

If I try to install those "unmet dependencies" I get a list of even more unmet dependencies and a broken packages error:
```

# apt-get install libcairo2-dev libpango1.0-dev libfontconfig1-dev libfreetype6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.2.1-5ubuntu1.1) but 2.3.2-0mlind1~edgy1 is to be installed
E: Broken packages


```

I've also tried apt-get build-dep xournal, but it errors as well:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for xournal could not be satisfied.

```

I'm probably just being incredibly stupid, but please help me! I will give you cookies!

---

### Post by embrodak on 2007-12-05
Bump.  Please, if anybody has any ideas of what I need to do, or if I need to give more information, let me know!!

Also, as a somewhat unrelated issue, I can no longer open my math notes in xournal.  I edited the notes during class, saved, exported to pdf, then rebooted my laptop, and now xournal gives me an "Error opening file" message. All my other files open up just fine. Does anybody know if xournal backs up files anywhere? According to the user manual, an xoj file is a gzipped xml-like file, but I was unable to unzip it.  Any help at all would be greatly appreciated. My math final is on Monday. :(:(

Thanks!

---

