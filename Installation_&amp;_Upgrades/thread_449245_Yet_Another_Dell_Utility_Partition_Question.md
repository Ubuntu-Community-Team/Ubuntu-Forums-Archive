---
title: "Yet Another Dell Utility Partition Question"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by corq on 2007-05-20
I inherited a healthy Dell sata drive from building a new pc for a friend - it now resides in my home-built MSI box (which plays really nicely with Ubuntu drivers thus far!)

On the former Dell Drive, I've wiped it (or thought I had) and installed ubuntu  on it - all appeared to go well.

However -- When I reboot, instead of getting grub, I'm getting the "blue bar" of the dell utility partition loading, instead of Grub/Ubuntu. The Dell prompts cites an error of some kind and never drops to Ubuntu or anything else.

How can I safely be rid of the dell utility partition? Again - it's not about the space, I need this drive to be my boot drive with Grub and the durn thing doesn't want to give me Ubuntu after reboot. I do not own a dell PC there is no further use for a recovery partition. This particular machine will never have Windows on it...I do solemnly swear I will never wish to recover the windows partintion on my pure Ubuntu machine. ;)

I've run Gparted several times looked for the parttion and it only shows me the same partition with the suspicious chunk of mb's missing from the drive size -I'm presuming the partition is hidden... is there a way to "unhide" the thing? I can do command line work but I also have other larger storage drives on the machine I'd like to not mis-identify if I can't see their common labels. If forced to I will remove the other drives to safely fdisk /mbr the damn thing but I was hoping ubuntu users had found a more graceful way.

Thanks all - I'm typically a lurker that surfs here and rarely have to ask for stuff and someone sharp has alredy posted a solution for almost everything I've encounter thus far.

---

