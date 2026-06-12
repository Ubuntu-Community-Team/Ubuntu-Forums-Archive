---
title: "Need Help, Can't Boot Vista After Installing Ubuntu"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by chorizo on 2008-10-04
Hey all,

I am a long time windows user and highly experienced with that OS, however I am a complete newb when it comes to Linux. I followed some instructions I found on the net to install Ubuntu after Vista was already installed. I thought I followed them correctly, but when I get to the grub screen, if I select the Vista loader, it just reloads grub and nothing else happens. I can get into the recovery partition for Vista just fine, but I can not get into the OS. 

Ubuntu seems to boot perfectly. This is an HP Laptop, I do not have a Vista disk. I do have the capability to reformat and reinstall windows from the recovery partition and I have already done so once trying to get this to worl, but when I installed Ubuntu again, the same thing happened. 

How do I fix this? I'd like to use Ubuntu for just about everything and keep Vista around for games.

---

### Post by chorizo on 2008-10-04
To add:

I just noticed that it appears the vista partition is completely gone. I am not sure if its there and just not recognized by Ubuntu or what?

---

### Post by jerome1232 on 2008-10-04
It might be that vista decided uses ntfs differently than xp did. Since ntfs is a closed file system they don't release the changes they make and 3rd party utilities (like gparted that's what comes with ubuntu) will sometimes corrupt the ntfs disk when resizing it becuase they are not aware that vista has changed things. 

As a workaround You should be able to shrink vista's drive from within vista itself, then install Ubuntu into the freed up space.

---

### Post by caljohnsmith on 2008-10-04
The behavior you describe where Grub "reloads Grub" when you choose Vista typically happens when you accidentally install Grub to the boot sector of the Vista partition; thus when Grub tries to boot Vista by booting its partition's boot sector, Grub boots the Grub in Vista's boot sector and reloads itself. 

To start, I would download a Windows Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you get that, boot it up, go to the command line, and then run:
```
bootrec /fixboot
```
That will make sure you Vista partition has a Vista boot sector, not Grub. Most likely that will fix your problem, but if it doesn't, then please post the output of:
```
sudo fdisk -l
```
and we can work from there.

---

### Post by chorizo on 2008-10-05
Thanks for the tips. I just moved and have a lot of unpacking ahead of me. When I am done, I will try what you suggested and let you know.

---

