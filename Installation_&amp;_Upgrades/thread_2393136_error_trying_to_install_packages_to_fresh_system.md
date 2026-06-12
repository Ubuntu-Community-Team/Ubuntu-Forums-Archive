---
title: "error trying to install packages to fresh system"
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-30
i am trying to install 134 packages in a script on a freshly installed 16.04 LTS system and i get this error message and all the installs are not done.```
E: Opening configuration file ups - ifstream::ifstream (2: No such file or directory)
```is "ups" the name of a file it is looking for that it gets an error on?  if so, where is that file supposed to be located?

*edit*:

i had some package names in the list with hyphens in front of the names to have them deleted. i removed those and re-ran it.  with that change, it now works.  maybe _apt-get install_ doesn't really like doing that.  or maybe one of those packages is a troublemaker.  now it is time to put some back in and see what happens.

*edit*:

it doesn't like a hyphen in front of package names.  that looks like an option.

*edit*:

it's always some misunderstanding of how things work.  in this case i recall from long ago about putting a hyphen in front, so when i glanced over the man page to verify my memory, i glanced over the important word "appended".  so it must be something else that i was recalling that did put hyphens in front.  i just don't recall what it is.  but no matter, changing my script to append is trivial.  doing another fresh re-install now, and will run my script on it when the system re-install is done.

*edit*:

my package list is now installed and it should have removed any undesired packages if they were there.

---

