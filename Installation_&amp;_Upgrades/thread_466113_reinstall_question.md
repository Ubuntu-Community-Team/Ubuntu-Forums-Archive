---
title: "reinstall question"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2007-06-06
Hello

After having a power surge last night, my machine went wonky, so I had to do a fresh install of Feisty, afterwhich the inital problem of not being able to connect to internet still occurred. i finally got the tech guy at newwave cable to help me to restart my modem
/sbin/ifconfig
and all seemed to be fine, the install proceeded to down load an hours woth of files etc.......

today i am getting this error, i asked this over at another area, but so far no reply back

the error is always some variation of:
var/lib/apt/lists/security.ubuntu.com-ubuntu_dists_feisty-security_restricted_binary_i386_packages/var

can someone tell me, do i need to find this ^ file mentioned above and download it myself? IF so, how do i locate it? by the whole file name above or some variation?
i keep seeing that this missing security file comes up a ton today for me

thank you

---

### Post by taurus on 2007-06-06
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

