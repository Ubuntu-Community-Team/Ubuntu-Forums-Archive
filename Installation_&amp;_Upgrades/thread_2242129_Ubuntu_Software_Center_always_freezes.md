---
title: "Ubuntu Software Center always freezes"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by fotcfanforums on 2014-08-30
Hi guys. I just purchased a new PC which has Ubuntu 14.04 LTS and it was going quite well until I couldn't install programs. Just yesterday I tried to install VLC media player and that's when Ubuntu Software Center froze on me. I tried another thing to download and it froze again. Each time it freezes within seconds after I try to install a program. 

I also tried to install VLC media player by using the terminal, but first I did these codes to do an update and upgrade:

```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

I get this error after a while when running the first one: 

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

And the same happens right after entering the second code for the upgrade. What could the problem be? There's some programs I'd like to install soon, so any help would rock! :)

---

### Post by ThatBum on 2014-08-30
There is a package half-installed, do as says and run [COLOR=#000000][FONT=Ubuntu Mono][FONT=courier new]sudo dpkg --configure -a [/FONT][/FONT][/COLOR]to fix it it.[COLOR=#000000][FONT=Ubuntu Mono][FONT=courier new]
[/FONT]
[/FONT][/COLOR]

---

### Post by LostFarmer on 2014-08-30
Depending on Internet speed , it can take a long time.  When I first ran  Ubuntu Software Center it took 10+ min to download its update package list, and it did look like not a thing was going on.

---

### Post by ThatBum on 2014-08-30
Personally I don't use the Software Center anyway, it's been bloated and unstable in my experience. I usually use commands to get the job done, or Synaptic.

---

### Post by fotcfanforums on 2014-08-31
> **ThatBum said:**
> There is a package half-installed, do as says and run [COLOR=#000000][FONT=Ubuntu Mono][FONT=courier new]sudo dpkg --configure -a [/FONT][/FONT][/COLOR]to fix it it.[COLOR=#000000][FONT=Ubuntu Mono][FONT=courier new]
[/FONT]
[/FONT][/COLOR]

Thanks that worked. 

By the way, is Synaptic package manager still around? I preferred that over USC.

---

### Post by ThatBum on 2014-08-31
Yes, [FONT=courier new]sudo apt-get install synaptic[/FONT]

---

