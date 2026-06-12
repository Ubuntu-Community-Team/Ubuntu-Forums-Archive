---
title: "apt-get update issue"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by psoulocybe on 2005-03-22
I'm having a strangge issue w/ my updates....
i've tried w/ the standard ubuntu repositories in sources.list as well... but this is a strange bug to me.
any ideas?
```

Failed to fetch http://ubuntu.secs.oakland.edu/dists/hoary/universe/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading Package Lists... Done
W: Duplicate sources.list entry http://ubuntu.secs.oakland.edu hoary/main Packages (/var/lib/apt/lists/ubuntu.secs.oakland.edu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.secs.oakland.edu hoary/restricted Packages (/var/lib/apt/lists/ubuntu.secs.oakland.edu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.secs.oakland.edu hoary/universe Packages (/var/lib/apt/lists/ubuntu.secs.oakland.edu_dists_hoary_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by techmonkey on 2005-03-22
[QUOTE=psoulocybe]I'm having a strangge issue w/ my updates....
i've tried w/ the standard ubuntu repositories in sources.list as well... but this is a strange bug to me.
any ideas?
```

Failed to fetch http://ubuntu.secs.oakland.edu/dists/hoary/universe/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading Package Lists... Done
W: Duplicate sources.list entry http://ubuntu.secs.oakland.edu hoary/main Packages (/var/lib/apt/lists/ubuntu.secs.oakland.edu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.secs.oakland.edu hoary/restricted Packages (/var/lib/apt/lists/ubuntu.secs.oakland.edu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.secs.oakland.edu hoary/universe Packages (/var/lib/apt/lists/ubuntu.secs.oakland.edu_dists_hoary_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```[/QUOTE]
 I read about this somewhere else on the Hoary forum before. Apparently it's just because Hoary is still in Preview mode -- Come April 6th, those repositories will be activated again.

I'm still pretty sure they were working a week or so ago though. :-/
Use Synaptic preferences to deactivate them temporarily, if the errors bug you.

---

### Post by psoulocybe on 2005-03-22
nevermind
this afternoon it went through without a hitch

i figure it's because things are still changing so fast.

---

