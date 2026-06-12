---
title: "Does 13.04 Desktop support raid and is there a GUI tool for setting raid after instal"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by prcdslnc13 on 2013-06-10
Hi, 
I recently setup a media server using 13.04 and Ubuntu Desktop. I now am wanting to add in two 2tb drives in RAID 1 with software, and set them up as a network drive for all my other PC's. Im not after speed, just reliable file sharing and backups. 

Ive searched this but most of the posts are from 2009-2010 era. Some of the tutorials I have read state that the kernel included with Desktop does not support RAID. I am also looking for a GUI setup for my raid config. I have seen lots of tutorials for mdadm and it doesnt look too terrible, It would just be nice to have a gui :D

Any help you guys can give would be fantastic. 

Thanks

---

### Post by prcdslnc13 on 2013-06-11
No one?

---

### Post by oldfred on 2013-06-11
Somewhere I saw they made the kernels identical.

They did away with the alternative installer which supported RAID but then did not get all the RAID support into the desktop. You have to manually add drivers.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)

> There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 

[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 

[/LIST]


---

### Post by steeldriver on 2013-06-11
If you already have the system installed on a separate disk (i.e. not one of the 2TB ones that you want to RAID) then adding support for RAID should just be a matter of installing the mdadm package on that system - that's basically how I set up my HTPC (on Mythbuntu 11.04)

I'm not aware of a GUI for the actual setup though

---

### Post by ladasky on 2013-06-11
> **steeldriver said:**
> If you already have the system installed on a separate disk (i.e. not one of the 2TB ones that you want to RAID) then adding support for RAID should just be a matter of installing the mdadm package on that system - that's basically how I set up my HTPC (on Mythbuntu 11.04)

I was told that downloading **mdadm** while running from the 13.04 live DVD would allow me to install 13.04 onto my existing RAID1.  It *almost* worked.  I ran into trouble, as you can see _[here]("http://ubuntuforums.org/showthread.php?t=2140218")_ and _[here]("http://ubuntuforums.org/showthread.php?t=2153652")_.  It may be necessary to have partitioned your hard drives with LVM rather than with MBR.  Does anyone have an opinion about that?  Please share...

(Aside: now that Ubuntu has finally decided that they will not be constrained by the size of a CD-ROM, I don't see why they didn't just include **mdadm** in the 13.04 ISO.  It's only 1.2 megabytes.)

---

### Post by prcdslnc13 on 2013-06-12
> **steeldriver said:**
> If you already have the system installed on a separate disk (i.e. not one of the 2TB ones that you want to RAID) then adding support for RAID should just be a matter of installing the mdadm package on that system - that's basically how I set up my HTPC (on Mythbuntu 11.04)

I'm not aware of a GUI for the actual setup though


That seems to be the way to go from what Im reading. It scares me though with how much Im reading that release upgrades breaking arrays. Is this as much of a worry as I think? Im beginning to think that using the raw disk space and do good backups might be a better plan

---

### Post by steeldriver on 2013-06-12
Well I've not heard that - but it shouldn't be one or the other - the ONLY thing RAID1 gives you is availability in the event of a single disk failure, you still need backups as well

---

### Post by prcdslnc13 on 2013-06-12
Valid point sir.... valid point

---

