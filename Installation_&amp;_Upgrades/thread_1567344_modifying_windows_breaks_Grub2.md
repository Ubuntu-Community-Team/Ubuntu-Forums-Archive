---
title: "modifying windows breaks Grub2?"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by jadedcritic on 2010-09-03
I'm a little hazy on whether or not this has already been posted or if it's in the right topic category, but it strikes me as worth discussing.  Still trying to get my head around it.  

I think this actually happened to me, without telling too long a story, I was scrubbing bloatware off my Dell box and my GRUB quit working.  I didn't think too much of it at the time, but TADA! [http://tinyurl.com/2ce54gy](http://tinyurl.com/2ce54gy)

(Quote) This is a bug in which some proprietary Windows-based software overwrites particular sectors in the gap between the master boot record and the first partition, sometimes called the "embedding area". GRUB Legacy and GRUB 2 both normally use this part of the disk to store one of their key components

Looks like the Debian guys figured this out??

Well, if it's already been posted, I apologize.  I didn't manage to find it after 10 minutes or so of searching, but this strikes me as a really good thing to be mindful of for those of us with Win/Linux dual boots.  I honestly never seriously thought that removing windows elements could potentially breka the bootloader!

---

### Post by oldfred on 2010-09-03
WE have seen the issue but now the grub team is looking for  a work around for windows software that does not follow the rules. The area is for booting not hiding info you do not want overwritten.

Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

