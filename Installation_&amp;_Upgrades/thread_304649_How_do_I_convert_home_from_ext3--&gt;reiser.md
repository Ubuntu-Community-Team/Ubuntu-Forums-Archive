---
title: "How do I convert /home from ext3--&gt;reiser?"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2006-11-22
Hi,
I'm on a fresh installed 32b Kubuntu Edgy with a separate /home partition.
I prefer using the Reiser FS (at least or /home), yet during the (graphic) installation Reiser wasn't presented as one of the FS and I picked etx3 instead (although I later checked the EdDdy config file and found REiser is set up as a module).

Recently, after 30 cycles, Kubuntu tested my FS and found 15% defragmentation in my12% utilization (88 %) /home partition. That's way higher than any figure I've seen while using Reiser, thus I'd rather convert my /home to Reiser. I wonder what's the best way to do it:
1. I guess running partimage (from  Knoppix) won't wok ue the different FS? I'm I right?
2. Should I tar the whole partition (within Knoppix) to a DVD?
3. Is there a better way?
4. Is there a way to solve the defragmentation issue (and stay with ext3)?

TIA

---

### Post by cantormath on 2006-11-22
I do not know, but I believe that is something you would have to do during install.  Worse case, you could move your home onto a separate partition and then reinstall using ReiserFS.....but not entirely sure on the alternatives on this.  I have one machine on ReiserFS and its the fastest machine in my set HANDS DOWN.  Not sure if thats why.

---

### Post by streeto on 2006-11-22
partimage does not know about filesystems, it just dumps the data (correct me if I am wrong).

When I have to do this kind of thing, I copy the data to another partition, format the original partition, and then copy it back. I think it's easier and less error-prone. Just be careful to use a backup tool thar preserves file permissions and ownership, i.e. don't use 'cp -a'. For tar, that would be 'cd /home ; tar cpsf /other_part/file.tar *'.

Please read the tar manual, I am not responsible for any damage... ;)

---

