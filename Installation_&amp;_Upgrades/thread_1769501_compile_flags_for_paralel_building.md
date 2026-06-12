---
title: "compile flags for paralel building"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-05-28
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

this is how to set your ubuntu for compiling to use multi processor.  some older packages require you to use only 1 processor.  so comment the export make flag, then "echo $MAKEFLAGS" to see how many processors your using  you might need to "source .bashrc" to update the rc file

```

cat >> ~/.bashrc << "EOF"
# parallel compile settings
# set these to the number of processors you have + 1
export MAKEFLAGS='-j 5'
# end of parallel compile settings
EOF

```

previous code is 4 quad core, for my dual core

```

cat >> ~/.bashrc << "EOF"
# parallel compile settings
# set these to the number of processors you have + 1
export MAKEFLAGS='-j 3'
# end of parallel compile settings
EOF

```

to disable it momentarily for packages and do not compile correctly copy and paste this

```

export MAKEFLAGS=''

```

and then continue on.  the specific terminal with the disable ran will disable until closed  or re sourced .bashrc

---

### Post by mörgæs on 2011-05-28
Thanks. If you mark the thread 'solved', there is a better chance that people will find it.

---

### Post by boblizar on 2011-05-28
thanks for the heads up on marking it solved.  this script is set to add the info at the end of your .bashrc, so if you need to edit the command out, just put a # in front of the export MAKEFLAGS='-j 5' to de-activate it.

---

