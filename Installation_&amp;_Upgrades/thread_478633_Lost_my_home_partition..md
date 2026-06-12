---
title: "Lost my home partition."
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by PaulFXH on 2007-06-19
I have a multiboot system on my desktop including Feisty, Debian, Zenwalk and Windows XP.
The Linux part of the HDD is heavily partitioned and each distro has both a root and a home partition. Only one Swap partition is available and is "shared" by all three distros.
Ubuntu's Grub is installed on the MBR while the Grub from the other distros I've just put on the appropriate root partition.
This worked fine for almost a year then, for various reasons, I had to clean install Debian. This went fine but it seems that this operation totally messed up the Home partition belonging to Ubuntu.
How do I know? Well, when I tried to boot into Ubuntu the X server didn't open giving as an error message that my Home directory didn't exist although it still clearly showed up in GParted.
Then I tried to force an fsck on ALL the ext3 partitions. It checked every single one EXCEPT for my Ubuntu home.
The only way to get things back to normal was to format this partition.
However, I'm puzzled as to why installing something on another partition should have nuked one of my Ubuntu partitions.
As this is something that I may well have to do again, I'd welcome comments from anybody who thinks they might be able to explain what went wrong here because I can't.

---

### Post by floke on 2007-06-19
You don't know it was borked - it could have been an ownership issue or a broken gnome config. This has happened to me a couple of times and chucks the same error. Did you try deleting all the .gnome etc. config files, along with the .Xauthority etc. stuff?

---

### Post by PaulFXH on 2007-06-19
> **Steve.K said:**
>  Did you try deleting all the .gnome etc. config files, along with the .Xauthority etc. stuff?
No, I didn't as I wasn't aware this might help me.
Could you perhaps point me to a link where I can read about this in case this happens to me again (and I'm a great believer in the veracity of Murphy's law).
Best wishes
Paul

---

