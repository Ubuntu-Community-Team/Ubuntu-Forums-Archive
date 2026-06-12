---
title: "Clone m.2 best practices"
date: 2023-09-15
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2023-09-15
I have an m.2 based laptop and wanted to clone the ssd using dd for backup/restore purposes.  Trouble is, m.2 drives appear to be far worse than hdd's with respect to capacity.  I have four 1TB m.2 drives all with different actual capacities, thus a potential cloning nightmare.  Any words of wisdom here?

---

### Post by #&amp;thj^% on 2023-09-15
sudodus has an easy straight forward approach: [https://askubuntu.com/questions/966970/m-2-to-m-2-ssd-replace-smaller-with-larger-drive-with-a-single-m-2-slot](https://askubuntu.com/questions/966970/m-2-to-m-2-ssd-replace-smaller-with-larger-drive-with-a-single-m-2-slot)
Good luck

---

### Post by oldfred on 2023-09-15
You should not consider dd as a backup tool.

If cloning, better to do new install & restore data, or rsync data to each drive.

How re you connecting multiple NVMe drives? One at a time or with external adapters?
If not directly connected, then really just another SSD. And some internal adapters are sharing channel, so all drives then are slower.

[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2484708](https://ubuntuforums.org/showthread.php?t=2484708)
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

### Post by ken18 on 2023-09-15
Ah, I didn't mean to imply the NVMe drives were all connected at the same time. I have two internal to the laptop (one for Windows and the other for Ubuntu), and connect a third via USB-C m.2 adapter for backup/clone.  Thanks for the replies/suggestions.  I'll digest what's in the links and post again if I need to.

---

### Post by MAFoElffen on 2023-09-17
sudodus'es approach in 1fallen's link is to use Clonezilla... I use both Clonezilla (Linux) and EaseUS Partition Master (Windows).

In my kit that I used to take everywhere for Warranty Onsite Service Calls, I had my notebook, bootable USB flash drives with various OS'es and utilities, and a portable USB to dual M.2 NVMe drive caddy that I could clone drives to install a new or larger drive. The USB3.2 M.2 NVMe x2 drive caddy I have has slide-in trays for each M.2 NVMe, so is tool-less. I don't remember, but I think it was under $50 on Amazon. It's been awhile since I bought it...

Strategy: Because drives are not created equally, it is easier to clone/copy the partitions between drives and compress them in the process, then resize them to what you need them to be on the new drive. Both of the utilities I use, listed above, can compress the partitions in the copy process, then expand them. That overcomes the difference there may be in sizes on the target disk.

Not the only way, but the way I choose for me. Since I was contracted, Service Calls were paid by the call (not by the hour), so time was money.

---

