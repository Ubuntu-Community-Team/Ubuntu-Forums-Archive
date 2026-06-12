---
title: "Apt broken after failed .deb installation"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by Gordon_Ellis on 2014-01-18
Last week, I downloaded a .deb file for an old (REALLY old) version of libstdc++ to run a Return to Castle Wolfenstein dedicated server, and tried to install it using dpkg -i. However, it failed and I figured I'd get back to it later. Now, when I try to update the system with apt-get, it doesn't work and only says it is unable to find the libstdc++ files.
```
admin@server:~$ sudo apt-get update
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
admin@server:~$
```

I tried apt-internal-solver on a whim, but that yields the same issue.
```
admin@server:~$ sudo apt-internal-solver
apt-internal-solver: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-internal-solver: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
admin@server:~$
```

I tried removing the bad package with dpkg, to no avail
```
admin@server:~$ sudo dpkg --remove --force-remove-reinstreq libstdc++
dpkg: warning: there's no installed package matching libstdc++
admin@server:~$
```

All of these errors still exist even after rebooting
Any help on the topic is greatly appreciated, because this problem stops me from updating or installing anything new to the system.

---

### Post by deadflowr on 2014-01-18
try unistalling using the whole package name
```
sudo dpkg --remove libstdc++-the-rest-of-the-package-name
```
or you might try
```
sudo dpkg --remove libstdc++*
```
the * symbol will replace everything that's suppose to be after the ++.
Be warned if you have other libstdc++ packages they would be listed as well.

I don't know which version of Ubuntu you are running, but you can get the package from here
[http://packages.ubuntu.com/search?suite=precise&keywords=libstdc%2B%2B](http://packages.ubuntu.com/search?suite=precise&keywords=libstdc%2B%2B)

It's a core package so it's in the main repo, if that helps.
I'm running precise, so for reference, the package I have is libstdc++6 version 4.6.3-1ubuntu5.

From the link you would find the one for the Ubuntu version you have and open it, then scroll the bottom of the page and then download the package.(it'll list an amd64, and an i386 package. The amd64 is for 64-bit and the i386 is for 32-bit)

It would be easier to post which version of Ubuntu you are running, so as we can link you to the absolute right version.

---

### Post by tylerwilsonthefirst on 2014-01-19
Hello, I'm the other admin on the server, its running 12.04.3.

---

### Post by deadflowr on 2014-01-19
Here then
[http://packages.ubuntu.com/precise/libstdc++6](http://packages.ubuntu.com/precise/libstdc++6)

Click on the link for the version. amd64 or i386.
This will move you to a page with a list of mirrors, where you can get the package.
It might warn of that the package is untrusted. No worries, simple click ok.
Once downloaded try
```
cd Downloads
sudo dpkg -i the full name of the deb package
```

I'm not sure of the full name, in cases like this I use tab completion to complete the name correctly.
Make sure though to include the .deb part.
once it's installed, see if apt works correctly again.
I would run
```
sudo apt-get update
```
You may need to run
```
sudo dpkg --configure -a
```
Hope it helps

---

### Post by Gordon_Ellis on 2014-01-20
Thank you so much! This completely solved the problem and saved us hours and hours of headache.

---

### Post by deadflowr on 2014-01-20
well, at least that issue seems to have been resolved.
+1 to that.


I would suggest maybe starting a thread(probably in the gaming and leisure subforum section) to see if anyone can help get that server up and running as you would like it to be.
Maybe somebody knows a quick trick or two that can workaround the problems you have/had/having with it.

Good Luck, in any case.

---

### Post by Gordon_Ellis on 2014-01-22
The strange thing is that I have an identical setup running on another server without any issues :/
I'll probably find out I got a package for the wrong architecture or something

Thanks again for your help! :D

---

