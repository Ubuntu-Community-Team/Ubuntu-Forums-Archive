---
title: "Kpackagekit borked (again)"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ktar on 2009-10-03
If I install something in Kpackagekit, it tells me there has been an unexpected error, then brings up a report option for each of the components that it says haven't installed, and then gives me this error information.

```

Error Type: 
Error Value: "The cache has no package named 'dpkg-exec'"
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1948, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1945, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1907, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 647, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 553, in dispatch_command
self.install_packages(package_ids)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 166, in _unlock_cache_afterwards
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1201, in install_packages
if not self._commit_changes(): return False
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1620, in _commit_changes
PackageKitInstallProgress(self, install_range))
File : /usr/lib/python2.6/dist-packages/apt/cache.py, line 314, in commit
res = self.installArchives(pm, installProgress)
File : /usr/lib/python2.6/dist-packages/apt/cache.py, line 289, in installArchives
res = installProgress.run(pm)
File : /usr/lib/python2.6/dist-packages/apt/progress/__init__.py, line 329, in run
res = self.waitChild()
File : /usr/lib/python2.6/dist-packages/apt/progress/__init__.py, line 298, in waitChild
self.updateInterface()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 398, in updateInterface
apt.progress.InstallProgress.updateInterface(self)
File : /usr/lib/python2.6/dist-packages/apt/progress/__init__.py, line 277, in updateInterface
status_str.strip())
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 372, in statusChange
pkg = self._backend._cache[pkg_name]
File : /usr/lib/python2.6/dist-packages/apt/cache.py, line 142, in __getitem__
raise KeyError('The cache has no package named $r' $ key)

```

But the stupid thing is it does install the package, so why am I getting this? Why does Kpackagekit still suck so badly?

---

### Post by ktar on 2009-10-03
This is the error message box.

[IMG]http://a.imagehost.org/0591/21_4.png[/IMG]

---

### Post by ranch hand on 2009-10-03
I realize that there are a lot of folks excited about packagekit, I am not one of them.  It is used by other OS' and I have used it and do not like it.

I suggest installing synaptic.  Yes, I know it is a gnome (shudder) app.  So was adept at one time.  The main difference between packagekit and sunaptic is that synaptic works.

---

### Post by Slug71 on 2009-10-03
Well im not sure this is Packagekit specific though i could be wrong but i think it has something to do with apt and apport too.

Another thing missing from PK on deb systems at the moment is correct debconf and conf file handling. This is currently in the planning stages so that PK could possibly used as the backend to USC in Karmic +1. 

Maybe USC will be ported to Kubuntu then too.?

Also for KDE 4.4 Kpackage will be replaced with Kpackagekit. This on its own will give much better integration.

So while there is a lot of improvements over the 0.3.x series, there is still a lot to be done. Im hoping we will see debconf in PK in the development 0.5.x series so that it can make the next Ubuntu/Kubuntu release but im sure Sabastien's focus right now is on aptdaemon and Karmic.

---

### Post by NormanFLinux on 2009-10-03
Synaptic is a stable package manager. I run it under Kubuntu with no problems.

---

### Post by Slug71 on 2009-10-03
> **NormanFLinux said:**
> Synaptic is a stable package manager. I run it under Kubuntu with no problems.

Thats not good for dev cycles though. Kinda defeats the purpose.

---

### Post by slakkie on 2009-10-03
Never used it and never will. It only pops ups every once in a while telling me there is some other tool which has the exclusive lock. aptitude ftw.

I just tried to install a package via kpackagekit and I have the same issue. If you open a bug report and post the link I'll confirm the issue for you.

It is already reported: [https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/438279](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/438279)

---

