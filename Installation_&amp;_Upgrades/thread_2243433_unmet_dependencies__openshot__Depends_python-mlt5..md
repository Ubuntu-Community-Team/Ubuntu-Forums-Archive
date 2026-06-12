---
title: "unmet dependencies:  openshot : Depends: python-mlt5. E: Unable to correct problems,"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by Daniel_Narrias on 2014-09-08
Hello everyone.

I've been trying to solve this problem by googling it but it's been totally unsuccessful. I've tried every single suggested solution and none of them works. :( I gave up so I hope somebody can help me out with this.

I had installed Openshot and Blender. I couldn't use 3D animated features (not matching of Openshot and Blender), so then I uninstalled them with "sudo apt-get remove openshot" "sudo apt-get remove blender". I think somehow this deleted dependencies used by other applications and broke packages. 

Now, when I try to install Openshot back, using a PPA for example (google entries), then I type
> sudo apt-get update
> sudo apt-get install openshot openshot-doc

and I get the error

```

The following packages have unmet dependencies:
 openshot : Depends: python-mlt5 but it is not going to be installed or
                     python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

When I try to install each package, I get into a loop without end:

> sudo apt-get install python-mlt5

```

The following packages have unmet dependencies:
 python-mlt5 : Depends: libmlt5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Then

> sudo apt-get install libmlt5

```

The following packages will be REMOVED:
  libmlt++3 libmlt6
The following NEW packages will be installed:
  libmlt5

```

But then, because of this, when I try to install python-mlt5, I get:
> sudo apt-get install python-mlt5
```

The following packages have unmet dependencies:
 python-mlt5 : Depends: libmlt++3 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
 
Again, 

> sudo apt-get install libmlt++3
```

The following extra packages will be installed:
  libmlt6
The following packages will be REMOVED:
  libmlt5
The following NEW packages will be installed:
  libmlt++3 libmlt6

```

> sudo apt-get install python-mlt5
```

The following packages have unmet dependencies:
 python-mlt5 : Depends: libmlt5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

>sudo apt-get install libmlt5
```

The following packages will be REMOVED:
  libmlt++3 libmlt6
The following NEW packages will be installed:
  libmlt5

```

INFINITY LOOP! :(

Help please!!
Thanks in advance.

---

### Post by ian-weisser on 2014-09-08
Try installing from the Ubuntu repositories instead of the PPA.
You should also tell the PPA maintainer that they have created a seemingly unresolvable dependency loop.

Here's what mine looks like on 14.04
```
$ apt-cache depends openshot
openshot
  Depends: gtk2-engines-pixbuf
  Depends: fontconfig
  Depends: librsvg2-common
  Depends: melt
  Depends: python-gtk2
  Depends: python-httplib2
  Depends: python-imaging
 |Depends: python-mlt         # Replaces python-mlt2/5, avoids dependency problem
 |Depends: <python-mlt5>   # Not in Ubuntu repos
  Depends: <python-mlt2>   # Not in Ubuntu repos
  Depends: python-pygoocanvas
  Depends: python-xdg
  Depends: python
  Depends: python-support
  Suggests: blender
  Suggests: inkscape
  Recommends: openshot-doc
  Recommends: frei0r-plugins

```

And it installed without problem.

---

### Post by Daniel_Narrias on 2014-09-10
Ok, solved the Problem.

There was a dependency Problem with an other PPA i had already enabled. The package libmlt was already installed but the PPA was disabled.
I thinked that the package would be uninstalled if the PPA were disabled.

---

### Post by ian-weisser on 2014-09-10
> **Daniel_Narrias said:**
> I thinked that the package would be uninstalled if the PPA were disabled.

A repository or PPA is simply a source for a package. Installing/Uninstalling is YOUR decision.

If you disable a PPA, the package remains installed in your system.
The package merely won't be upgraded,

---

