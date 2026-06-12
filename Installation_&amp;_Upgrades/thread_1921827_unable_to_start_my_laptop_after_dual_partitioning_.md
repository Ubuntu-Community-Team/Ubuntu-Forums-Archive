---
title: "unable to start my laptop after dual partitioning with windows 7 and ubuntu 11.10."
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by ohnoplus on 2012-02-07
I am unable to start my laptop after dual partitioning with windows 7 and Ubuntu 11.10.
More specifically:
I had windows 7 professional installed on my computer; it worked fine.
I partitioned my hard drive and installed Ubuntu on a new partition.  Restarted the computer, selected Ubuntu through GRUB and had no problems.
Restarted the computer and started windows 7 through grub.  It ran check-disk as the repartition caused it to "detect problems or some such" and then started up.
I then tried reboot the computer, which is when the problems began.  Now when I boot from the hard drive I get the HP logo and the message press ESC key for startup menu and a picture of a battery with a plug.  [I am running an HP Probook 6445b].  That stays on for maybe half a second and then goes off.  Then flashes back up, then off and on again ad infinitum.
I can boot from a CD no problem.  I tried reinstalling GRUB2 (not 100% sure it woked though).  The reinstall didn't seem to do anything.  I also tried reinstalling Ubuntu, no luck there either.

I am happy to provide any more information you all may need. Thanks in advance for any assistance.

---

### Post by jerrrys on 2012-02-08
You may have to settle for repairing windows until you find an answer.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+windows+7&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+windows+7&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2012-02-08
You should be able to reinstall grub2 to the MBR to boot Ubuntu or install the Windows boot loader to boot Windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Are you running any DRM software, HP software or agressive virus checker that thinks grub is a virus? Grub2 has since added a workaround on flexnet but not others that I know of.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html")
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

If you have to run your DRM software you can boot with Windows and use EasyBCD. It becomes a work around on grub2/Uubntu that is less reliable. On grub udates you may have to reinstall grub to the PBR.

I have not used this, asa I prefer grub2, but a few that primarily boot Windows have said it works:
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Edit - an older post had this:
> I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that ****. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!

---

