---
title: "ISO CD no log - can see files instead ?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Babak on 2008-04-24
I burned an ISO image onto CD using Nero. Instead of giving me the ubuntu logo, I see the name of the CD and the files instead, this is really weird...

WTF?

Here's a screengrab:

[IMG]http://img46.imageshack.us/img46/5619/ubuntuinstallisomn5.png[/IMG]

---

### Post by Partyboi2 on 2008-04-24
Make sure you burn it as a iso image not as data. If the problem still persists try using another program like imgburn
[http://www.imgburn.com/](http://www.imgburn.com/)

Edit:  What do you mean by ubuntu logo? Are you meaning the ubuntu logo that comes on screen after you have booted the live cd from a system restart?

---

### Post by Babak on 2008-04-24
yeah this is really confusing... if it was data then it should be showing me just one file, not the breakdown of file/folders, etc.

I've used two programs so far, Nero and CDBurnerXP Pro 3 they've both given me the same results.

Can someone please tell me what the proper result is supposed to look like? or what the proper CD result is supposed to do exactly?

that is upon insertion of CD, etc...

thanks!!

---

### Post by Partyboi2 on 2008-04-24
The process should be something like
download the iso 
check md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))
burn the image as a iso to disk ([https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto))
After the burn is finished reboot system making sure that in the bios the cd is see to boot first.
Ubuntu main menu screen should appear where you check cd for defects. Then install

---

### Post by Babak on 2008-04-24
reboot? huh? what about WUBI? doesn't that allow me to install ubuntu just as any other app under windows?

thanks

ps just burned another CD with imgburn... so far I'm just making coasters since they all do not show the ubuntu logo at MyComputer window and instead show the files/folders inside

---

### Post by Partyboi2 on 2008-04-24
If you are using wubi you should download the wubi program [http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)  and run it.

---

### Post by Babak on 2008-04-25
ok I installed wubi and ran it but it gives me an "Error 15"!

something about my NTFS drive? strange, any idea what that may be about?

---

### Post by Partyboi2 on 2008-04-25
Found this on the wubi page
> **Booting problems: Error 15, file not found**

  A common reason is that Wubi does not support software raid (aka fakeraid), you have to install into a partition outside of the raid array. Pure hardware raids should be ok. 
 Another possible cause of problems is if you used an Alternate ISO instead of a Desktop ISO with Wubi 8.04.  
 If your filesystem is corrupted that can also create booting problems, please run "chckdsk /r" from within a Windows DOS terminal within the drive where you installed Wubi. 
 Often installing Wubi on a different disk/partition will work.


---

