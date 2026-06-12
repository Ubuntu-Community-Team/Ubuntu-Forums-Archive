---
title: "Error when updating package list.."
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by python.noob on 2010-06-14
Following are the error details..
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C174A7B143CBFCC0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CE90D8983E731F79

Any help..

---

### Post by python.noob on 2010-06-15
Have i posted in the wrong section?? After two days .. no reply..:confused::confused:

---

### Post by plucky on 2010-06-15
See [Here](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)


Or in a terminal,copy and paste each line
```
gpg --keyserver keyserver.ubuntu.com --recv C174A7B143CBFCC0
gpg --export --armor C174A7B143CBFCC0 | sudo apt-key add -
```

and

```
gpg --keyserver keyserver.ubuntu.com --recv CE90D8983E731F79
gpg --export --armor CE90D8983E731F79 | sudo apt-key add -
```


Good Luck

---

### Post by python.noob on 2010-06-19
> **plucky said:**
> See [Here]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304")


Or in a terminal,copy and paste each line
```
gpg --keyserver keyserver.ubuntu.com --recv C174A7B143CBFCC0
```

The error is..
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/lucie/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

Please help me..

---

