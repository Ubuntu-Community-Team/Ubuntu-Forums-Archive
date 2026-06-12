---
title: "Change default folders to custom names or folders on other partitions"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by mat14 on 2015-01-22
I wanted to change the Ubuntu 14.04 standard folders located in "Home" ("Music", "Images", "Download"...) to another partition, since my default document-partition is ntfs shared with Windows 7 and I was tired of looking the folders up up manually or having the downloaded files in the wrong folder all the time.

I came across several threads adressing the issue, mostly via terminal and modifying files manually like

```
[FONT=Ubuntu Mono]gedit ~/.config/user-dirs.dirs[/FONT]
```

(see [http://askubuntu.com/questions/67044/change-default-user-folders-path](http://askubuntu.com/questions/67044/change-default-user-folders-path))

but it seemed not to be so simple when You want to link to another drive or partition.

After much reading I found a page ([http://forum.ubuntu-it.org/viewtopic.php?f=43&t=578189](http://forum.ubuntu-it.org/viewtopic.php?f=43&t=578189)) suggesting to use the program Ubuntu Tweak, a solution that worked for me and I just wanted to share with the non-Italian speaking community

In short it works like this:

```
[COLOR=#555555][FONT=Monaco]sudo add-apt-repository ppa:tualatrix/ppa[/FONT][/COLOR]
```

```
[COLOR=#555555][FONT=Monaco]sudo apt-get update[/FONT][/COLOR]
```

```
[COLOR=#555555][FONT=Monaco]sudo apt-get install ubuntu-tweak[/FONT][/COLOR]
```

then launch the program and use the various tweaks.

---

### Post by 33Nicolas on 2015-02-02
That's funny, I saw Ubuntu Tweaks for the first time on my Mint laptop last night. Thanks, installing it and trying to find where it is.

---

