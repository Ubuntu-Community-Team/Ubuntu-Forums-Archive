---
title: "How to fsck --repair-tree?"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by Zarckon on 2008-11-28
I did a bad thing. I shut my system down improperly. My monitor quit working and my attempts to get it back up failed. So I just killed my machine. I was online somewhere at the time.

When I got the monitor back up and running and attempted to boot back into Ubuntu I got the following:

fsck 1.40.8 (13-Mar-2008)
Filesystem seems to have fatal corruptions. Running with --rebulid-tree is required.
Reiserfs super block in block 16 on 0X803 of format 3.6 with standard journal blocks (total/free): 13428320/4676743 by 4096 bytes.
Filesystem is Not clean
fsck died with exit status 4.

*an automatic file system check (fsck) of th root filesystem failed. A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintainance mode with the root filesystem monted in read-only mode.
*The root filesystem is currently mounted in read-only mode, a maintainace shell will now be started.
After performing system maintainance, press CONTROL-D to terminate the maintainance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root:mycomp:~#

So from there I've run fsck. I've tried it plain, -A, -r, and other variations.

With -r I got something like this:

bad_paths the left delimiting key [14012 14789 0X0 SD (0)] of the node (2425622) must be equal to the first element's key [14011 84535 0X0 SD (0)] within the node.
bad_stat_data: The objectid (11489) is shared by at least two files. Can be fixed with --rebuild-tree only.
finished
comparing bitmaps.. vpf-10640: The on-disk and the correct bitmaps differs. Fatal corruptions were found, Semantic pass skipped 2 found corruptions can be fixed only when running with --rebuild-tree

I'm obviously not understanding how to run --rebuild-tree. I was thinking that it was a function of fsck, but if so I'm missing it. If it's some other program, then can someone tell me how to run it? I should also mention that it's my root system that's corrupted. Does that mean it's not repairable? And I did see a post that said something about the alternate CD's having some sort of repair installation function, would that help me repair a file tree?

Thanks for any help you can provide.

---

### Post by cariboo on 2008-11-29
See as your are using reiserfs shouldn't you be using reiserfsck? have a look here:

[http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html)

Jim

---

### Post by Zarckon on 2008-11-29
> **cariboo907 said:**
> See as your are using reiserfs shouldn't you be using reiserfsck? have a look here:

[http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html)

Jim

Ow! Had no idea that there was an fs specific fsck. The instructions seem clear, but one little hang up. If I'm reading it correctly I have to install reiserfsck and at this point I can't boot into Linux at all. Am I hosed or is there some way to install it on my broken system?

---

### Post by Zarckon on 2008-11-29
I went and checked to see if reiserfsck was on my machine, found it and ran the line suggested in your post. On restart it appears that the current kernel .24 disappeared. I get a file not found error from grub.

I was able to boot to a command line interface from .19, but don't know how to do anything from there. That is, not sure how to start x, or log in to my account (assuming it's actually still there).

I'm thinking that if I can get back into .19 then I can upgrade to ,24 from there.

Almost but not quite there. Any thoughts on how I can complete the journey?

---

