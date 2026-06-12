---
title: "bash: make: command not found"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by websurrfr on 2005-10-07
I'm following the instructions for installing a program and they instruct me to type make at the command line but i get the error in the title of this thread.  Is there something I need to do to get this functionality?  Thanks.

---

### Post by varunus on 2005-10-07
Install the "build-essential" package from synaptic.

This will give you gcc, make, and several other things you'll need to compile.

You can also get any libraries you need by getting the "libraryname-dev" package from synaptic; if your program require libfoobar to compile, install libfoobar-dev from synaptic for it to work.

---

### Post by websurrfr on 2005-10-07
worked like a charm, thanks!

---

