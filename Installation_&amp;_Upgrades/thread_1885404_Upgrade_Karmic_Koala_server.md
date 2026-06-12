---
title: "Upgrade Karmic Koala server"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by Alex1200GS on 2011-11-23
Hi all,

I have a server running Karmic Koala and just decided to upgrade it to the current version, only to find out that the karmic repositories are no longer there. 

How should I edit /etc/apt/sources.list so that the OS will realize there are updates available?

Thanks for any hints.

---

### Post by surfer on 2011-11-23
the repositories for the 'retired' versions are here:

[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by Alex1200GS on 2011-11-23
Thanks Surfer!

I updated sources.list with the "retired" repositories, then ran apt-get update/upgrade, even dist-upgrade but to no avail; the OS didn't notice that there's a new version available. Any hint on how to force upgrade?

---

### Post by Alex1200GS on 2011-11-24
So, the answer to my question was "sudo do-release-upgrade", but I need to physically be there as the OS discourages me from upgrading through SSH.

---

### Post by surfer on 2011-11-25
true, it is discouraged. but i've tried it (with a newer release than karmic though) and it worked perfectly. if there is a glitch during the update, you may not be able to reconnect to the ssh server...

good luck if you try!

---

### Post by MAFoElffen on 2011-11-25
> **Alex1200GS said:**
> So, the answer to my question was "sudo do-release-upgrade", but I need to physically be there as the OS discourages me from upgrading through SSH.Since you updated your sources.list to the EOL repo's already, make sure you have all patches and upgrades up-to-date before going on:
```

sudo aptitude update && sudo aptitude dist-upgrade

```Update your sources.list from Karmic to Lynx:
```

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sed -i 's/old-releases/us.archive/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

```Then try your release upgrade:
```

sudo aptitude install update-manager-core && sudo do-release-upgrade

```That installs the new update manager before doing a release upgrade.

- If you who get &#8220;no release found&#8221;, edit the /etc/update-manager/release-upgrades
and if you see &#8220;Prompt=lts&#8221; change it back to &#8220;Prompt=normal&#8221;, unless you want to just upgrade to an LTS.

If  you get this &#8220;no release found&#8221; and you have &#8220;Prompt=lts&#8221; in  /etc/update-manager/release-upgrades and don't want to change that  release setting because of say unattended updates. Then all you need to  do is run

   ```

  
   sudo do-release-upgrade &#8211;proposed 
 
 
```- The above should work okay over ssh. Has worked Okay for me, but you know there are no 100% guarantees... Things do happen. 


Notes on other/alternate methods:
- I do the above method for older installs to newer -and- to get a new install to a development version for testing.

Notes:
Some on old versions may have to do an incremental distribution upgrade to 10.04 first, before going higher. I know 2 ways to do incrementals on old Server Editions...

The first way is to take an Alternate Install CD of the target version. Don't boot off it, but rather plug it in and run ./cdromupgrade from /media/cdrom. 

There's another undocumented utility on the Server Edition Install CD that I've used that allows Incremental upgrades on Server.  If you booted on a Server Install CD and select Install. it Probes the installed system...  If it sees an earlier version of Server, it asks if you want to upgrade that system...

---

