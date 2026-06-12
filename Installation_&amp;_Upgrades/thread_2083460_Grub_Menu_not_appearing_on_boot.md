---
title: "Grub Menu not appearing on boot"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by OakRaider4Life on 2012-11-12
I just helped a friend install Ubuntu on his machine alongside Windows. I did this by clearing out the Dell recovery partitions ahead of the Windows 7 partition and installing Ubuntu in the approximate 20GB space resulting.

However, we seem to have encountered some trouble. It would appear that the GRUB2 menu is not showing itself at boot time, which to mee seems to hint that GRUB2 is not detecting windows. I added the windows partition manually to the 40_custom file and ran update-grub2, but this didn't do anything to fix the issue.

What additional information can I provide for help troubleshooting this issue? Thanks in advance for any help!

---

### Post by oldfred on 2012-11-12
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Boot-Repair cannot fix most Windows issues other than booting from MBR. Do you have Windows repairCD or USB?

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

