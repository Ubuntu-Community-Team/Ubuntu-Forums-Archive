---
title: "repo issues when using debootstrap - bad nano install"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by mattbennett on 2007-03-15
Hi all,

I'm experiencing a strange problem building Edgy images for xen via deboostrap. Here's the command for that:

```
debootstrap --arch i386 edgy /xen-images/mnt http://gb.archive.ubuntu.com/ubuntu/
```

where I've got an ext3 image mounted into /xen-images/mnt 

The installation all goes to plan, I can start my image using Xen and everything looks fine until I try to use my favourite text editor. Surprisingly, nano is not installed. So I fire up apt-get and tell it to fetch it. Everything installs smoothly but when I run nano, it experiences some problems.

Specifically, ctrl-o doesn't prompt me to save the file. When I hit return after typing ctrl-o (hoping that the menu just hadn't appeared) I get this mess:

```
hello world[ 8957.030164] SysRq : HELP : loglevel0-8 reBoot tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount
```
(the hello world was me)

It's not totally broken though -- if I then hit ctrl-x it asks me if I'd like to save the file before I exit.

At first I thought it was just a download glitch, but it's happened more than once. I've also tried it with different keyboards, machines etc.

Could there be some corruption in the repository?

Thanks,
Matt.

---

### Post by agent8131 on 2007-12-23
I realize this is an old thread but I've been researching this issue and thought I would comment.  The problem is not with nano.  The issue is that when using the xen console it emulates a serial console in which Ctrl+O is hardcoded to signal a Magic SysRq Key.  This is normally Alt+SysRq+[another key] but I guess there are issues using that combination over a serial link so for some reason Ctrl+O was chosen to emulate that sequence.  Since Xen uses one of these serial drivers it has the same behavior.  So far as I know there is no way to disable this or to switch the key combination to something else but if I find a way I will be posting it.  You can verify that the system works fine by connecting through ssh and you'll find that Ctrl+O works fine in nano again.

---

