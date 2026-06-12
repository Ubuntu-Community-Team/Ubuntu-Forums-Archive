---
title: "Messed up big time. Easy fix?"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by jorwex on 2008-05-02
I *had* a wonderfully working hardy install going. I had to use a friend's laptop with windows on it earlier in the month, and decided that I'd like to put back a tiny windows partition at the end of my disk. So I popped in my ol windows xp cd after i made a fat32 primary partition at the end of my 320GB drive. 

Installation was going good. It got to the point where it restarts, but you leave the disk in the drive, and it continues where it left off...except that it started the installation all over instead, and didn't go to the 2nd part of the installation.

So I took out the disk to see what would happen, and it now says "Invalid Partition table." So I'm thinking something with grub and the MBR maybe?

I thought, "o well, I'll retreat to ubuntu till I can figure this out." I've never had to do it, but i knew you could boot up a live cd, go to a terminal and type "sudo grub" and then "find /boot/grub/stage1" and it returned (hd0,1). So I typed "setup (hd0)" and it says "Error 12: Invalid device requested"

So Now I'm screwed.

1) how do i get my dear ubuntu back.
2) does anyone know of the way you get windows to do the 2nd part of the install? I KNOW it has something to do with grub. I could always start from scratch and wipe ubuntu, install windows, then install ubuntu like you're supposed to...but this is much more interesting :)

HELP!

Thanks,

Jordan

---

### Post by jorwex on 2008-05-02
Alright I got #1 figured out. I needed to do "root (hd0,1)" before "setup (hd0)".

Now How do i get Windows XP to finish the installation and not go back to the beginning of the install after the mandatory restart? 

Is this happening because the partition is at the end of my disk (in terms of partitions)?

---

