---
title: "apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by AI0867 on 2008-04-26
Short version:
APT no longer works, libapt-pkg-libc6.7-6.so.4.6 is incompatible with the new libstdc++.so.6 (or the other way around)

Long version:
-Used adept_updater to dist-upgrade (which downloaded the dist-upgrade tool and so on), this predicted at least an hour of download time, I went to sleep
-Next morning, dist-upgrade tool is gone (as in closed), adept_updater's tray icon tells me over 1500 packages need updating (only slightly less than the dist-upgrader said), which leads me to believe the tool crashed halfway in.
-I tell adept_updater to do its job and leave again
-Return to the same situation, with 735 packages left
-However, adept_updater refuses to start, as do all other graphical updaters. Aptitude and apt-get reveal the following:
ai@VIJF# sudo aptitude full-upgrade 
aptitude: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by aptitude)
aptitude: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
ai@VIJF# sudo apt-get dist-upgrade
apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)

Apparently, the upgrade crashed somewhere between the updates for glibc and apt, leaving my apt in a broken state. Luckily, autotools and gcc still work.

Possibilities for solving this:
-Dropping in a fresh apt to fix things
-Manually resolving the dependencies to get apt working again so it can take care of the rest itself
-My /home is on a seperate partition, and I still have a free partition that I can set up a new / on, it's the same size as my current / too. (last resort)

Not being too familiar with the inner workings of apt, I could use some advice with this.

---

### Post by sujitpal on 2008-06-04
Were you able to find a solution for this? Is there a solution for this short of re-installing Ubuntu?

I am running 8.04 and this started happening right after I did a dist-upgrade.

I can no longer run either apt-get or synaptic. When I run apt-get to do anything, it comes back with (so this is chicken and egg here):

$ sudo apt-get update libstdc++
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.7-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_l, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

/usr/lib/libstdc++.so.6 is linked to /usr/lib/libstdc++.so.6.0.9
and 
/usr/bin/gcc is linked to /usr/bin/gcc-4.2

gcc -dumpversion says 4.2.3

I have tried copying over libstdc++.so.6.0.8 and gcc-4.1.2 and linking to them from my FC7 box at work, but I still get the error.

I am neither a Debian guru or a C++ programmer, so this is pretty much going to be the extent of my troubleshooting ability unless someone is kind enough to give me instructions on how to fix this.

I really hope I don't have to re-install the entire thing, but if thats the last resort, then that is what it is...

Would really appreciate you (or any of the gurus here) providing some pointers.

Thanks very much,
Sujit

---

### Post by AI0867 on 2008-06-07
I managed to fix it, here's roughly what I did:
-Figure out which of the two files is the old one (libstdc++.so.6 in my case)
-Find the package containing it on packages.ubuntu.org (google helps)
-Download the package and extract the archive
-Drop the file in /usr/local/... (so /usr/lib/libstdc++.so.6.0.9 becomes /usr/local/lib/libstdc++.so.6.0.9)
-Set up the same symlinks as the original file had
-Check if it now works, if it doesn't, repeat the procedure with the new conflicting file.
-When you're done, upgrade the packages the proper way and clean up your /usr/local again.

---

### Post by jordanius on 2008-07-10
My immense gratitude for this one aio867...Cheers!

---

