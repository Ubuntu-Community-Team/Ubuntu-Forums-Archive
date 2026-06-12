---
title: "About gnome-do-plugins"
date: 2009-05-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-05-16
Sorry folks if this isn't the correct place to post, but gnome-do-plugins seem to have some unsolvable dependencies problem in karmic.

> The following packages have unmet dependencies:
  gnome-do-plugins: Depends: libgconf2.24-cil (>= 2.24.0) but it is not going to be installed
                    Depends: libgnome-vfs2.24-cil (>= 2.24.0) but it is not going to be installed
E: Broken packages


Thanks.

---

### Post by 23meg on 2009-05-16
When that happens, [check whether your mirror is up to date]("https://launchpad.net/ubuntu/+archivemirrors"), and if it is, just wait. It's almost always due to dependencies not being built and available at the time you're updating packages (you can check the build status on the Launchpad page corresponding to the source package: [https://launchpad.net/ubuntu/karmic/+source/](https://launchpad.net/ubuntu/karmic/+source/)**source_package_name**/+builds). If it's happening well into the development cycle, and a dependency is consistently in FTBFS (fails to build from source) status, it's worth filing a bug report.

---

### Post by Vanishing on 2009-05-16
Thank you. I will check it out now.

---

### Post by Vanishing on 2009-05-16
I just checked it out, it says the status is published, and I'm using the main server.
This means there is a need of bug report right?

---

### Post by Vanishing on 2009-05-16
The deb file indicates:
To install the following changes are required:
To be removed:
libgnome-vfs2.0-cil
libgnome2.24-cil
gnome-do
libgnomepanel2.24-cil
libgconf2.4-cil
tomboy
To be installed:
libevolution5.0-cil
libgnome-vfs2.24-cil
libgconf2.24-cil

They apparently have a conflict..

---

### Post by 23meg on 2009-05-16
Actually, the i386 build has failed:

[https://launchpad.net/ubuntu/+archive/test-rebuild-20090513/+build/1007428](https://launchpad.net/ubuntu/+archive/test-rebuild-20090513/+build/1007428)

We're [still]("https://wiki.ubuntu.com/KarmicReleaseSchedule") in [a period of automated Debian imports]("https://wiki.ubuntu.com/DebianImportFreeze"), where this kind of transient build failure is commonplace, so it's best to refrain from reporting them manually at this stage. Apport will catch packages that fail to install/upgrade in the update manager and offer to report them anyway, and will do version and duplicate checking too, so that we don't get lots of duplicates and false positives.

---

### Post by Vanishing on 2009-05-16
Oh..sorry, but how did you come up with that page? I got another page saying status:published.
Thanks

---

### Post by 23meg on 2009-05-16
[https://launchpad.net/ubuntu/karmic/+source/gnome-do-plugins](https://launchpad.net/ubuntu/karmic/+source/gnome-do-plugins) -> [click "Show builds"] -> [https://launchpad.net/ubuntu/karmic/+source/gnome-do-plugins/+builds](https://launchpad.net/ubuntu/karmic/+source/gnome-do-plugins/+builds) -> [click the i386 build]

[QUOTE=Vanishing]I got another page saying status published.[/QUOTE]

Could you give me the URL?

---

### Post by Vanishing on 2009-05-16
[https://launchpad.net/ubuntu/karmic/i386/gnome-do-plugins](https://launchpad.net/ubuntu/karmic/i386/gnome-do-plugins)
Maybe I was not thinking right. I thought that status on this page is what you meant before.

---

### Post by 23meg on 2009-05-17
[QUOTE=Vanishing]Maybe I was not thinking right. I thought that status on this page is what you meant before.[/QUOTE]

Right, I had meant the build status for each build.

---

