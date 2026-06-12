---
title: "firefox xenial installed from the site blocks security updates and ppa"
date: 2018-08-30
forum: MINT
---

### Post by Joleen on 2018-08-30
Hi dear friends! Today I celebrate my anniversary of ten years with linux!
I run Iinux mint sarah 18 on a lenovo laptop -very bad choice I made  years ago by the way, stay away from lenovo. just installed firefox xenial -downloaded the package from official firefox site and run the executable file-
and now this happens when I try to update --I particularly would like your opinion on how xenial messes up tor ppa. I thought they where different. --see last lines--
```
 maria@bossmachined ~ $ sudo apt-get update
[sudo] password for maria: 
Err:1 http://archive.canonical.com/ubuntu xenial InRelease
  Temporary failure resolving 'archive.canonical.com'
Err:2 http://packages.linuxmint.com sarah InRelease
  Temporary failure resolving 'packages.linuxmint.com'
Err:3 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:4 http://repo.vivaldi.com/stable/deb stable InRelease
  Temporary failure resolving 'repo.vivaldi.com'
Err:5 http://archive.ubuntu.com/ubuntu xenial InRelease                        
  Temporary failure resolving 'archive.ubuntu.com'
Err:6 http://dl.google.com/linux/chrome/deb stable InRelease                   
  Temporary failure resolving 'dl.google.com'
Err:7 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial InRelease
  Temporary failure resolving 'ppa.launchpad.net'
Err:8 https://repo.skype.com/deb stable InRelease
  Could not resolve host: repo.skype.com
Err:9 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:10 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  Temporary failure resolving 'dl.google.com'
W: Failed to fetch http://packages.linuxmint.com/dists/sarah/InRelease  Temporary failure resolving 'packages.linuxmint.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'archive.canonical.com'
W: Failed to fetch https://repo.skype.com/deb/dists/stable/InRelease  Could not resolve host: repo.skype.com
W: Failed to fetch http://repo.vivaldi.com/stable/deb/dists/stable/InRelease  Temporary failure resolving 'repo.vivaldi.com'
W: Failed to fetch http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'ppa.launchpad.net'
W: Some index files failed to download. They have been ignored, or old ones used instead. 
```
thanks a lot for any help.

---

### Post by howefield on 2018-08-30
Thread moved to the "*MINT*" forum.

---

### Post by ajgreeny on 2018-08-30
Why did you install firefox direct from the mozilla site and not from the Mint repos using whatever software installer Mint uses?

I also wonder why you needed to install firefox at all; from my memories of Mint from some years ago it used firefox as the default browser; has that changed to something else such as chromium in recent versions of Mint?

---

### Post by Joleen on 2018-08-30
firefox told me it needed an update -and I believed it, since it was crushing all the time-, and redirected me there, though I am updating my system every couple of days. Software installed said it was already installed. If I resolved your wonders, maybe we should start wondering about the strange tor messing up things.

software installer, correction.

Hmm, I think you are right. Correct thing to do was to update, actually. But installer would not do, terminal would not do, and the browser redirected me to installation to update..now what? remove and reinstall maybe?

I hate to tell you this..just a reboot fixed the problem [https://forums.linuxmint.com/viewtopic.php?f=47&t=276622....thanks](https://forums.linuxmint.com/viewtopic.php?f=47&t=276622....thanks) so much for your time [**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747") ! sorry for being aggressive at my anniversary!! I will mark this as solved?

---

