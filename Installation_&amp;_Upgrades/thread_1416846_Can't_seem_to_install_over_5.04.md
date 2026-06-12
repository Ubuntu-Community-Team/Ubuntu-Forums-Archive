---
title: "Can't seem to install over 5.04"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by MeanRoy on 2010-02-26
I downloaded the latest release, burned a disk and successfully booted.

When it comes time to choose a partition I don't have the option of replacing the old release. I can install in parallel leaving both but can't use the whole disk.
Interestingly enough I CAN replace the windows installation.

Of course I already have Grub installed but I don't see how this would affect installing.

Can someone clue me in here?

Roy.
---------
Ok I read the article here [http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml) and it seems I may have missed a step.
However it's implied I will lose the current Grub installation. Is that the case?

---

### Post by oldos2er on 2010-02-26
You need to use the "specify partitions manually" option to point the installer to 5.04's partition.

Ubuntu 9.10 uses grub2, which will replace legacy grub.

---

### Post by MeanRoy on 2010-02-26
> **oldos2er said:**
> You need to use the "specify partitions manually" option to point the installer top 5.04's partition.

Ubuntu 9.10 uses grub2, which will replace legacy grub.

Thanks.
I had figured I needed to *specify partitions manually*, but wasn't sure what would happen with Grub.

May I presume Grub2 will preserve the other OS info?

Roy.

---

### Post by recluce on 2010-02-26
> **MeanRoy said:**
> Thanks.
I had figured I needed to *specify partitions manually*, but wasn't sure what would happen with Grub.

May I presume Grub2 will preserve the other OS info?

Roy.

It will not "preserve" but redetect. Windows XP is always detected, Vista and Windows 7 seem to be detected fine 99% of the time. If you have multiple Linux installations, you might prefer a dedicated Legacy GRUB partition and chainload into the individual boot loaders (whatever they are, NTLDR, LILO, GRUB1, GRUB2 etc) from there. Let me know if that is your situation and I will post a few pointers.

---

### Post by MeanRoy on 2010-03-03
Thanks for the help, I just finished the installation as was suggested.

The only caveat is that formerly I had a partition used as a swap. The installer wiped that and used the whole disk.
It doesn't appear to be a problem as I don't actually recall why it was done that way. (I had one of my Sons Guru buddies help me out with the original installation of 5.04)

The only thing I haven't got working so far is my local network. I'm scanning through the various help files and threads looking for the answer but no luck so far. I get the message"Unable to mount location Failed to retrieve share list from server" when I double click on "Windows Network".

Roy.

============ edit ==
I was wrong, it did preserve the partition, I just didn't realize what I was looking at. Duh.
Local network still inaccessible.

---

### Post by recluce on 2010-03-03
> **MeanRoy said:**
> Thanks for the help, I just finished the installation as was suggested.

The only caveat is that formerly I had a partition used as a swap. The installer wiped that and used the whole disk.
It doesn't appear to be a problem as I don't actually recall why it was done that way. (I had one of my Sons Guru buddies help me out with the original installation of 5.04)

The only thing I haven't got working so far is my local network. I'm scanning through the various help files and threads looking for the answer but no luck so far. I get the message"Unable to mount location Failed to retrieve share list from server" when I double click on "Windows Network".



You would probably do better by starting a new thread about the networking problem.

---

