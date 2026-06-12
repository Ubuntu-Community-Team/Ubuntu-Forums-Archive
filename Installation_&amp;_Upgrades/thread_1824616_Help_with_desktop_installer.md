---
title: "Help with desktop installer"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by FMS.SouL on 2011-08-14
I'm currently using window 7 and I planning to install ubuntu desktop in same pc without remove my window7,should I download Ubuntu(Original edition) or widow installer called (Wubi).

---

### Post by Actonix on 2011-08-14
> **FMS.SouL said:**
> I'm currently using window 7 and I planning to install ubuntu desktop in same pc without remove my window7,should I download Ubuntu(Original edition) or widow installer called (Wubi).

If my understanding serves me correctly the Wubi version would enable you to run/install Ubuntu on top of Windows as you would any Windows application and it adds the option to boot into Ubuntu. Wubi does not modify the partitions of your PC or change your bootloader (ntldr) but it does require about 5 GB free harddisk space.

If you intend to run it in as a Dual boot system ie Ubunto in it's own partition then you could use the Original edition, but you if you do not have the free space to create the partitions required to do so you would be need to resize your existing Windows partition to make that space for Ubuntu - 7 GB should be about the right amount of space to have for Ubuntu to leave you sufficient space to install a few more basic apps and make Ubuntu as functional if not more so than Windows - bear in mind you would most likely be using just over 1 GB as a swap partition . A boot loader, most likely grub, would be installed for you to facilitate dual booting but this will all be handled by the Ubuntu installer which will prompt you for any input as and when needed.

In order to resize partitions in Windows 7 to make room for a separate Ubuntu installation (Dual-boot) you can use the Disk  Management utility that is integral to Win7. To find that, go to the search bar in your Start menu  and type &#8216;create and format&#8217; and click on the link that should come up on  top - it would be wise to backup any important files just to be on the safe side but it really is not a risky process.

---

### Post by raja.genupula on 2011-08-14
as compare with wubi , i choose separate install of ubuntu. but the best thing if it is first time to you , just move with wubi . if you feel comfort then go to separate installation  .so its depends on you . installing through wubi is some thing like installing an application inside windows . easy process .

---

### Post by garvinrick4 on 2011-08-14
Read all the "Show me hows" and look at graphic illustrations will learn a lot.
Either way you choose WUBI or Paritition will need to download and burn a disk so read that. At install can just choose to install side by side with Windows and Ubuntu installer will make partitions for you.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by FMS.SouL on 2011-08-14
If I choose wubi then I can run linux in windows 7 just like an application.
Then I should choose the original,that when I start computer,it will ask me which type of desktop I want to use,am I right ?:P

---

### Post by garvinrick4 on 2011-08-14
> **FMS.SouL said:**
> If I choose wubi then I can run linux in windows 7 just like an application.
Then I should choose the original,that when I start computer,it will ask me which type of desktop I want to use,am I right ?:P 
All you do is download the .iso file I gave you from Ubuntu and BURN it to a disk. Put it
in tray and open disk choose Wubi it opens and you choose the size you want to have.
Make it a minimum of 10 gig just so you have room to breath takes about 4 gig or so
for install leaves 6 for your personals in /home directory. Use more space if you have
room go's up to 30 gig I believe. Then you give user name and password and click install.
Will give you choice of Windows or Ubuntu to boot into now. Will be in a folder right next
to Users in C: drive in Windows. In Ubuntu file system Windows will be under directory 
(folder) called host. You can see windows files in Ubuntu you cannot see Ubuntu files in Windows. From now on Folders are
called directorys and the file system is called / your personal home directory is called /home.
In my signature under Main Page is a site that will give you a post installation guide, welcome to the World of Ubuntu linux. Ask all the questions you need to and put Wubi
in the title so Wubi users get on your questions.

---

### Post by raja.genupula on 2011-08-14
> **FMS.SouL said:**
> If I choose wubi then I can run linux in windows 7 just like an application.
Then I should choose the original,that when I start computer,it will ask me which type of desktop I want to use,am I right ?:P
yes

---

### Post by FMS.SouL on 2011-08-14
Both installer won't make any change of my windows 7 ?

---

### Post by garvinrick4 on 2011-08-14
> Both installer won't make any change of my windows 7 ?Anytime you install another Operating System on a Hard Disk Drive there is
a chance something will go amiss. The more one knows it gets to be less of a chance if
any at all. If you have all your personals backed up and have the install disks for the operating systems you use, it is never a real problem. When installing focus on what
you are doing and have studied install methods using if not used before. But to answer "no" another install does not change a different Operating System.
With Wubi it puts a new folder called "Ubuntu" in C: drive. Can be uninstalled from there or Add and Remove programs in Windows.
Ubuntu or Linux in general when dual booted in partions will use their grub boot manager and not Windows (so that is the change).

---

### Post by Actonix on 2011-08-15
> **FMS.SouL said:**
> Both installer won't make any change of my windows 7 ?

Wubi install - apart from taking up space in the windows partition and the necessary configuration that takes place against and when you install any application - no changes

Ubuntu install (Original - separate install from Windows) - Dual Boot install of Ubuntu into it''s own partition results in Grub taking over as your Boot-Loader (Helps to choose to load up Linux or Windows after Ubuntu is installed) - but the Ubuntu install requires that there is space for Ubuntu to make it's own partitions - if windows takes up all the space on your hard-disk you need to create that space - apart from this no other changes should occur

---

### Post by Mark Phelps on 2011-08-16
If you want Ubuntu in its own partitions, BEFORE you do the install, look in Win7 Disk Management and see how many partitions you already have in place.

If the PC came preinstalled witn Win7, it's possible that it already has the maximum of four partitions -- meaning, you can't simply create another one. You will have a difficult path ahead that will involve removing a partition, in order to continue the install.

Also, if you really do want to go ahead with dual-boot, BEFORE you do the install, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 boot loader.

---

