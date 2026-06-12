---
title: "Wanting to put /home on SDHC card on Acer Aspire One netbook"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by andy.stevens on 2013-02-11
Hi,

I have an Acer Aspire One netbook (one of the original A110 models) that I'm about to do a fresh installation of Ubuntu (12.10) on.  However, the SSD drive isn't especially big - 8Gb - indeed, that's why I'm doing a clean installation, as when I tried to upgrade automatically from 12.04 it ran out of space half way through and left the machine unbootable...  But since I have a spare Class 10 16Gb SDHC card lying around (which is probably as quick as the SSD since it's fitted with one of the slower drives that Acer used in these early models) and the machine has a second SD slot specifically for "expansion storage" I was thinking of putting /home on that.

I assume I can set up the relevant partitions (manually if necessary) during installation.  My first question, though, is what's the best filesystem (and parameters) to use on it to avoid excessive writes, and to avoid excessive rewrites on any one area?
For that matter, are there any similar suggestions or tips for the SSD partition(s)?  While I know SSDs are generally rated for a huge number of rewrites I figure there's no harm trying to preserve it as much as possible.

Secondly, the original linpus-based OS on this machine had the ability to automatically move the /home contents onto a card placed in that SD reader, or to swap it for a bigger card and transfer everything over.  I think I read somewhere that this is done using aufs, so my question is whether something like this can also be done with Ubuntu and how to set it up?  I don't mind if the file migration isn't automatic, so long as I know what needs to be done manually if the need ever arises...

Oh yes, and I trust I'm right to assume there's not still the problems with memory cards getting their partition table zapped one resuming from suspend? (that I saw reported in the bug tracker)

Help and suggestions gratefully received.  Thanks,


Andy.

---

