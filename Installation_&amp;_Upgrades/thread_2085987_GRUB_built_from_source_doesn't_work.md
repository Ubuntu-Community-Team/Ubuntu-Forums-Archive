---
title: "GRUB built from source doesn't work"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by tc1148 on 2012-11-19
Hi, I am new to the forum, but am a software professional with many, many years of experience. I have been trying to build and run grub legacy from source code (the latest package on the download site, 097-29ubuntu66) for use on an ext4 partition. Using grub legacy and building it from source is a requirement for my project - I can't use the binary dist nor use grub2.

After not having any success, I did some googling. I noticed that there was a patch to support ext4. I checked the binary dist's build log and noticed 2 things:
1) It applies a whole bunch of patches (not just ext4), and
2) It links with libvolume_id

I've checked all the package dependencies, and they seem fine. I applied the patches (although my 00list does not include the last 3, cache-coherency.diff, objcopy-absolute.diff and no-reorder-function.diff). I also had to revert the varargs.diff patch, since I got a compile error (stdarg.h not found). I build with ./configure OBJCOPY="objcopy -R .comment.SUSE.OPTs -R .note.gnu.build-id" to overcome the objcopy problem. Everything builds fine, but it does not build or link with libvolume_id. I've tried some minor messing with the Makefiles, but I can't get it to build or link with libvolume_id.

I know how to install/reinstall grub, but when I install the built version it just reboots - no msg, no output at all, just an immediate reboot (to rescue disk). When I revert to the same version of the binary dist, everything boots fine. I also did a binary compare of my built stage1 and the binary dist stage1, they are byte identical, so I assume the problem is with stage2. I am guessing the issue is the lack of libvolume_id, but I don't know. I also don't understand why configure/make wouldn't recognize this was a needed component, if indeed it is.

This is extremely frustrating. Can someone enlighten me as to what I am missing?
Thanks!
--Tim

---

