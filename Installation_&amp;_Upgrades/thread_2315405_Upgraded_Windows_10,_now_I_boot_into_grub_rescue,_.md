---
title: "Upgraded Windows 10, now I boot into grub rescue, and my ubuntu partition is gone?"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by Pengatom on 2016-02-28
I have a dual boot machine with ubuntu and Windows 10 on it. Today windows update forced me to update wine, and after a reboot grub goes into rescue mode.
If it had just overwritten my boot loader, I guess I could get it to work again, but according to this [http://paste.ubuntu.com/15231827/](http://paste.ubuntu.com/15231827/) I cannot see my ubuntu partition any more?
Is it gone or what?

The 160gb disk should be half windows and half ubuntu, I don't understand what happend here? Or is it something I don't see?

Any help would be highly appreciated!

---

### Post by yancek on 2016-02-28
> I have a dual boot machine with ubuntu and Wine10 on it.

Did you actually mean "windows 10"?  windows always messes up the booting but you should then be able to boot windows which is apparently the case.  I've read other posts here indicating that updating windows 10 causes problems with the partition table.  If you look at the output from fdisk, you can see that the beginning of the Extended partition (sda4) does not correspond to the beginning of the swap partition (sda5) so your filesystem partition is still there.  You should be able to fix that but I have no idea how so maybe you can find an answer with google or someone with more knowledge on the subject will post. 

> /dev/sda4         167,317,502   312,580,095   145,262,594   5 Extended 
> /dev/sda5         292,581,376   312,580,095    19,998,720  82 Linux swap / Solaris 

---

### Post by Pengatom on 2016-02-29
Hi yancek!

Thanks for replying to my post!
After you mentioned this about the sizes don't add up, I googled some more, and found this: [http://ubuntuforums.org/showthread.php?t=1775331&page=3](http://ubuntuforums.org/showthread.php?t=1775331&page=3), might try this when I come home today.

For me it just looks like the partition is gone, but maybe there is hope after all!

---

### Post by oldfred on 2016-02-29
I did not realize I had been posting essentially the same instructions since 2011. :)

And of course the bug in Windows has not been fixed since long before that. It just forgets to write a logical Linux partition. 

New threads, but essentially same info in all of them:

 sudo parted /dev/sda unit s print
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by Pengatom on 2016-02-29
Turns out it was really easy:
> [COLOR=#000000]*sudo sfdisk -d /dev/sda > PT.txt*[/COLOR]

[http://www.gnu.org/software/parted/m...de/rescue.html]("http://www.gnu.org/software/parted/manual/html_node/rescue.html")

[COLOR=#000000]*sudo parted /dev/sda unit s print*[/COLOR]

[COLOR=#000000]*sudo parted*[/COLOR]
[COLOR=#000000]*unit s*[/COLOR]
[COLOR=#000000]*rescue*[/COLOR]
[COLOR=#000000]*input start & end and see if it finds partition*[/COLOR]

---

