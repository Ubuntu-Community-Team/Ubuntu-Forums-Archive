---
title: "Upgrade issues"
date: 2020-01-13
forum: Installation &amp; Upgrades
---

### Post by rishrules on 2020-01-13
A friend recently gave me a Dell XPS-13-9360 with 7th gen Intel Core 64 bit with 2.50GHz × 4 and an Intel Kayblake graphics card.  Having installed mirrors into various machines for years it excited me to receive a machine with 16.04 factory installed!  I figured upgrading would prove a cinch!  Not so much.  It looked at first blush the laptop couldn't find the right public key, much less the right libraries.  I kept getting the following - 

```

W:GPG error:[http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The followingsignatures couldn't be verified because the public key is notavailable: NO_PUBKEY 6494C6D6997C215E, W:The repository'http://dl.google.com/linux/chrome/deb stable Release' is notsigned., W:Data from such a repository can't be authenticated and istherefore potentially dangerous to use., W:See apt-secure(8) manpagefor repository creation and user configuration details., W:There isno public key available for the following key IDs:
6494C6D6997C215E  ,E:Problem executing scripts APT::Update::Post-Invoke-Success 'if/usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli;then appstreamcli refresh > /dev/null; fi', E:Sub-process returnedan error code
```.   I checked the LinuxMint[https://forums.linuxmint.com/viewtopic.php?f=42&p=1351074#p1350799](https://forums.linuxmint.com/viewtopic.php?f=42&p=1351074#p1350799)and tried their apt-get update suggestion.  The add command seemed towork.  It tells me &#8220;ok&#8221;.  So I appear to have found the keys.  But the update fails.  First there&#8217;sthe report ```
*** Error in `appstreamcli': double free or corruption(fasttop): 0x00000000014dd430 *** 
``` Shell runs a backtrace, thenstarts a memory map.  After a long string of files it says ```
aborted &#8211;core dumped.  E: Problem executingscriptsAPT::Update::Post-Invoke-Success 'if /usr/bin/test -w/var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamclirefresh > /dev/null; fi'
``` 
Upgrading this factory install isn't quite so simple - I look forward to your insight!

---

### Post by rsteinmetz70112 on 2020-01-14
The post really should be a new post in a new thread where it will be more visible. 

I've requested the moderators create a new Thread with this post. 

If they don't I'd suggest you repost it as a new thread and add some code tags and newlines or returns.

It would help if you could describe how you attempted to upgrade the computer. the quick and dirty would be:

```
sudo apt update
sudo apt full-upgrade
do-release-upgrade
```

However since you acquired the machine in unknown condition there may will be problems with the existing installation.

---

### Post by QIII on 2020-01-14
Moved to its own thread.  Please to not hijack the threads of other users.  It muddies the water and keeps the OP and you from getting the individual attention you need for your issues.

Please also use code tags to enclose terminal commands and their output.


Are you running Mint or Ubuntu?

---

### Post by rsteinmetz70112 on 2020-01-14
As mentioned above we need more information. some of the information you posted does not make sense to me.
> [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb)
is not a directory I would expect Ubuntu to use.
You also mention Mint in passing. 
Mint is based on Ubuntu, but is different from it, so if that is what is installed then you should look for help with Mint.  
The 18 series of releases are based on Ubuntu 16.04 and are supported until 2021. 
The 19 series is also out and supported until 2023.

---

