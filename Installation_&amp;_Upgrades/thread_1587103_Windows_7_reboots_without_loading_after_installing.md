---
title: "Windows 7 reboots without loading after installing Ubuntu 10.4"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by mayooresan on 2010-10-03
Hi guys,
I installed a fresh copy of Windows 7 then installed Ubuntu 10.4 on another partition.

When I load, the system shows Win 7 and Ubuntu int he loader but whenever I choose the Win 7 system restarts in a loop.

But if I choose Ubuntu it works fine. No idea wot happned. Can someone tell me what to do?:confused::confused::confused:

---

### Post by Mark Phelps on 2010-10-03
How did you create the other partition?  Did you do it (properly) by (1) shrinking the Win7 OS partition using the Win7 Disk Management tool, (2) leaving the space unallocated, and (3) selecting the use largest free space option in the Ubuntu installer and letting IT format the unformatted space?

Or did you shrink the Win7 partition using GParted, or allow the Ubuntu installer to shrink the Win7 partition?

If the first, don't have an answer because that is the right way to do it and should not damage Win7 in the process.

If the second, you likely corrupted the Win7 boot loader using GParted and will have to restore that using either a Win7 Repair CD (you DID make one while Win7 was working, right?) or a Win7 Installation DVD.

---

### Post by mayooresan on 2010-10-04
> **Mark Phelps said:**
> How did you create the other partition?  Did you do it (properly) by (1) shrinking the Win7 OS partition using the Win7 Disk Management tool, (2) leaving the space unallocated, and (3) selecting the use largest free space option in the Ubuntu installer and letting IT format the unformatted space?

Or did you shrink the Win7 partition using GParted, or allow the Ubuntu installer to shrink the Win7 partition?

If the first, don't have an answer because that is the right way to do it and should not damage Win7 in the process.

If the second, you likely corrupted the Win7 boot loader using GParted and will have to restore that using either a Win7 Repair CD (you DID make one while Win7 was working, right?) or a Win7 Installation DVD.

1. I formated the whole Disk using GParted
2. Partitioned using Gparted
3. Installed Ubuntu
4. System boots fine
5. Installed Win 7
6. System didn't even show Win 7 in Boot menu as Windows overwritten it
7. searched for the command to install "Grub 2"
8. Run something like update grub
9. System booted fine and I could see Win 7 as well as Ubuntu 1.4 in Boot menu 

thanksk for your details reply buddy :popcorn:

---

### Post by Mark Phelps on 2010-10-04
OK, I'm confused ...

In your first post, you said you installed Win7 and THEN Ubuntu.

In your last post, you said you installed Ubuntu and THEN Win7.

Both can't be true ... which did you do?

If you formatted the NTFS partition with GParted and THEN installed Win7 to it, that's likely the problem because Win7 (like Vista) has problem with partitions it didn't format itself.

---

### Post by oldfred on 2010-10-04
Post results.txt so we can see what you have:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by mayooresan on 2010-10-05
> **Mark Phelps said:**
> OK, I'm confused ...

In your first post, you said you installed Win7 and THEN Ubuntu.

In your last post, you said you installed Ubuntu and THEN Win7.

Both can't be true ... which did you do?

If you formatted the NTFS partition with GParted and THEN installed Win7 to it, that's likely the problem because Win7 (like Vista) has problem with partitions it didn't format itself.
Initially i have installed Win 7 and then Ubuntu. It didn't work out as I said in the first post. But as I said in the secound post, later I have formatted the whole hard disk and partitioned it using Ubuntu Live CD and installed Ubuntu first.

Anyways now system is working fine :) thanks a lot for ya time.



> **oldfred said:**
> Post results.txt so we can see what you have:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

thanks. System is working now. :)

---

