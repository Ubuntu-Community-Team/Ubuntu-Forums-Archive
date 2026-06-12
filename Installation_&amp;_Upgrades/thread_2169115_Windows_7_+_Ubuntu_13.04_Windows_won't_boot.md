---
title: "Windows 7 + Ubuntu 13.04: Windows won't boot"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by sgehlich on 2013-08-20
Hey,

I just installed Windows 7 on my new Asus N550JV notebook. It runs perfectly fine. Afterwards, I installed Ubuntu 13.04 from a USB stick, on the installation i chose "Install Ubuntu next to Windows 7". The installation worked fine and it restarted.

But then it did not show the GRUB menu but it automatically booted into Windows 7. So I googled around and found out that boot-repair could fix that problem. I installed boot-repair in a Live CD session and chose the recommended repair. It did some stuff and asked me to do some stuff.

After I restarted, I saw the grub menu. I could successfully boot into Ubuntu. But when I chose one of the two (why two? /dev/sda1 and /dev/sda2?) Windows 7 installations, the screen stayed purple (like the GRUB menu). I waited a few seconds and heard the Windows 7 login-sound, but the screen stayed purple.

When I chose the first of the two Windows 7 installations, the screen stayed purple but I could not hear anything.

Here is my boot-repair info: [http://paste.ubuntu.com/6007744/](http://paste.ubuntu.com/6007744/)

Hope somebody can help me :)

---

### Post by oldfred on 2013-08-20
So many users have just deleted the (hidden) 100MB boot/repair partition as they do not know what it is and then cannot boot. So boot repair at backs up bootmgr to the main install. Then grub2's os-prober see the boot files in both sda1 and sda2 and gives you entries to both. Not sure if sda2 also has the BCD?

Is Windows hibernated? or does it need chkdsk? If resized it needs a chkdsk to reset internal partition size data in Partition boot sector. Grub typically only boots working installs of Windows and hibernation or chkdsk are most often the main issues.

---

### Post by sgehlich on 2013-08-20
I did not do anything to the 100MB partition. Windows told me it would create it so I was like "Okay, go on".  What is "the BCD"?

I installed Windows 7 on a totally empty disk, then installed Ubuntu after Windows 7 ran for the first time. I don't know whether it needs chkdsk since I don't see any output from Windows at all.

---

### Post by ukbeast on 2013-08-20
Try this tutorial [https://www.youtube.com/watch?v=xK8X7_tYWmA](https://www.youtube.com/watch?v=xK8X7_tYWmA)
in partitions, delete the ubuntu 13.04 sector in partitions menu and use that free space for the installation

---

### Post by sgehlich on 2013-08-20
> **ukbeast said:**
> Try this tutorial [https://www.youtube.com/watch?v=xK8X7_tYWmA](https://www.youtube.com/watch?v=xK8X7_tYWmA)
in partitions, delete the ubuntu 13.04 sector in partitions menu and use that free space for the installation

I just tried it exactly like that, but afterwards Windows 7 boots up instead of the GRUB menu.

EDIT:

I now reinstalled grub on /dev/sda as described here: [http://superuser.com/questions/374486/ubuntu-11-10-doesnt-boot-after-installation-only-boots-into-windows-7](http://superuser.com/questions/374486/ubuntu-11-10-doesnt-boot-after-installation-only-boots-into-windows-7)

Now I see the grub menu and only one Windows 7 install, but if I select it, I have the same issue: Purple screen, but I can hear the Windows 7 startup sound

---

### Post by oldfred on 2013-08-20
Boot-Repair does not fix most Windows boot issues. You may need to use Windows repairCD or flash drive to fix Windows.

       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

    
 [http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by sgehlich on 2013-08-20
> **oldfred said:**
> Boot-Repair does not fix most Windows boot issues. You may need to use Windows repairCD or flash drive to fix Windows.

Wouldn't that overwrite the MBR so that I wouldn't be able to boot into Ubuntu anymore?

---

### Post by Quackers on 2013-08-20
Yes it will but at the moment your biggest need is to get Windows booting normally again.
Repair/overwrite the MBR with Windows code and get Windows booting. Then run a chkdsk until no errors show and reboot into Windows.
At that point you can re-install Grub2 to the MBR from the live cd and all should then be good.

The 2 entries for Windows should both boot Windows normally iirc.

---

### Post by sgehlich on 2013-08-20
I now "repaired" the startup with the Windows install disk - and although it said that it could not find any errors, it now works perfectly fine - for now.

Thanks so far!

---

### Post by Quackers on 2013-08-20
So Windows now boots ok but you have no menu item for Ubuntu - is that correct?
If so I would still run a chkdsk on Windows as it has been re-sized by a non-Windows program. Once no errors are found you should reboot into Windows again to make sure it's still ok.
At that point you can put Grub2 back in the MBR and you should be ok to boot both systems.

---

### Post by sgehlich on 2013-08-20
No - I can see the Grub menu and both Ubuntu and Windows 7 work fine :)

---

### Post by Quackers on 2013-08-20
Interesting  :D
All's well that ends well!
Happy Ubuntuing!

---

### Post by sgehlich on 2013-08-20
Thanks mate! I have no idea what happened - but I'll mark this as solved for now. :) (EDIT: If I knew how!)

---

### Post by Quackers on 2013-08-20
Good idea, it'll help other people when searching.
Not exactly sure what happened myself :D
It's fixed though!

---

### Post by Quackers on 2013-08-20
I just noticed your topic heading includes the wubi prefix. This isn't a wubi installation is it?

---

### Post by sgehlich on 2013-08-20
No it's not!

---

### Post by Quackers on 2013-08-20
I thought not. It may be an idea to edit that to "Ubuntu" so that people searching will know this thread refers to a dual boot system, not a wubi install.

EDIT if you're not sure how to do that just go to your original post and click on the edit post (bottom right) then when the edit window opens click on "go advanced" and that should then give you the option of changing the wubi prefix to Ubuntu.

---

### Post by raidsteel on 2014-02-08
My problem was almost the same. New laptop, dual-boot (Windows7 - Ubuntu12.04), ubuntu boots perfectly but Windows 7 is stuck in the Purple screen after I select it in grub! I tried everything you were talking about, but nothing seems to fix the problem permantly! The odd think that windows were starting normally I could hear all the sounds, and I could turn off the laptop normally from the keyboard "blindly" (Windows Button -> Right Arrow -> Enter :P ). Startup repair from windows CD did help but only the first time I booted my computer, windows were entering like a charm and in the second time the purple screen of death was back and I had to repeat the procedure with the startup repair.

Anyway to make a long story short, After a lot of reading and guessing I was starting to thing that the resolution of grub was messing something up. I did some testing and finally set it to the lowest most common 640x480. And that did the trick! A week of frustration but finally is working! I provide a link how to do it.
[http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

I don't know if it's related to this problem, but the initial problem were the same. So I though I would write my story in this thread in case someone in the future has the same problem :) !
Guys I really thank you best wishes!

---

