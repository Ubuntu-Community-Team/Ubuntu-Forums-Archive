---
title: "reinstall troubles"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by bearcat on 2007-11-22
Got myself in a bit of a bind here...

The background: I have a dual boot XP/Gutsy box. A few weeks ago, my Windows partition seized up and wouldn't boot, so I thought I'd take the opportunity -- per a prior thread on here -- to ditch the Windoze and finally go to an all-Ubuntu machine. I don't know if I did something wrong in the process, or if I followed the directions correctly and my own computer was having none of it, but it rendered my *Ubuntu* partition unbootable. 

So, reluctantly, I ended up deleting my new "storage" partition and reinstalling Windoze after all, knowing full well that I was going to lose grub in the process. I used explore2fs to drag any files I hadn't backed up over into Windows, so that's not my primary problem, and I think I may as well take the opportunity to do a clean Gutsy reinstall while I'm at it. But I'd still prefer, if possible, to get back into the Ubuntu partition to make *sure* I haven't forgotten to recover any important files that might be hiding in places I didn't think to look with explore2fs.

So I need to (a) either reinstall grub and undo whatever I the hell did to fstab, so that I can get back into the Ubuntu partition directly, or (b) access the Ubuntu partition directly from the LiveCD. Help?

---

### Post by bearcat on 2007-11-22
Never mind. I just installed ext2IFS instead of explore2fs, so I'm going to check for files that way and then just do a clean reinstall once I'm sure I have everything carried over.

---

