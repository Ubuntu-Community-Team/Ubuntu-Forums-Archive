---
title: "After a Feisty install...&quot; Error, failed to load OS&quot;"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Levenly on 2007-06-02
My friend is trying to install Feisty on his machine, but after he installs it he gets an error that says, "Failed to load OS" on a blank screen.

He reinstalled Feisty about 2-3 times (I wasn't there and I was helping him via AIM), and I guessed that he probably didn't do the partitions correctly, or mount it correctly, but he did it right.

He has two hard drives on his machine, sda1 and sdb1.  He is trying to install it to sdb1, but every time he installs it, he gets the error.  

We decided to download and install Edgy and see if that works.  But I really have no clue what the problem is.

If any of you have any suggestions, feel free to post them.

---

### Post by bulldog on 2007-06-02
Thank you for the invitation to post here :D

On which hdd did he install GRUB?
By default it will install on hd0 [sda] but if he boots from hd1 [sdb] you will get an error.

Try to set to boot from the other hdd in your BIOS and see if you see GRUB.
[no guarantee it will boot,but it's a start :D]

---

### Post by Levenly on 2007-06-02
Ok, I forgot about that.  Though, sdb1 is his primary hard drive that he boots off of.  So I'm not sure if it's already set up to boot from there, but I'll have him check.  I did think he said he tried out Vista on his computer, and I've heard from people that Vista won't let you do anything on the computer besides use Vista, but I'm not sure.

I'll have him check though, thanks!

---

