---
title: "FYI: How to uninstall Ubuntu on dual boot Windows XP using Windows only"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by bobmorris on 2008-02-08
My Ubuntu installation which has dual boot on Windows XP got hopelessly trashed. Endless command line errors upon booting. After much searching, I found an easy way to uninstall it using Windows only.

I just did it. It took about three minutes and worked flawlessly. Hope this helps someone else. (And now I can reinstall Ubuntu!)

a) Use Disk Manager in Windows to delete the Ubuntu partitions.

b) Boot off your Windows XP CD.

-Choose "Repair"

-When it asks for the installation number, I put in "1", and it worked fine (you may want to test this first to be sure.)

- Enter Admin password

-at the command prompt type "fixmbr", then confirm. Windows will overwrite the dual boot info in the MBR that Ubuntu put there.

- Reboot!


Here's full information:

Uninstall Ubuntu using Windows
--------------------------------------
[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/1800](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/1800)

suppose you are running Windows. If so, follow these steps:
1) In Windows, launch Disk manager and remove every partition used by Ubuntu (root partition, swap, ...)
2) Reboot with your Windows CD. When asked, choose "reapair" and launch fixmbr. This command replaces GRUB with Windows bootloader.
3) Reboot again and you have done.

Once you are done, it you want to recover the space for Windows that was once used by Ubuntu. You can use the steps outlined above (going the the Disk Manager, etc). To create a new NTFS partition and assign it as something like the D: drive (or some other letter) to be used for data and so forth.


Disk Manager
---------------
[http://support.microsoft.com/kb/309000](http://support.microsoft.com/kb/309000)

How to use Disk Management
To start Disk Management:
1.	Log on as administrator or as a member of the Administrators group.
2.	Click Start, click Run, type compmgmt.msc, and then click OK.
3.	In the console tree, click Disk Management. The Disk Management window appears. Your disks and volumes appear in a graphical view and list view. To customize how you view your disks and volumes in the upper and lower panes of the window, point to Top or Bottom on the View menu, and then click the view that you want to use.
NOTE: Microsoft recommends that you create a full back up of your disk contents before you make any changes to your disks or volumes.

---

