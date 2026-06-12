---
title: "Deleted Partition - Now what?"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by kpayton on 2011-03-06
Alright so I ran Dual Boot for a while, and I wasn't using Ubuntu as my second OS since I have it on a VM, so I went into Disk Management (From within Windows) and deleted the ubuntu partition.  now my System won't boot.  I can boot with a Windows Repair disc and get to a command prompt but it looks like everything is on the D Drive and something from ubuntu is still trying to boot the system.

Can anyone help please?

---

### Post by Hakunka-Matata on 2011-03-06
Your internal hard drive had two partitions, one for Ubuntu and one for Windows?  One NTFS or FAT32, and one Linux partition?  But you didn't use the linux partition, you'd open a VM while running Windows and run Ubuntu out of it?  Explain a bit more what you had/have.  Was Ubuntu ever installed on it's own partition on your internal disc?

---

### Post by Hakunka-Matata on 2011-03-06
You may only need to boot into windows Repair disc - C:\ and run fixmbr and/or fixboot to get your windows bootloader back.  

What version Windows are you using?

---

### Post by Hakunka-Matata on 2011-03-06
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm")

---

### Post by kpayton on 2011-03-06
> **Hakunka-Matata said:**
> You may only need to boot into windows Repair disc - C:\ and run fixmbr and/or fixboot to get your windows bootloader back.  

What version Windows are you using?


Sorry I wasn't more detailed.  

Ive booted into a Windows Repair disc and Fixmbr nor Fixboot are valid line entries.  This is Windows 7 and not windows XP.  not sure if that makes a difference.

My Data is still in tact but I believe it was because Ubuntu was the primary partition thats why it won't boot anymore.  I was basically just trying to aquire space back.  I had a 250 Gig Drive and I wasn't using Ubuntu to Dualboot anymore.

---

### Post by JBAlaska on 2011-03-06
1. Put the Windows Windows 7 installation or repair  disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type **Bootrec.exe /FixMbr** and hit enter.
   8. Type **Bootrec.exe /FixBoot** and hit enter.
   9. Reboot your computer.

---

### Post by kpayton on 2011-03-06
> **JBAlaska said:**
> 1. Put the Windows Windows 7 installation or repair  disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type **Bootrec.exe /FixMbr** and hit enter.
   8. Type **Bootrec.exe /FixBoot** and hit enter.
   9. Reboot your computer.

Perfecto Good Sir.  You rock - I am officially backup and functioning within Winblows :(

now that Im back within Windows whats the best way to get all of my space back?

---

### Post by JBAlaska on 2011-03-06
Go to administrative services, diskmanager and expand the space back to your primary win partition.

---

### Post by kpayton on 2011-03-08
> **JBAlaska said:**
> Go to administrative services, diskmanager and expand the space back to your primary win partition.

Don't see an option to expand it within Windows?

---

### Post by Hedgehog1 on 2011-03-08
You need to delete not only the visible partitions created by the Ubuntu install, but also the logical one.  Then you can expand to use the rest of the space on the disk.

Here are some pictures:

After your dual boot install:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/7512348.png?786[/IMG]

Delete swap partition:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/2982403.png?800[/IMG]

Delete Ubuntu partition:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/5434858.png?784[/IMG]

Delete logical partition:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/9703723.png?839[/IMG]

Expand to fill the space:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/4541249.png?737[/IMG]

***The Hedge***

:KS

---

### Post by kpayton on 2011-03-08
> **Hedgehog1 said:**
> You need to delete not only the visible partitions created by the Ubuntu install, but also the logical one.  Then you can expand to use the rest of the space on the disk.

Here are some pictures:

After your dual boot install:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/7512348.png?786[/IMG]

Delete swap partition:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/2982403.png?800[/IMG]

Delete Ubuntu partition:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/5434858.png?784[/IMG]

Delete logical partition:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/9703723.png?839[/IMG]

Expand to fill the space:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/4541249.png?737[/IMG]

***The Hedge***

:KS


Got it - 

I left the partition active I just needed to deleted it to get the option there to extend.

Thanks for the help guys - I now have some more space - I appeciate the help!

The Ubuntu Forums are always friendly and extremely useful!

---

