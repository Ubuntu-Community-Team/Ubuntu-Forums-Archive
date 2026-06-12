---
title: "apt update fails in several ways."
date: 2016-11-09
forum: Installation &amp; Upgrades
---

### Post by agrowcott on 2016-11-09
A week or two ago I installed XUbuntu Xenial. All went well.

The last few days there is a warning icon telling me that  my update information is out of date. The GUI tool was useless, so I tried "apt update".
[B][COLOR=#ff0000]
The first problem I had was that it was trying to contact various hosts using their IPv6 adress and this was simply hanging.[/COLOR][/B]

I know we're all in this trendy new IPv6 world, but it would be best if there was a timeout of a second or so and then it retried using IPv4. Anyway I fixed that by editing /etc/hosts to resolve the addresses to the IPv4 values.

**[COLOR=#ff0000]The second problem I had was missing "Release" files.[/COLOR]**

$> apt update
```
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Ign:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Ign:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                 
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security Release                                            
  Connection failed
Ign:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease                                         
Err:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial Release                      
  Connection failed
Ign:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Err:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial Release
  Connection failed
Err:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates Release
  Connection failed
Err:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports Release
  Connection failed
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.canonical.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```


Does anyone have any ideas how I can get around this issue.

---

### Post by Mark Phelps on 2016-11-10
Yes-  change the mirrors to different ones.

I ran into exactly the same problem and had to change archive.ubuntu.com and archive.canonical.com to other mirrors.

In my case archive.linux.duke.edu was the fastest mirror.

Good Luck

---

### Post by mello-hat89 on 2016-11-10
When updating my machine...I also find this kind of problem...and I try to remove some ppa's that are not in my use anymore. Also, i tried the GUI software updater but still no luck. Could it be just the mirror or other?

---

### Post by Mark Phelps on 2016-11-11
The problem I found is related to the IP version you are running.

Like everyone else in 16.10, I did not know I was using IPV6 by default, and evidently, that has some serious problems with some of the mirrors, a couple being the ones canonical uses.

I thought I'd fixed it by choosing different mirrors, but ended up having to comment out the security and canonical archive mirrors to get Update to finish.

Then, I stumbled across a thread that mentioned that disabling IPV6 would fix it.  I tried that -- and it worked.

So, my suggestion is to search for a thread that talks about editing sysctl.conf -- those are the changes that you need to make.

---

### Post by agrowcott on 2016-11-11
Hi, Mark.

Thanks for the advice. I'll give it a go.


When working on the command line, where do I find a list of mirrors, and how do I select which mirror I wish to use?

---

### Post by agrowcott on 2016-11-11
Turning of IPv6 solves the first problem in a better way - thanks.

The second problem, that of the missing "Release" files is still an issue.

---

### Post by agrowcott on 2016-11-11
Restarting resolveconf worked:

    sudo /etc/init.d/resolvconf restart

---

