---
title: "Update Problems with Fedora"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by spacelad101 on 2010-03-13
Ok, I just installed Fedora as kubuntu was not working for me and i am now trying to get bug updates, program updates, etc and there are like 400 of them totaling just over 300MB and when i go to update everything it requires me to install some programs for the update to proceed, i went to install the programs and now im getting this error message everytime i try. "An Internal System Error Has Occurred" these are the details of the error message.

 Error Type: <class 'yum.Errors.RepoError'>
Error Value: Error getting repository data for installed, repository not found
  File : /usr/share/PackageKit/helpers/yum/yumBackend.py, line 3125, in <module>
    main()
  File : /usr/share/PackageKit/helpers/yum/yumBackend.py, line 3122, in main
    backend.dispatcher(sys.argv[1:])
  File : /usr/lib/python2.6/site-packages/packagekit/backend.py, line 710, in dispatcher
    self.dispatch_command(args[0], args[1:])
  File : /usr/lib/python2.6/site-packages/packagekit/backend.py, line 657, in dispatch_command
    self.update_packages(only_trusted, package_ids)
  File : /usr/share/PackageKit/helpers/yum/yumBackend.py, line 1948, in update_packages
    signed = self._is_package_repo_signed(pkg)
  File : /usr/share/PackageKit/helpers/yum/yumBackend.py, line 1437, in _is_package_repo_signed
    repo = self.yumbase.repos.getRepo(pkg.repoid)
  File : /usr/lib/python2.6/site-packages/yum/repos.py, line 121, in getRepo
    'Error getting repository data for $s, repository not found' $ (repoid)

Please, if you know can you let me know whats wrong and how to resolve this issue.
Thanks In Advance :D

---

### Post by d3v1150m471c on 2010-03-13
Can you tell me how to install a corvette engine in a volkswagen beetle?

---

### Post by spacelad101 on 2010-03-13
what does that have to do with my problem???

---

### Post by Simian Man on 2010-03-13
It sounds like either yum has become corrupted or you have removed some of the update repos somehow.  Post the out put of the following commands please:
```

su -
yum clean all
yum update

```
Which will try to reset yum and then do the update.


And (if that doesn't work):
```

cat /etc/yum.repos.d/*.repo

```
Which will show all of your repository info.

---

### Post by d3v1150m471c on 2010-03-13
> **spacelad101 said:**
> what does that have to do with my problem???

Glad you asked. What does fedora have to do with ubuntu?

---

### Post by spacelad101 on 2010-03-13
you do make a interesting point but someone was able to help unlike you, just because you think this should not be here it does not mean you should access the fourm and just post useless stuff, and thank you [Simian Man]("http://ubuntuforums.org/member.php?u=481510") for the help, it worked =)

---

### Post by d3v1150m471c on 2010-03-13
It shouldn't be here. "Installation & Upgrades
For questions about upgrading and installation of your [COLOR="DarkRed"]**new Ubuntu OS**[/COLOR]."

Speaking of useless stuff, fedora isn't ubuntu.

---

### Post by Simian Man on 2010-03-14
I'm glad you got it sorted out :).

@d3v1150m471c:
Sure Fedora isn't what this forum is about, and he may have been better served at the Fedora forums, but technical questions about another Linux flavor are a hell of a lot closer to what this forum is for than all the garbage in the Cafe.  So if you've taken it upon yourself to eradicate "uselessness" here, you should start some place else.

Besides Linux's are all very much the same, so many people prefer better distros but hang around here to assist other Linux users anyway.

---

### Post by Barriehie on 2010-03-16
> **simian man said:**
> i'm glad you got it sorted out :).

@d3v1150m471c:
Sure fedora isn't what this forum is about, and he may have been better served at the fedora forums, but technical questions about another linux flavor are a hell of a lot closer to what this forum is for than all the garbage in the cafe.  So if you've taken it upon yourself to eradicate "uselessness" here, you should start some place else.

Besides linux's are all very much the same, so many people prefer better distros but hang around here to assist other linux users anyway.

+1

---

