---
title: "how to compile and run &quot;linux in a box&quot; from source"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by sam2501 on 2008-07-18
I've been trying to compile the source code of this for a while
this is my first time compiling from source so i have no idea what i am doing

i want to post the output but its too long
so, any ideas on what i have to do?

---

### Post by Partyboi2 on 2008-07-19
maybe just post the last 10 lines so we have an idea where you are stuck at. You can also use something like [[COLOR=Blue]pastebin[/COLOR]]("http://pastebin.com/") to paste to and then provide a link to it.

---

### Post by sam2501 on 2008-07-26
> **Partyboi2 said:**
> maybe just post the last 10 lines so we have an idea where you are stuck at. You can also use something like [[COLOR=Blue]pastebin[/COLOR]]("http://pastebin.com/") to paste to and then provide a link to it.


 :)=D> Thanks, for ur answer, but tried a different way & it worked
      i installed clisp & slime from synaptic and wrote these few lines in a new file .emacs in my home directory
                 (setq inferior-lisp-program "usr/bin/cmucl")
                 (add-to-list 'load-path "/usr/share/emacs/site-lisp/slime")
                 (require 'slime)
                 (slime-setup)
its a different implementation though (cmucl not clisp)
but thanks anyway

---

