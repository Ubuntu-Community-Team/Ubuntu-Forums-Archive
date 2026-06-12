---
title: "How do I reset the package manager?"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by fbarcenas on 2007-01-31
I had a failed installation of a package that the system won't let me uninstall. Therefore I can't install or remove any software untill I fix this problem.

I've tried "sudo dpkg install -f¨
"sudo aptitude install -f¨
"sudo dpkg remove¨
"sudo apt-get install -f¨

and everything under the sun that I could think of. 
I there some work/temp directory that the package manager uses that I might delete, that would reset the package manager? 

I'm so frustrated I'm thinking about reinstalling Ubuntu. 

The package was from another distro. I mistakenly tried to install a package from debian.com instead of packages.ubuntu.com

How can I fix this?

---

### Post by p!=f on 2007-01-31
You may also try 
```

sudo dpkg -P <package>

```
Please, post the error you get here then it will be easier to help. :)
Next, post the output of
```

dpkg -l | grep -v ^ii

```

---

