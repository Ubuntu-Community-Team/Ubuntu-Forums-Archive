---
title: "Synaptic failure - cannot update"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by touchlikefire on 2007-04-14
I  am having one B of a problem with Synaptic.  I cannot update any of my packages, nor can I install, or uninstall, anything.  I have no idea how this happened, so let us just start from the beginning.

I installed **Feisty AMD64** about two weeks ago, and since that time the kernel was updated twice; first to **2.6.20-13-generic** and then to **2.6.20-14-generic**.  When Synaptic Update Manager prompted me to update to 2.6.20-14, it also updated a bunch of packages as well.  However, after a reboot, I got a very strange error about having an invalid ext3 fs on my /usr partition, and eventually I corrected it by reverting to 2.6.20-13.

However, since that time, Update Manager has been telling me about all the goodies I should be updating to, however I keep getting **Broken Dependency **Errors that I *cannot* resolve.

Synaptic recommends **"sudo apt-get install -f"**, but that doesn't do anything, it still fails.  I can't get Synaptic or the command line to replicate the errors I was receiving, but here is the most recent output of **apt-get install -f**:
```
Unpacking replacement python2.5 ...
/var/lib/dpkg/info/python2.5.postrm: 8: update-menus: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 8: update-menus: not found
dpkg: error processing /var/cache/apt/archives/python2.5_2.5.1~rc1-0ubuntu3_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 8: update-menus: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Preparing to replace python2.5-minimal 2.5.1~rc1-0ubuntu2 (using .../python2.5-minimal_2.5.1~rc1-0ubuntu3_amd64.deb) ...
Unpacking replacement python2.5-minimal ...
Errors were encountered while processing:
 /var/cache/apt/archives/python2.5_2.5.1~rc1-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The broken dependency issues are related to OpenOffice.Org suite, and then python 2.5.  However, I cannot upgrade, install, or uninstall anything, b/c of these dependency issues. 
```
# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  python-uno: Depends: openoffice.org-core (= 2.2.0-1ubuntu3) but 2.2.0-0ubuntu2 is installed
  python2.5: Depends: python2.5-minimal (= 2.5-5ubuntu11) but 2.5.1~rc1-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.

```

I wish I had more precise error messages for you, but I can't get the command line to give the same ones I was seeing earlier in the week.  I know there is simple solution to this--I had a similar problem once six months ago on Edgy 6.10 i386--but I've searched all my previous posts and cannot find it.

Please help me fix Synaptic/apt-get so that I don't have to scrap my whole OS and start over.  Any links or information is greatly appreciated; I've come very far learning linux, but I'm still an amatuer and this baffles me.

---

### Post by zvacet on 2007-04-14
**synaptic>edit>fix broken packages**

---

### Post by touchlikefire on 2007-04-15
I thought I had tried that previously, but I tried it again, and got the same errors:
```
E: /var/cache/apt/archives/python2.5_2.5.1~rc1-0ubuntu3_amd64.deb: subprocess new post-removal script returned error exit status 127
```
that's the only one i could copy and paste.  The rest are the same as my previous post.

---

### Post by touchlikefire on 2007-04-17
Bump?

Does anyone know how to fix a Synaptic that perpetually fails because of broken dependencies, but won't let you update them or remove them, and therefore you can't do anything at all to fix it?

This is one of reasons I don't see linux making it in the consumer market: an update system/software philosophy that catastrophically fails (as in all, or nothing) when one piece of software is broken.  What a bummer; I was really hoping I wouldn't have to reinstall my entire OS.

---

### Post by UltraSonicSite on 2007-04-25
I'm experiencing the same problem, with another program that won't uninstall. It is a bit discouraging.

---

### Post by UltraSonicSite on 2007-04-25
I got it working again:

> /var/lib/dpkg/status and remove all [actual file you want to delete/fix] entries

---

### Post by touchlikefire on 2007-04-26
> **UltraSonicSite said:**
> I got it working again:

Thanks UltraSonicSite for the possible fix.  Unfortunately, I ended up scrapping the entire thing and reformatting the drive.  But it's good to know there's a solution, should anything like this happen again.

---

### Post by kelvin spratt on 2007-04-26
i've just started with linux and i new before that there is always a solution to any problem with linux but in our own arragance we blame linux for our own lack off knowledge in linux anything can be fixed with a bunch of code except our own lack of knowledge lets us down as we are programed to think if its not ms its a toy but thats not true linus is a super application can ms make an application that works straight from the box with no aditional drivers no they can't motherboards and every other piece of software needs extra drivers to work
i'm not slagging msoft i still use it for certain things till i find solutions and remember linux is free not $xxx.xx
as is msft so please use the forums as i do and be patient as all probs can be fixed linux is different and you learn as you go on how much better it is but you can't run before you walk just think different and it will come

---

### Post by Linuxratty on 2007-11-05
This just happened to me about ten minutes ago:

EDPKG was interrupted You must manually ryn dpkg config ar to fix the problem. Huh
E _cache >open () failed.please report.


 I have no idea what has gone wrong,much less how to fix it. A reboot did no good.

---

