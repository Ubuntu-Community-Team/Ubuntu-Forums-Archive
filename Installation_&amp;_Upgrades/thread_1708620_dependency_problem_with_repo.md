---
title: "dependency problem with repo"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by tanveer on 2011-03-16
Hi all
I need some help on resolving the dependency error problem. Now-a-days its lot more easy to install anything as yum/apt-get takes care of the dependencies by themselves. 
Now say if I want to install **openssh **in traditional way with ./configure then make and make install it works fine in Fedora but not in Ubuntu as it gives error for a Mailer program when ran ./configure as sendmail is by default installed in Fedora but not in Ubuntu. 
What I need to know is there any way to resolve the dependency problem from the error automatically? For start is there any file in ubuntu which lists all the packages along with their dependencies?
Thank you.

---

### Post by wojox on 2011-03-16
Graphically you can do a [Ubuntu Packages Search]("http://packages.ubuntu.com/")

From the command line 

```
sudo apt-cache show openssh-server
```

---

### Post by tanveer on 2011-03-17
Thanks for your reply. 
I am actually looking for the file or technique that apt-get uses to resolve the dependency problem.

---

### Post by tanveer on 2011-03-19
Hi wojox, from where it's fetching all the information using the command
[PHP]sudo apt-cache show openssh-server
[/PHP] 
Is it from internet or from my machine somewhere it's stored? I am actually after that.
And what is the difference between Depends,Recommends and Suggests?

[PHP]Depends: libc6 (>= 2.8), libcomerr2 (>= 1.01), libgssapi-krb5-2 (>= 1.8+dfsg), libkrb5-3 (>= 1.6.dfsg.2), libpam0g (>= 0.99.7.1), libselinux1 (>= 1.32), libssl0.9.8 (>= 0.9.8m-1), libwrap0 (>= 7.6-4~), zlib1g (>= 1:1.1.4), debconf (>= 1.2.0) | debconf-2.0, openssh-client (= 1:5.5p1-4ubuntu4), upstart-job, libpam-runtime (>= 0.76-14), libpam-modules (>= 0.72-9), adduser (>= 3.9), dpkg (>= 1.9.0), lsb-base (>= 3.2-13), procps
Recommends: xauth
Suggests: ssh-askpass, rssh, molly-guard, openssh-blacklist, openssh-blacklist-extra, ufw
Conflicts: rsh-client (<< 0.16.1-1), sftp, ssh (<< 1:3.8.1p1-9), ssh-import, ssh-krb5 (<< 1:4.3p2-7), ssh-nonfree (<< 2), ssh-socks, ssh2
Filename: pool/main/o/openssh/openssh-server_5.5p1-4ubuntu4_amd64.deb[/PHP]

---

