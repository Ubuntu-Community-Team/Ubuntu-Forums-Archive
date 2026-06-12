---
title: "Emacs doesn't load .emacs"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by elektronaut on 2006-11-02
Hi,

I'm not sure why this is happening. Either it didn't work from the start or it's because someone played around with some emacs configuration files a while ago. I already tried to solve this by reinstalling, but to no avail.

The problem is that ~/.emacs is not loaded. If I try to change and save an option inside emacs, I get an error message stating that it was invoked with the -q option. This option prevents loading of the .emacs configuration file. I have no idea why it is called with this option. ```
$ alias 
``` doesn't show anything for emacs.

Somebody with an idea?

---

### Post by agrimstad on 2006-11-02
Why don't you try running:

$ which emacs

assuming you invoke emacs from the command line. I don't think the answer is going to be /usr/bin/emacs. I presume there is an emacs in your $PATH that is invoked instead of /usr/bin/emacs and this emacs, possibly a shell script, invokes the -q option.

-- al

---

### Post by elektronaut on 2006-11-20
:oops: Didn't notice your reply, sorry. I found the solution thanks to support from the usenet emacs group. There was an error in the global configuration file which caused emacs to start with the '-q' option and thus neglecting all configuration files.

---

