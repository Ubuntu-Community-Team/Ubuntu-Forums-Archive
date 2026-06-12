---
title: "Trouble Installing Ubuntu on Windows"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by ladubois on 2011-09-10
When I installed Ubuntu, I accidentally set it to install on my portable hard drive, instead of my PC. This drive is all that I have to back up my files with, which are still on my PC which is currently running Windows XP.
Since having installed Ubuntu, when my PC boots in Windows, it does not recognise the portable drive when I plug it into a USB port, and when booted in Ubuntu, it won't let me copy my files from the PC to the portable drive. (I get some error about not having permission or something...)

The way I see it, I need to somehow reformat my drive or something so that Windows will recognise it again so that I can reback up my files, and try again with the installing of Ubuntu.

Suggestions on how to do this/other ideas?

---

### Post by 2F4U on 2011-09-10
For me the question is what you want to do with the existing Ubuntu installation. If you want to get rid of Ubuntu, you should as a first step restore the Windows boot load into the MBR and verify that it works. After that you can reformat your portable drive from Windows and I would suggest you make backups and after that disconnect the portable drive. And finally you can install Ubuntu into the right place.

---

### Post by ladubois on 2011-09-10
Er... MBR? What's that? ...Sorry, I'm not particularly experienced with computers. More so than the average user, but not so much in comparison to most people who actually know them.
If I'm understanding what I think you are saying correctly, Windows is still running fine, and (thankfully) I left all of my original files on the computer before installation, so as soon as I can access the portable drive, I will be able to back them up again.

Here's what happens when I boot my computer. If the portable drive is not plugged in at the time, it will boot in Windows normally, since that is all that is on the machine. If I boot with the portable drive plugged in, it boots in Ubuntu off of the portable drive. I'm pretty sure it doesn't give me options, in either case but I can double check if necessary.

---

### Post by Megaptera on 2011-09-10
MBR is 'Master Boot Record' it controls Windows boot up.

If you install Ubuntu it uses Grub to overwrite (Windows) MBR - but from what you're saying you don't think this has happened to your Windows install.

---

### Post by ladubois on 2011-09-10
Correct. Windows is completely intact, from what I can tell, on my computer. But I can't access the hard drive so I can back up my files and reinstall Ubuntu while on Windows.

Also, I tried copying things from Windows to Ubuntu while running Ubuntu, but I get some sort of error about lacking permission or something...

I *think* the simplest way to fix this is to wipe the hard drive so that Windows will detect it again, but I'm unsure as to how to do this.

EDIT: I fixed it! (I believe/hope...) In Windows, I went to the Computer Management in the Administrative Tools, found the portable hardrive, deleted its partitions, then reformed and reformatted them. As soon as the reformatting is done, I will begin copying my backups to the hard drive and then begin installing Ubuntu! ^^ ...After unplugging the hard drive this time... >_>

---

### Post by Megaptera on 2011-09-11
> **ladubois said:**
> ... EDIT: I fixed it! (I believe/hope...) In Windows, I went to the Computer Management in the Administrative Tools, found the portable hardrive, deleted its partitions, then reformed and reformatted them. As soon as the reformatting is done, I will begin copying my backups to the hard drive and then begin installing Ubuntu! ^^ ...After unplugging the hard drive this time... >_>

I hope it's all solved, thanks for the update!

---

