---
title: "Kernel 2.6.31-rc1 build failed for i386?"
date: 2009-06-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-06-25
Just saw the kernel in [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1/)
seems like build failed for i386?:D

A little information about 2.6.31:
> We've had the regular two-week (and one day) merge window, and -rc1 is out, and the merge window is closed.

[ I suspect I'll still merge the SCore architecture, I wanted to give it a quick peek, but I've been busy with all the other patches so I'm closing the merge window now, but leaving myself the option of merging Score later - last I looked, the only non-SCore file it touched was the MAINTAINERS file, so it's not like it should break anything else ]

There's a lot in there, but let me say that as far as the whole merge window has gone, I've seldom felt happier merging stuff from people. I'm really hoping it isn't just a fluke, but people kept their git trees clean, and while there were a couple of times that I said "no, I'm not going to merge that", on the whole this was a really painless merge window for me.

I'm not saying that it was necessarily less bug-free than usual, I'm just saying that on the whole people sent me merge requests that made sense, explained what they did, and when I pulled I saw clear development lines. That just makes it much easier for me.

So thanks to everybody involved.

I hope that doesn't mean that it was really painful for others, or that we'll be chasing down more bugs than usual. And I _really_ hope we can keep things going this way, and it wasn't a one-off "things just happened to work this time".

As to the actual changes - too many to list. As usual, the bulk of the changes are to drivers (70% of the diffs), with drivers/staging being the bulk of that (about 60% of all driver changes - 40% of the total). But wonder of wonder, I think drivers/staging actually _shrank_ this time around, alledgely due to cleanups. Believe that who will.

On the filesystem front, we had btrfs, ext3 and xfs getting active development (Why xfs? Beats me, but that's what the stats say), and a fair chunk of work on the whole fsnotify unification work. And the VFS layer got some TLC wrt ACL and private namespace handling.

On architectures: ARM, powerpc, mips, sh, x86 are the bulk of it. On ARM, the bulk is new platforms (u300, freescale stmp, whatever), there seems to be no end to crazy new arm platforms. On x86 (and at least some degree on powerpc), a noticeable part is the whole new perf-counter subsystem. Along with lots and lots of other stuff.

On the whole? Tons of stuff. Let's start testing and stabilizing.

Linus

---

