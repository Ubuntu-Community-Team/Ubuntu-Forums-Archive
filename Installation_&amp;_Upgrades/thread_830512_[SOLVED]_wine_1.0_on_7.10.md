---
title: "[SOLVED] wine 1.0 on 7.10?"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2008-06-15
I see that wine 1.0 is out, i read a post about backports and wine, but gonna have to reread it a few more times to understand what is needed.

If I understood the post, wine will not be updated in Ubuntu for some time yet, but it can be done via the aforementioned backport.

Has anyone updated to wine 1.0 yet?
am i better off to wait for ubuntu team to include it on next release?

---

### Post by upchucky on 2008-06-15
bah, it turns out that i must upgrade to 8.04 to use wine 1.0

Gotta wait for a dvd to be made of 8.04, my satelite sys wont let me download complete upgrades.

---

### Post by emwine on 2008-06-17
For wine, git is probably your best bet.  Updates occur so often that it becomes frustrating waiting for packages to appear.  But with [git]("http://www.winehq.org/site/git"), you can be up to date anytime you feel like it.

If you are on 64 bit, see [here]("http://wiki.winehq.org/WineOn64bit").  I created the lib32 directory above my wine git tree, and then placed a symlink in my wine git tree.  That way I don't have to perform the lib32 links every build.

[Edit]
Using git means building from source.  By keeping a Wine git tree, you can fetch the diffs from release to release which will be relatively small after the initial download.  You also need various dependencies which you will discover in the 'configure' step.  In 7.10 64 bit, libhal and libcapi20 are missing.  For most people, these are not needed, but I assume their absence is why the Wine package maintainer stopped supporting Gutsy, although I don't really know.  But using git is a good way to keep up to date with Wine on 7.10 was my main point.

---

