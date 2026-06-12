---
title: "Ubuntu+Kubuntu dualboot UEFI both use /boot/efi/EFI/ubuntu how toget seperate entries"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by interzoneuk on 2012-11-05
Hi

I have a UEFI system running various OS's.

i.e

opensuse, arch, ubuntu, kubuntu

My issue is that both ubuntu + kubuntu share the same UEFI folder - /boot/efi/EFI/ubuntu meaning that when I install the 2nd (of the 2 ubuntu based os's) it overwrites the previous UEFI entry.

I can still access the other on via grub, however I like to use rEFInd to boot into os's, I believe it detects os's my folder within /boot/efi/EFI/

How can I change it so that kubuntu fo example uses /boot/efi/EFI/kubuntu ? and thus has a seperate entry with the UEFI menu ?

(i.e opensuse, arch are fine as they have seperate UEFI entries anyway.)

---

### Post by oldfred on 2012-11-06
You may want to file that as a bug and see if developers have a fix or not.

Not sure if really different than one MBR and many grub menu entries. Can you not run sudo update-grub and get multiple boot entries in the grub menu of which ever system you boot? Or do all entries have to chain back to the efi partition like chain loading to Windows does.

bug reports info on how to do, you do need separate sign on to launchpad:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Check for similar bugs ( I looked at grub-efi and did not see any similar, but not eveyone would know it is grub-efi)
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

### Post by interzoneuk on 2012-11-11
done so thanks

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1077643](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1077643)

---

