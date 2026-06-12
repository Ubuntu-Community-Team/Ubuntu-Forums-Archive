---
title: "Ubuntu Server 14.04 openssh update error"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by adam.vadala_roth on 2015-09-15
Hello,
I have been having a very hard time fixing this problem with my server running Ubuntu Server 14.04. It started when apt-get upgrade was hanging when attemping to update openssh, something about a directory not being able to be locked. I tried rebooting then running sudo apt-get update && apt-get upgrade and it still hung on the same errror. I decided to remove openssh and attempt to install it fresh but I got the same error. So after battling with this for over a week I thought I'd start from scratch and post here. 

So here we go, when I attempt to install openssh-server with the following command:

```
sudo apt-get install openssh-server
```

I get 

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:6.6p1-2ubuntu2.3)
 openssh-sftp-server : Depends: openssh-client
 ssh-import-id : Depends: openssh-client
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Now when I run 
```
sudo apt-get -f install
```

It fails because of the following errors:

```
dpkg: error processing archive /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.3_amd64.deb (--unpack):
 unable to make backup link of './usr/bin/ssh' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any idea how to fix this ? I looked at many forum posts from users who had similar problems but nothing I try seems to work.

---

### Post by matt_symes on 2015-09-15
Hi

Can you post the output of

```
lsattr /usr/bin/ssh
```

Kind regards

---

### Post by adam.vadala_roth on 2015-09-15
> **matt_symes said:**
> Hi

Can you post the output of

```
lsattr /usr/bin/ssh
```

Kind regards

Hey thanks for getting back!! I actually just discovered that fix and it worked!!! This is what I did in case anyone is wondering

First get root:

```
sudo su
```

Next I did
```
lsattr /usr/bin/ssh
```

found that it had the ia in there, then I removed them:

```

[COLOR=#000000][FONT=Courier New]*chattr -i /usr/bin/ssh *[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New][I]chattr -a /usr/bin/ssh
[/I][/FONT][/COLOR]
```

Next I fixed dependencies

```
apt-get -f install
```

Installed Openssh-client
```
apt-get install openssh-client
```

Next I did
```
lsattr /usr/sbin/sshd
```

found that it had the ia in there, then I removed them:

```

[COLOR=#000000][FONT=Courier New]*chattr -i /usr/sbin/sshd *[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New][I]chattr -a /usr/sbin/sshd
[/I][/FONT][/COLOR]
```

Update aptitude

```
apt-get update
```

Installed Openssh-client
```
apt-get install openssh-server
```

Now I'm back in business!!!

---

