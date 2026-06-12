---
title: "Fresh Install Question"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by victor9098 on 2008-04-24
Hi All,

Will keep this as brief as possible. When I went from Feisty to Gutsy (via upgrade) I had a few problems like losing all my compiz and a few other things. After a few weeks I did a fresh install and everything was perfect.

So the question...can I just make a copy of my home directory, save to an external source, then do a fresh install (of Hardy) and 'drop' in the old home directory with all my settings and files? Or is this bad practice?

Any advice would be much appreciated!

---

### Post by IgnorantGuru on 2009-11-01
Sure, you can drop in the old /home folder.  However, some system-level settings are stored in /etc, /root, and elsewhere, so you may need to set up compiz again, for example.  /home stores user-level settings.  Anything does with sudo is usually stored elsewhere.

If you know the particular settings you want, you can sometimes copy them from the old system folders to the new ones.  But don't copy all of /etc because you'll damage Karmic's setup, which differs from Gutsy.

My new habit is to learn to do all my mods from the command line.  Then I can save them to a post-install script which I run to set everything up the way I want.  And in some cases this script copies files from the old /etc.  It makes fresh installs very quick!  (I never do upgrades.)

---

