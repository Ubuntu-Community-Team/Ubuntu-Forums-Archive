---
title: "Updates manager claims mno web connection"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2013-01-02
Is there a reason for error messages below.  Internet connection is active. Get yahoo, cnn, etc.  This PC hasn't been updated a a couple of months.

John

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.5_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.5_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.5_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.16~exp12ubuntu10.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.16~exp12ubuntu10.5_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.5_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.43+bzr805-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.43+bzr805-0ubuntu5_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu5_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu5_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.43+bzr805-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.43+bzr805-0ubuntu5_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon-data_0.43+bzr805-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon-data_0.43+bzr805-0ubuntu5_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_0.2.8-0ubuntu1.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_0.2.8-0ubuntu1.3_i386.deb) 404  Not Found [IP: 91.189.91.15 80]

---

### Post by Cheesehead on 2013-01-02
The answer to your specific question is "You are getting those 404 error messages because you are not asking for the latest versions of those packages. The older package versions you are asking for have been superseded and removed."

How, exactly, are you updating?
Specifically, are you updating your package lists first? (sudo apt-get update)
Do you have precise-security enabled?

For example, aptdaemon has incremented from 0.43+bzr805-0ubuntu5 to -0ubuntu7 in the precise-security repo.

If you have the -security repo enabled,
and if you update package lists (or run System Updater, which does it automatically),
then the increment will be noticed by the package manager and the update will be downloaded and installed.

---

### Post by cigtoxdoc on 2013-01-03
A couple of notes. 

This PC was last updated about a month ago and had been out-of-service since last evening.

I did sudo apt-get update twice, and the problem went away.

Was this the solution?

John

---

### Post by Cheesehead on 2013-01-04
That was exactly the right solution.
Well done!

---

