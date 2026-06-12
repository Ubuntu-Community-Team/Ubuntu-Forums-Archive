---
title: "Fresh whiped hard drive, no errors during install, get grub rescue after reboot"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by JamesDonaldChilds on 2011-10-20
I'm installing 10.10 any help or idea why it instakls perfectly with no errors and I'm completely wiping the disk yet it still results in grub rescue after reboot?

---

### Post by oldfred on 2011-10-20
Welcome to the forums.

From liveCD run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Or download this which can run script and may be able to do minor fixes.
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by JamesDonaldChilds on 2011-10-20
What is that that I am running? I just did another FRESH install to a different hard drive and same error... I'm thinking my computer just won't accept Ubuntu for some reason...

---

### Post by oldfred on 2011-10-20
Are you installing to a very large hard drive with just one very large system partition? There have been some errors with that. It is best to keep system partition at 20 or GB and let the rest be /home. You have to use manual install to be able to create /home partition.

---

