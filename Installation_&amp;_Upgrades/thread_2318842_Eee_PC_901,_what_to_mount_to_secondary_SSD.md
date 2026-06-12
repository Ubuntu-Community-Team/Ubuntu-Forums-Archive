---
title: "Eee PC 901, what to mount to secondary SSD?"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by ranma_dude on 2016-03-29
Hi, everyone. Basically what it says on the tin. I'm trying to get Ubuntu 15.10 x32 on my netbook (it currently has 11.04(?) installed from way back when). It has a 4GB primary SSD and a 32GB secondary SSD. I'm doing a clean install, but the install keeps erroring out because there's not enough space on the 4GB drive. I've mounted /home to the second SSD, but what else can/should I mount to it? I want to keep any core/boot-up files on the first drive because it reads/writes much faster than the second. Right now my thoughts are to move /usr, /var, /tmp, and /dev. Thanks!

---

### Post by Bucky Ball on 2016-03-29
Welcome. You're not going to get Ubuntu on 4Gb, regardless of what they say on the tin. You could create a /boot partition and put that on the 4Gb SSD (sure it's not an eMMC card?) and that should speed things up. People do it but I've personally never used a separate /boot partition so can't give much help.

No doubt you'll find more info with a search.

---

### Post by ranma_dude on 2016-03-29
Thanks for the super prompt reply. On 11.04 you could make do with the entire OS sans /home on the single 4GB (it's advertised as soldered onto the motherboard, though a quick google just now turns out that's not true, it's just ridiculously hard to access). My original thought was to mount those various folders to the second SSD, but I think perhaps your idea is better and simpler. That would mean mounting / to the second SSD and /boot (+ others?) to the first, yes? Anything else that would speed boot-up?

I'll try that out, see if it works, and get back to you. Thanks again.

---

### Post by Bucky Ball on 2016-03-29
*Thread moved to **Installation & Upgrades**.*

You'll probably get more input here and people will take into account you're new here. :)

11.04 was an age ago in computer terms. 15.10 is a rather larger beast. With some extreme hoop-jumping you may be able to get a semblance of it running from the 4Gb SSD, but I would probably consider that an achievement and 'experimental'. Virtually everything would be on the larger SSD, which may cause issues in itself if there's breakage.

PS: Just a note. On some of these hybrid machines, and laptops generally, it is only possible to boot from this little 'jump' drive (sda). Therefore you might need to put /boot there regardless. Hopefully someone with more experience of them will be able to jump in.

The majority of laptops will only boot from sda without some serious hacking to make it otherwise (don't get me started on trying to boot from SSD (sdb) in a hard drive caddy in my optical drive bay!).

---

### Post by Irihapeti on 2016-03-29
I've got an EeePC 900 with 4GB and 16GB drives.

I keep the system on the smaller drive and /home on the larger one. I'm aware of the shortage of space on the main drive, so I keep installed programs to a minimum, and make sure that old update downloads (in /var/cache/apt/archives) are deleted regularly.

It's currently running 16.04 (pre-release), but it's not a standard install. I start with a command-line version, using the mini ISO, and then add only the bits that I want.

I've never tried making a /boot partition, but I imagine that would be a possibility. Just don't make it too small, or it can get full rather quickly and then cause major problems.

---

### Post by ranma_dude on 2016-03-30
Hm... Thanks for that, you two. Yes, I had mine set up identically to irihapeti's before. Well, save for it being a standard install of an older OS.

I went ahead and tried it with /boot taking up all of the 4GB drive and the rest of the system on sdb, and the result booted up fine but introduced some problems of its own. I then went ahead with my original plan (everything on sda except /home, /var, /tmp, /usr in separate partitions on sdb), and while that has resulted in a problem-free install, chopping up my drive is not as elegant a solution as I'd have liked. Oh well. I don't plan on adding much more to it than what's included anyhow.

I'll tinker with it a little more, but at least I know I have a solution that works. Many thanks again, you two.

---

### Post by Impavidus on 2016-03-30
You need to have /bin, /sbin, /etc, /root and /lib on the root partition. On my system, I have 10 GB on the root partition, 8 GB of which is in /usr. Putting /home and /usr on two partitions on the big SSD and everything else on the root partition on the small SSD should work.

/dev, /proc, /run and /sys are pseudo-filesystems. They are not on any drive.

---

### Post by ranma_dude on 2016-03-30
Okay, so yes, moving just a few more folders to the other drive worked and Wily Werewolf is now fully installed without any problems. I would still like to get the hotkeys and Eee PC-specific features/buttons working, but that's a problem with software that I'll look into and try to fix on my own. There are enough dangling threads that I can at least start with.

Thanks for all the help, everyone.

---

### Post by mörgæs on 2016-03-30
Good, please mark the thread 'solved'.

---

### Post by Bucky Ball on 2016-03-30
> **mörgæs said:**
> Good, please mark the thread 'solved'.

+1. See the first link in my signature.

---

