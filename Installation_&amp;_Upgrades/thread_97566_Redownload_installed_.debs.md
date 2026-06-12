---
title: "Redownload installed .debs"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by g2devi on 2005-12-01
My current computer was upgraded from Warty to Hoary to Breezy, and I cleared my apt cache a few times in the process so I have no history of what packages were installed. Is there a way to redownload (but not reinstall) all the debs on my system?

The reason I'm asking is I've installed Breezy on a new test computer that doesn't have network access and I'd like to copy the installed debs from my computer to this test computer and turn that debs copy into a local repository for the test computer.

---

### Post by bwog on 2005-12-01
Perhaps you the info in here is of use: [http://ubuntuforums.org/showthread.php?t=94727](http://ubuntuforums.org/showthread.php?t=94727) and [http://ubuntuforums.org/showthread.php?t=94050&highlight=dial](http://ubuntuforums.org/showthread.php?t=94050&highlight=dial)

---

### Post by g2devi on 2005-12-01
Thanks for the links.

Unfortunately, it's not quite what I need. I want to download the deb packages that are installed on my main computer, so that they can be used on the test machine. I don't want to download all the main/.../multiverse repositories, because my test machine won't need most of them. They'll only need reference to what I'm already using.

I'm hoping there's a better way (since I think this situation must be a fairly common problem for people without an easy internet connection), but after some searching, I'm thinking that I need to write a script like the following:

get a list of all installed packages on my main computer
for each packages in that list, download but not install that package into the apt cache
make a repository out of those packages and copy it to my test machine

---

### Post by ow50 on 2005-12-01
Some hints that might help you when writing that script.

[QUOTE=g2devi]get a list of all installed packages on my main computer[/QUOTE]
```
dpkg --get-selections \* | grep install | grep -v deinstall | sed -e "s/\s.*//"
```

[QUOTE=g2devi]for each packages in that list, download but not install that package into the apt cache[/QUOTE]
```
sudo apt-get install --reinstall --download-only <package name>
```

[QUOTE=g2devi]make a repository out of those packages and copy it to my test machine[/QUOTE]
I don't think you necessarily need a repository. Just copy the packages from one computer's /var/cache/apt/archives to another. Also you might need to check that there's no max size limit set for the apt cache.

Also, check [this](http://www.ubuntuforums.org/showthread.php?t=33530) thread.

---

### Post by g2devi on 2005-12-02
[QUOTE=ow50]Some hints that might help you when writing that script.
[/QUOTE]

Thanks! They really helped. Here's the script/command line I used in case anyone needs it:

[INDENT]dpkg --get-selections \* | grep install | grep -v deinstall | sed -e "s/\s.*$//" | sed 's/^/sudo apt-get install --reinstall --download-only -y -q  /g' | sh | tee progress.log
[/INDENT]


[QUOTE=ow50]Also, check [this](http://www.ubuntuforums.org/showthread.php?t=33530) thread.[/QUOTE]

I didn't plan on exactly mirroring my system (just the installed repositories), but this link is a keeper. Thanks.

---

