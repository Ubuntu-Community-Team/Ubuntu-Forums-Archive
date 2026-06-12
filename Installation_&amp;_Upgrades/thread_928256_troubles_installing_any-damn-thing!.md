---
title: "troubles installing any-damn-thing!"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by coolethan on 2008-09-23
i have been unsuccessfull installing anything onto my ubuntu OS for as long as i've had it which is about 4 or 5 months and so eventually i just gave up and stopped using the computer because i couldn't get anything to install and therefor it was worthless to me. my computer isn't conected to the internet so i have had to download files to an external hard drive and then transport them to the computer to install them. when i double click on the package in opens up the package installer but no matter what kind of file i downlaod (amd64,i836 or powerpc) it either gives me a wrong architecture error or one that says that the dependency is not satisfied or something to that effect. the computer will be designated for one task only and i only need to install one program. what do i do?

---

### Post by aysiu on 2008-09-24
If you type this in [the terminal](http://www.psychocats.net/ubuntu/terminal), the output should tell you what architecture you have: ```
uname -m
```

Maybe you can use a live CD on your internet-connected computer and then copy the /var/cache/apt/archives contents to the external drive?

I've heard good things about AptonCD, too, though I've never used it.

---

