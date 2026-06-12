---
title: "Triple boot - XP Vista Ubuntu"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by FredKornyev on 2008-10-06
Hey Guys,

Here is the problem: I would like to have XP (or actually Windows Server 2003, but it's all the same), Vista and Ubuntu on the same machine. I have dual booted XP/Ubuntu and Vista Ubuntu before and it worked fine. This time I started by dual booting XP/Vista and used the [http://www.syschat.com/dual-boot-vista-xp-vista-already-1946.html?garpg=4](http://www.syschat.com/dual-boot-vista-xp-vista-already-1946.html?garpg=4) guide, because I wanted to avoid using any programs to edit the boot file.

But now I come to install Ubuntu, and sure enough, installs fine, but when GRUB appears and I choose Vista/Longhorn loader it just gives me a bunch of colored lines with random characters, and the pattern is different every time I try it.

Anyway, I restored my dual boot system (backed it up before installed Ubuntu) and tried again, but still the same. I am looking for a solution, but in the mean time I thought someone may possibly come across this thread and save me some time and possibly help others.

Thanks!

---

### Post by Braytok on 2008-10-06
getting that particular setup to work can be VERY tricky. Triple booting a linux OS and 2 Windows OSes is some task.

What I would do if it were me would be to install one OS that I would like to be my main one then install VirtualBox or Vmware 
[http://www.virtualbox.org/](http://www.virtualbox.org/) 
[http://www.vmware.com/](http://www.vmware.com/)

then install the other 2 OSes as guest.

---

### Post by caljohnsmith on 2008-10-06
I've helped other people in exactly your situation to successfully triple boot Vista, XP, and Ubuntu, so it is certainly possible and usually not too big a deal to get working. When you installed XP and Vista, did you leave space on the drive for Ubuntu? Or did you use Ubuntu's partition editor (gparted) to make space? That can be an issue, because it is highly recommended to use Vista's Disk Management to do any partitioning since Vista exists on the drive. The reason is that Vista maintains its own partition table outside of the main partition table in the HDD's MBR (Master Boot Record), so if you use anything other than Vista to do your partitioning, Vista's partition table won't be updated with the changes and it can break Vista. 

Also, please post:
```
sudo fdisk -lu
```
And identify which partitions belong to which OSes, and we can work from there if you like.

---

