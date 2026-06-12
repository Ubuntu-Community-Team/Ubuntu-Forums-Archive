---
title: "apt-get error"
date: 2018-01-07
forum: Installation &amp; Upgrades
---

### Post by nauanalima on 2018-01-07
I'm getting the following error:
[COLOR=#b22222]
N: Ignoring file 'sp' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/COLOR]

when I run the commands **sudo apt-get** update and **sudo apt-get** upgrade

It doesn't seem to be affecting my machine directly, but I would like to  clear up the issue before it has a chance to develop into something  worse.

EDIT: solved!

---

### Post by howefield on 2018-01-07
What is the output from..

```
ls /etc/apt/sources.list.d/
```

---

### Post by nauanalima on 2018-01-07
> **howefield said:**
> What is the output from..

```
ls /etc/apt/sources.list.d/
```


nauana@GlaDOS:~$ ls /etc/apt/sources.list.d/
sp          spotify.list.save                  vajdics-netbeans-installer-trusty.list.save  webupd8team-java-trusty.list.save
spotify.list  vajdics-netbeans-installer-trusty.list  webupd8team-java-trusty.list

---

### Post by howefield on 2018-01-07
Does the sp file contain anything ?

```
cat /etc/apt/sources.list.d/sp
```

If it is empty you could delete it, or move it to your Documents folder if you want to save a copy.

```
sudo mv /etc/apt/sources.list.d/sp ~/Documents/
```

---

### Post by nauanalima on 2018-01-07
> **howefield said:**
> Does the sp file contain anything ?

```
cat /etc/apt/sources.list.d/sp
```

If it is empty you could delete it, or move it to your Documents folder if you want to save a copy.

```
sudo mv /etc/apt/sources.list.d/sp ~/Documents/
```

Done with that problem, but I still have these warnings:

W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages)

What can I do?

---

### Post by ian-weisser on 2018-01-07
Locate and delete one of the duplicates in sources.list.
Why do you have both 32-bit and 64-bit sources listed?

---

### Post by nauanalima on 2018-01-07
> **ian-weisser said:**
> Locate and delete one of the duplicates in sources.list.
Why do you have both 32-bit and 64-bit sources listed?

I was trying to install Spotify but neither of the two versions worked. :(

---

### Post by nauanalima on 2018-01-07
Thank you very much, guys!

---

### Post by deadflowr on 2018-01-07
For what it's worth you can forego the spotify repository now and instead install the snap package for it:
[https://insights.ubuntu.com/2017/12/20/canonical-welcome-spotify-as-a-snap-for-linux-users/]("https://insights.ubuntu.com/2017/12/20/canonical-welcome-spotify-as-a-snap-for-linux-users/")

You can also go ahead and mark this thread as solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

