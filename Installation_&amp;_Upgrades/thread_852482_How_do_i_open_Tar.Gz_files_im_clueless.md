---
title: "How do i open Tar.Gz files? im clueless"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Attila2452 on 2008-07-07
i just downloaded a dock for my Ubuntu, and it has a tar.gz file . i don't know what to do.

---

### Post by Rallg on 2008-07-07
Try double-clicking. If that doesn't work, right-click and use "Open with Archive Manager."

You will see a window that display the contents of the archive. Select what you need, and extract it. You might have to do that twice.

In Linux, the kind of files that come as *.tar.gz are usually source code, which must be compiled to be used. Do you know how to do that?

---

### Post by erfahren on 2008-07-07
sounds like you'll need to compile it - but before you go and do that did you check to see if it's in the repositories? (search for it in Synaptic Package Manager)

you can also search the list of packages online [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

if you do decide you need to compile it take a look at these guides
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

notes: the "apt-file" package mentioned in the first one can be helpful
also: get the "nautilus-open-terminal" package - it puts the option to open a folder in the terminal - so you can just right-click on the archive and extract it and then right-click on the extracted folder and "open in terminal" (it saves some typing and comes in handy)

---

### Post by Attila2452 on 2008-07-07
> **Rallg said:**
> Try double-clicking. If that doesn't work, right-click and use "Open with Archive Manager."

You will see a window that display the contents of the archive. Select what you need, and extract it. You might have to do that twice.

In Linux, the kind of files that come as *.tar.gz are usually source code, which must be compiled to be used. Do you know how to do that?



this is the link im using:

[http://wiki.awn-project.org/InstallingFromSource](http://wiki.awn-project.org/InstallingFromSource)

im trying to follow the instructions but its not working. This is what it says:


attila@attila:~$ tar -xzvf avant-window navigator-0.2.6.tar.gz
tar: avant-window: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: navigator-0.2.6.tar.gz: Not found in archive
tar: Error exit delayed from previous errors

---

### Post by satauros on 2008-07-07
looks like your missing a dash between window and navigator, kiddo

---

### Post by avtolle on 2008-07-07
First, you have a typo according to the link. IIRC, it is avant-window-navigator-0.2.6.tar.gz.
Second, did you download it to your desktop? If so, the first thing would be to ```
cd ~/Desktop
``` then begin the tar command; after typing in tar -xzvf a use the Tab key to autocomplete the name of the file to avoid typos.

---

