---
title: "dual boot ubuntu and mint, share /home?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by evolmachine on 2010-12-18
Is it possible to share the /home partition between two distros?  I have two separate hdds, one with Lucid and another with the /home partition.  Can I install Mint 10 alongside Lucid and share the /home drive, or will that cause problems?

I currently have Ubuntu 10.04 32-bit, I want to try Mint 10 64-bit.

---

### Post by lmarmisa on 2010-12-18
I do not recommend to share both home directories because there is a lot of hidden configuration files and folders in these home directories.

```

ls -la ~

```

---

### Post by evolmachine on 2010-12-19
I found a solution by creating symlinks to the shared /home for files I want on both distros.

I mount the /home partition to somewhere in the Mint installation and delete all my directories I want to share in my Mint /home and replace them with symlinks.  Pretty shweet.  So far I've shared my Music, Pictures, .mozilla, .thunderbird, and a few other settings.

My only problem now is the Desktop folder still shows up empty.  Any thoughts on why?

---

### Post by lmarmisa on 2010-12-19
I agree. I like the symbolic links solution too.

---

### Post by evolmachine on 2010-12-19
Well the ~/Desktop symlink worked itself out after switching between the two distros.  Maybe I just needed a reboot.  All is well!

---

### Post by lmarmisa on 2010-12-19
Only one comment.

I suppose you will have no problem with the configuration data of Firefox and Thunderbird in the future, but I am not 100% sure about it.

Why?. Because it is very probable you will have different versions of these programs in your two distros during some periods of time. Therefore, you could have some troubles if the config files are not 100% compatible in both versions.

---

### Post by oldfred on 2010-12-19
I have my Firefox & Thunderbird profiles in a shared NTFS partition from when I used to boot XP a lot. I have had that for about 4 years and did try to coordinate version update in XP at the same time as Ubuntu but have not had any issues.

I do not symlink from another /home but from a /data partition. I now keep /home as part of root in each install and have moved all data & some hidden folders with data into my /data partition. I create a new root for each new version of Ubuntu of about 20-25GB and link all my data in to each of them. So when testing the next version I have all my same data in each version.

---

### Post by evolmachine on 2010-12-19
I guess I'll cross that bridge when I get there.  For now its a-okay!

---

