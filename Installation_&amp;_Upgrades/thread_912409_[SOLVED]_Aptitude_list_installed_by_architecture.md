---
title: "[SOLVED] Aptitude list installed by architecture"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by glitch83 on 2008-09-06
Hi all - I'm on a 64-bit Ubuntu install (mad props for making it work so well!) and I was doing some development for building 32 bit packages. I've run low in space and finished the project and would like to clean my system up of all my 32 bit deb packages. Anybody know how to do something similar to "dpkg -l" but with architecture so that I can maybe grep for it or something similar? Any suggestions would be grand!

---

### Post by glitch83 on 2008-09-08
*Bump* - I'm still looking for solution - anybody have one?

---

### Post by glitch83 on 2008-09-09
Figured it out! 
dpkg-query is da bomb - 
```
dpkg-query -W -f='${Package}\t\t${Architecture}\n' | grep 'i386'
```

dpkg-query
-W (list all installed packages with the ability to format the output)
-f=... (format the output)

In this example I put the variable "packagename" followed by some tabs and the architecture it targets. check out the man page for dpkg-query for all the possible output variables.

I then piped the output of that into grep to look for everything that's 32 bit binaries (see the original problem)

viola! Hope this helps someone

---

