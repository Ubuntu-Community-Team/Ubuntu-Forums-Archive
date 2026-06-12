---
title: "Problem during update"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by shaquille on 2010-09-30
Hi there, I am facing a disgusting problem. While I am trying to update my system using update manager It downloaded the files and then while it starts installation it shows the following message

```
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
files list file for package 'linux-libc-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover
```

And then nothing occurs.

I had to add that i had been faced a bit different problem earilier. And using the following code I solved that:

```
sudo mv /var/lib/dpkg/updates/0103 /home/shaquille/dpkg_update_0103
```

```
sudo mv /var/lib/dpkg/updates/010 /home/shaquille/dpkg_update_0104
```

```
sudo mv /var/lib/dpkg/updates/0105 /home/shaquille/dpkg_update_0105
```

```
sudo mv /var/lib/dpkg/updates/0106 /home/shaquille/dpkg_update_0106
```

```
sudo mv /var/lib/dpkg/updates/0107 /home/shaquille/dpkg_update_0107
```

```
sudo mv /var/lib/dpkg/updates/0108 /home/shaquille/dpkg_update_0108
```

and then:

```
sudo dpkg --configure -a
```

The problem was solved then.

But now with this problem what can i do?

---

### Post by mörgæs on 2010-10-02
What happens if you boot the machine and run

```
sudo apt-get update
sudo apt-get upgrade
```?

---

