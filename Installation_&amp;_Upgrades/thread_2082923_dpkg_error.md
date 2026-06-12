---
title: "dpkg error"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by daniel.cotter on 2012-11-10
Hello,

I get this error trying to install a .deb file I downloaded.  I could say more, but most likely, you will be able to glean from the error verbage what I wanted to do.

```
dpkg --install cackey_0.6.8-1_amd64.deb 
(Reading database ... 185314 files and directories currently installed.)
Unpacking cackey (from cackey_0.6.8-1_amd64.deb) ...
dpkg: error processing cackey_0.6.8-1_amd64.deb (--install):
 unable to create `/usr/lib64/libcackey.so.dpkg-new' (while processing `./usr/lib64/libcackey.so'): No such file or directory
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 cackey_0.6.8-1_amd64.deb
```

My question is, what can I do to get around this error?

You see, I am a CAC card holder, with a need to access DoD websites.  I needed the cackey package, rather than coolkey, because I was having so much trouble configuring it.  But, in all their wisdom, they only make cackey available on a secure site that requires CAC access #catch22.

So, installing 12.10 on a separate partition solved the configuration problems, because it just automatically is all set up.  Too bad 12.10 crashes hard and frequently, so I'm stuck using the nice, stable 12.04, without access to DoD sites.

I booted into 12.10 long enough to download the package, then dragged it over to my 12.04 home folder, and when I try to install it, so that I might have the access I need under 12.04, I get the error pasted above.

So, again, any suggestions to get past this error?

Thanks a bunch,
Daniel

---

### Post by dgharmon on 2012-11-10
> **daniel.cotter said:**
> unable to create `/usr/lib64/libcackey.so.dpkg-new'

Are you running as root, are you out of space?

---

### Post by daniel.cotter on 2012-11-10
well,

I had not installed all the necessary pcscd packages, so i just did so.  I am trying it again after having everything installed.

P.S.:  I was not running as root, but I used the sudo command.
Also, there is plenty of free space on my system.

---

### Post by dgharmon on 2012-11-11
> **daniel.cotter said:**
> well,

I had not installed all the necessary pcscd packages, so i just did so.  I am trying it again after having everything installed.

P.S.:  I was not running as root, but I used the sudo command.
Also, there is plenty of free space on my system.

[Guide for Installing CAC on Ubuntu 12.04]("http://militarycac.com/PDFs/CACKeyUbuntu12.04.pdf")

---

### Post by chrislott on 2012-11-20
The guide (link from @[dgharmon]("http://ubuntuforums.org/member.php?u=1535831")) states that you have to manually create the directory /usr/lib64 before installing the CACKEY package.  Maybe the deb package is messed up.  Did you find that instruction?

---

