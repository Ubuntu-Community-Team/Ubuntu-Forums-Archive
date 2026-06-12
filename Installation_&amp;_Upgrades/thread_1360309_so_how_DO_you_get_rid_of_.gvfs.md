---
title: "so how DO you get rid of .gvfs"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by graemev on 2009-12-20
I can see lots of discussion about how to get rid of this very annoying directory but I can't find a definitive solution.

It's only purpose seems to be to cause normal, well behaved, commands/programs to fail .... the final straw for me was when I ran out of space in / so decided to move all the homes to another new partition  ... so mv /home/* /newpart   ....then expect to do ln -s /newpart/* /home .... but of course .gvfs causes the mv to fail  ... as if does with any command that walks your $HOME   ... so I'm left with an incomplete copy and  lots of duplications (wasted space) as I don't have the time to work out what's safely copied and what's not  .. if does note show up in mount(1) so it very hard to get rid of .... would un-installing FUSE do the job ?

---

### Post by graemev on 2009-12-20
It seems to be completely undocumented 

graeme@eddie:/home/graeme-junked-bygvfs$ man -k gvfs
graeme@eddie:/home/graeme-junked-bygvfs$ man gvfs
No manual entry for gvfs

So I have some undocumented feature installed on my machine , which seem to break all the rules:

graeme@eddie:/home/graeme-junked-bygvfs$ ls -l .gvfs
ls: cannot access .gvfs: Transport endpoint is not connected
graeme@eddie:/home/graeme-junked-bygvfs$ file .gvfs
.gvfs: ERROR: cannot open `.gvfs' (Transport endpoint is not connected)

graeme@eddie:/home/graeme-junked-bygvfs$ ls -ali | grep gv
ls: cannot access .gvfs: Transport endpoint is not connected
188868 d?????????  ? ?      ?          ?                ? .gvfs

It's a DIRECTORY!!  ...it's not a pipe or a socket, it' just a plain directory...it has an i-node but nothing seem to be able to understand it ... I can't believe something like this has been allowed out out  ... and the it got installed without my needing to choose a lot of unstable/testing options.

---

