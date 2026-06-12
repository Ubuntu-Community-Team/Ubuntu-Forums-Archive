---
title: "How to redownload installed packages"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by chumakm on 2007-09-18
Hello!

I cleaned the /var/cache/apt/archives via aptitude clean. How can i redownload installed packages,  but without standard packages, that included into ubuntu-desktop?

Thanks.

---

### Post by jnorth on 2007-09-18
Something like this maybe?  Let me know if I'm not understanding your question correctly.

Ripped from [https://answers.launchpad.net/ubuntu/+question/5435]("https://answers.launchpad.net/ubuntu/+question/5435")

Notes.
1.  Read through what this is doing first, copy and paste at your own risk.  Though it probably won't damage your system, it may not be doing what you want it to do.
2.  You need to apt-get install apt-show-versions first for this to work.
3.  This isn't really the best way to do this.  A better way would be to do a dpkg -l and use grep/sed to get a space-delimited list of installed package names.  Then just do an apt-get -d `cat package_list` to download only and rebuild your package cache.  I'm just not good enough with sed to whip something up unfortunately.

```
ALL='apt-show-versions | sed '{s/[\/ ].*//}' | wc -l`; I=0; for P in `apt-show-versions | sed '{s/[\/ ].*//}'`; do let I=I+1; echo; echo " Downloading $P ($I/$ALL)" ; apt-get -dy --force-yes install $P ; done
```

---

### Post by chumakm on 2007-09-19
Thank you for your answer. I reviewed some posts here and find the way to redownload a hole packages... 

This is a thread [http://ubuntuforums.org/showthread.php?t=97566](http://ubuntuforums.org/showthread.php?t=97566) and there is solution

dpkg --get-selections \* | grep install | grep -v deinstall | sed -e "s/\s.*$//" | sed 's/^/sudo apt-get install --reinstall --download-only -y -q /g' | sh | tee progress.log

I do by this way, ie, download all installed packages. In my case they are near 800 MB.

I don't find the method to get packages list from standard install, but it's possible get needed packages from package cache on another computer (if has it).

---

