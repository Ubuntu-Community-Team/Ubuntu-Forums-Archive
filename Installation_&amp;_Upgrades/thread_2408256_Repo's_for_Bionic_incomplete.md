---
title: "Repo's for Bionic incomplete?"
date: 2018-12-16
forum: Installation &amp; Upgrades
---

### Post by frankvw on 2018-12-16
Lately I've been having the following problem on Bionic more and more often:

```
$ [program name]

Command [program name]' not found, but can be installed with:
sudo apt install [package name]

$sudo apt install [package name]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package [package name]

```

And this doesn't occur only with exotic or third-party stuff. E.g.:

```

$ spell

Command 'spell' not found, but can be installed with:

sudo apt install spell

$ sudo apt install spell

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package spell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'spell' has no installation candidate
```

A "sudo apt update" does not fix the problem. I'm downloading from the "main server" but switching servers doesn't help, either.

So I'm confused. I can understand packages being discontinued in the latest repo's, but then why do I keep getting the suggestion to install it from those repo's? Can anyone tell me what's going on here?

Tnx!

---

### Post by howefield on 2018-12-16
Assuming the above is actual terminal output, [package name] probably shouldn't have brackets around it, the error could hardly be more explicit, it cant find a package by that name.

---

### Post by Impavidus on 2018-12-16
Maybe something wrong with your repositories. spell should be available:```
$ apt-cache policy spell
spell:
  Installed: (none)
  Candidate: 1.0-24build1
  Version table:
     1.0-24build1 500
        500 http://nl.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
```Is the universe repository enabled? It ought to be by default, but maybe not on your box.```
cat /etc/apt/sources.list
```

---

### Post by frankvw on 2018-12-18
> **howefield said:**
> Assuming the above is actual terminal output, [package name] probably shouldn't have brackets around it, the error could hardly be more explicit, it cant find a package by that name.

I'm not using brackets, those are just to denote the package name. See actual terminal output for spell.

---

### Post by frankvw on 2018-12-18
OK. I'm in South Africa; maybe that's part of the problem. I set up an SSH proxy tunnel to a Linux box in the Netherlands and piped everything through there, and now it works. Don't ask me how but it's obviously an artefact of local Internet conditions. ISPs here do atrocious things (such as using reverse proxies that take 24 hours or more for website updates to reflect) so everything's possible, I suppose.

---

