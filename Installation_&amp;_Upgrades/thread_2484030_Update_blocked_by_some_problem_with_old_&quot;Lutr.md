---
title: "Update blocked by some problem with old &quot;Lutris&quot; install"
date: 2023-02-15
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2023-02-15
So Software Updater is demanding (the message is stronger than usual) that I upgrade, on Ubuntu 20.04.LTS

Then I get "Failed to download repository information - check your Internet connection". That message is both uninformative and wrong, but anyway...

So, since several sources say try "sudo apt-get update" in this situation,

```
sudo apt-get update
Hit:1 https://dl.winehq.org/wine-builds/ubuntu focal InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                                     
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                       
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                     
Hit:5 http://security.ubuntu.com/ubuntu focal-security InRelease                                                                        
Hit:6 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu focal InRelease
Get:7 http://ppa.launchpad.net/lutris-team/lutris/ubuntu focal InRelease [18.0 kB]
Reading package lists... Done                            
E: Repository 'http://ppa.launchpad.net/lutris-team/lutris/ubuntu focal InRelease' changed its 'Label' value from 'Lutris stable' to 'lutris'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
```

So Lutris apparently changed their Label again. There are [old bug reports]("https://forums.lutris.net/t/lutris-package-not-found/9972") of the reverse problem, where the label changed from "lutris" to "Lutris stable" back in 2020.

I don't really need Lutris. So I went into Symantic Package manager and removed it. 

That didn't help. Same messages.

Tried ```
sudo apt-get clean
```, then update again. Didn't work.

I don't need Lutris, but I don't seem to be able to make it go away.

---

### Post by John Nagle on 2023-02-15
So I look at the key situation:

```
> apt-key list
...

/etc/apt/trusted.gpg.d/lutris-team_ubuntu_lutris.gpg
----------------------------------------------------
pub   rsa4096 2019-03-23 [SC]
      82D9 6E43 0A1F 1C0F 0502  747E 37B9 0EDD 4E3E FAE4
uid           [ unknown] Launchpad PPA for lutris

...

```

OK, so there's the obsolete key for Lutris. 

Tried 

> sudo apt-key del "82D9 6E43 0A1F 1C0F 0502  747E 37B9 0EDD 4E3E FAE4"
OK

No good, now sudo apt_get update complains ti lacks a key.

The solution was to remove the Lutris PPA from Software Updater. Even with no Lutris packages installed, the updater keeps trying to talk to the PPA, unsuccessfully.

---

### Post by grahammechanical on 2023-02-15
> The solution was to remove the Lutris PPA from Software Updater. Even  with no Lutris packages installed, the updater keeps trying to talk to  the PPA, unsuccessfully.

Well it would, wouldn't it? The Lutris PPA is in your software sources.list file that contains a list of internet addresses to software repositories.

Regards

---

### Post by monkeybrain20122 on 2023-02-15
Removing the packages doesn't remove the ppa. You should go to software& upates  (or from synaptic, settings > repositories) to uncheck the ppa. But the proper way to remove a ppa is to use ppa-purge (don't uncheck the ppa in software&updates in this case). This is because some packages might have been upgraded from the ppa and you would want to downgrade them back to their original versions.

---

