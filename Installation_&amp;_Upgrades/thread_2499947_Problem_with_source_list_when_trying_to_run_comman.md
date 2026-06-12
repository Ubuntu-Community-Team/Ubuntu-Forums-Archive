---
title: "Problem with source list when trying to run commands"
date: 2024-08-16
forum: Installation &amp; Upgrades
---

### Post by akoposko6 on 2024-08-16
So first of all before getting into this i want to just say I'm completely new to Linux so bear with me but im not sure what I did or what happened but the only thing i can say that I did that could have caused this is before this started happening is had a couple updates but besides that nothing out of the ordinary but here are a few examples of what Ill type into the command terminal and then the error I get.

```
cb1xxx:~$ sudo apt install geditE: Malformed entry 1 in sources file /etc/apt/sources.list.d/third-party.sources (URI parse)
E: The list of sources could not be read.

```

```
cb1xxx:~$ apt-get update
E: Malformed entry 1 in sources file /etc/apt/sources.list.d/third-party.sources (URI parse)
E: The list of sources could not be read.

```

```
cb1xxx:~$ apt-get source third-party
E: Malformed entry 1 in sources file /etc/apt/sources.list.d/third-party.sources (URI parse)
E: The list of sources could not be read.

```

Whenever I go to the source list and the one thats third-party.sources in the files this is what is in it if it happens to help at all 

```
Types: deb
URIs: cdrom:[Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220)]/
Suites: jammy
Components: main restricted

```

Also once again whenever you are giving your answers keep in mind im relativity new to Linux so if you could dumb down your answers a little that would be very much appreciated thank you

---

### Post by ActionParsnip on 2024-08-16
The file isn't appropriate and should be removed. You can do this with:
```

sudo rm -f /etc/apt/sources.list.d/third-party.sources

```
You can then resume normal use. You can check with:
```

sudo apt update

```
Which should now be smooth

---

### Post by akoposko6 on 2024-08-16
Thanks that worked for me been trying to fix this all day thank you for the quick reply

---

### Post by ActionParsnip on 2024-08-16
No worries. If you have Internet access then you don't need the install media as a source as the repos will more than likely have newer versions.

---

### Post by vuchkov on 2024-11-09
> **ActionParsnip said:**
> The file isn't appropriate and should be removed. You can do this with:
```

sudo rm -f /etc/apt/sources.list.d/third-party.sources

```
You can then resume normal use. You can check with:
```

sudo apt update

```
Which should now be smooth

It works! Thanks a lot.

---

