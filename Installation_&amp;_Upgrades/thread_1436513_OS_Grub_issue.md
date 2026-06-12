---
title: "O/S Grub issue"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Abundance_Linux on 2010-03-22
Linux Crew,

Well, i had a dual O/S win Vista 64bit & unbuntu 9.10 64bit.

1. Had a virus on my Win vista side, anti virus could help (virus kept replicating itself - to halt all progs from running).

2. In the End Win Vista would start & was only used Unbuntu for about 2 days.
3. Tried to repair Win Vista, but noting worked.
4. Couldn't mount Win partition through unbuntu either - needed to copy some files across.
5 Eventually formatted Win partition side & re-installed Win Vista 64bit.
6 The problem now is that the grub option to select the O/S choice isn't there, thus i can't use Linux.
6b. The computer loads only Win vista 64bit (Like there usn't a Linux)
7 Checked at the disk management prog - could see my linux  space but have no access.
8. Used a live Linux cd to access linux partition, just to check - it worked.
9. how can i acccess the Linux O/S as normal?

Help?
AL

---

### Post by drs305 on 2010-03-22
Do you see a Grub menu at all?  If you were using Grub 2 and want to reinstall G2, boot to the Live CD Desktop and open a terminal, then run:

```
sudo mount /dev/sd**XY** /mnt
sudo grub-install  --root-directory=/mnt/ /dev/sd**X**
```
Note you mount the partition (e.g. sd**a5** but you *install* to a drive (sd**a**) and not the partition).

You may need to run "sudo update-grub" after you boot into linux for the first time to let Grub 2 find your Windows install.

Here is the community doc section on reinstalling Grub 2 from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

