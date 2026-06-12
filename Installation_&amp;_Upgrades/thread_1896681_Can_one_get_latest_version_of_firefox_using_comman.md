---
title: "Can one get latest version of firefox using command &quot;sudo apt-get upgrade&quot;?"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by newhere_m on 2011-12-17
Is it possible to get the latest version of firefox by using the commands "sudo apt-get update && sudo apt-get upgrade"? I am using ubuntu 10.04 LTS-2. If it is not possible then what is the correct way to get the latest version of firefox?

---

### Post by cwklinuxguy on 2011-12-17
It is POSSIBLE, but I think the repos usually are a version or so behind (they don't update when Firefox does). So probably the best way to get the latest is to download the tarball from Mozilla's website.

---

### Post by Paddy Landau on 2011-12-17
Generally, an Ubuntu version has a "version freeze" for stability.

If you want to get the latest version, there are a few ways to do it. I know of three.


[LIST=1]
[*]Go to [Mozilla's website]("http://www.mozilla.org/") and download. Unfortunately, it's not a .deb version, which makes it difficult; also, you won't get further updates.
[*]Add the [Firefox PPA]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable") to your system (using Software Sources is the easiest way), and refresh the repository. This will always give you the latest stable version.
[*]Open Software Sources > Updates > check Unsupported updates. This will give you the latest approved version for the latest Ubuntu version (even if you use a prior one such as 10.04) -- but that applies to *all* programs, not just Firefox, and could lead to some system instability.
[/LIST]


In your case, I would recommend option 2.

---

### Post by lovinglinux on 2011-12-18
See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247) sticky.

---

