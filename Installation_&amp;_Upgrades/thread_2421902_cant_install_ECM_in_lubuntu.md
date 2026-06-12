---
title: "cant install ECM in lubuntu"
date: 2019-06-28
forum: Installation &amp; Upgrades
---

### Post by mstella2390 on 2019-06-28
I want to install ecm so that I can play a psx rom on the mednafen emulator.  I have newest version of lubuntu 19.04.  I used nano to remove the hashtags in the /etc/apt/sources.list file and have used sudo apt-get update so that I am connected to the universe repository where I believe the ecm package is located (as well as several other repositories that were in the original sources.list file), but when I try to use sudo apt-get install ecm, i get the error E: package 'ecm' has no installation candidate.  is there a source that I can add to my source.list file that will make it so that I can install ecm?

---

### Post by cruzer001 on 2019-06-29
Hello

You updated first?

Please post the sources.list entry you made.

---

### Post by deadflowr on 2019-06-29
ecm doesn't seem to exist on 19.04.
Not sure what the fix is, perhaps pull it from an older release archive.

---

### Post by mstella2390 on 2019-06-29
right so, question was, which entries did i make to my sources.list file.  Answer is: I didn't make any entries.  I just deleted the hashtags that were turning certain lines of code to text so that those lines were activated as code lines.  I deleted the hashtags preceding the lines that add access the Universe, the Multiverse, and the Canonical.

second post suggests accessing older versions of lubuntu repository in order to have access to a repository which contains ecm through the terminal.  Now im wondering, how is that done?  Do I just make additional entries to my sources.list file, and if so what are those entries?

What I see here, is that if the ecm is a package, and there is a location for this package on the internet, what is that location?  Can I enter this location into my sources.list file, so that I can then download ecm through the terminal?

---

### Post by CatKiller on 2019-06-29
Before it got pulled from the repositories, it had been on the same version for ages. It doesn't seem to depend on anything that you won't have. You can probably just download and install the .deb file from the [18.04 repository](https://packages.ubuntu.com/bionic/ecm).

---

### Post by mstella2390 on 2019-07-01
Thank you so much. I downloaded that deb package directly from one of the mirrors on that site and I just double clicked it and ecm was installed.  Playing ff7 (e) for ps1 as we speak.

---

### Post by liquidcross on 2020-04-23
I tried this, but ecm is still coming up as "command not found" after installation. Any recommendations? (I'm running 19.10.)

---

