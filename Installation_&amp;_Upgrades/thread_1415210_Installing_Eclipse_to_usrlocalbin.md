---
title: "Installing Eclipse to /usr/local/bin"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by pteri498 on 2010-02-24
I wish to use the new Eclipse Galileo, and so far it works fine... out of my home directory.

I would like to install this system-wide, so that all my users can use it just the same.

I assume the destination would be /usr/local/bin, but when I put the directory there and link the executable as /usr/local/bin/eclipse (linking to /usr/local/bin/eclipse_bin/eclipse), I get shared library errors.

This was a failed attempt at a hack, so I would like to know: where can I put the files so as to _properly_ do this installation?

---

### Post by sudo_your_mom on 2011-03-03
I know this thread is old but I had difficulty researching my own answer and wish to record it here for posterity.

> I assume the destination would be /usr/local/bin, but when I put the directory there and link the executable as /usr/local/bin/eclipse (linking to /usr/local/bin/eclipse_bin/eclipse), I get shared library errors.The problem here is that, with the symbolic link, eclipse thinks it is being run from /usr/local/bin and *not* /usr/local/bin/eclipse_bin. So, when the program is trying to load resources which ought to be found relative to /usr/local/bin/eclipse_bin, it is actually searching paths relative to /usr/local/bin; thus, the resources are not found and errors occur.

The solution, or at least an *easy* solution, is to remove the symbolic link and replace it with a shell script:

```
$ cd /usr/local/bin
$ sudo nano eclipse
```'eclipse' is the name of the script. Enter this into the nano editor:

```
#!/bin/bash

# move to the eclipse directory and execute 
cd /usr/local/bin/eclipse_bin
eclipse
```Press Ctrl+O to write to disk and Ctrl+X to exit. 

Finally, you will need to mark this script as executable for other users:

```
sudo chmod o+x eclipse
```Now, as long as '/usr/local/bin' is in your path, you should be set!

---

