---
title: "Winxp in Ubuntu OS"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by Patrik_Samju on 2014-04-22
Hi Guys! I'm have tried Ubuntu before but not to the extent that I am using it everyday as my computing tools. It just a sort of familiarization of the OS like getting to know each other :). I'm a windows user cause of my job. I'm an old school programmer. I'm using VB6 until now. Currently my dev tool was installed in Windows8 Ultimate but been encountering errors on my compiled application. 

I would like to reformat my old laptop from windows8 to ubuntu. Can I virtualize my windows applications inside ubuntu? Can I still develop vb6 application with windows in ubuntu? How? Need help. 

Shifting from windows user to Ubuntu.

---

### Post by Gilad_Pellaeon on 2014-04-22
> **Patrik_Samju said:**
> Hi Guys! I'm have tried Ubuntu before but not to the extent that I am using it everyday as my computing tools. It just a sort of familiarization of the OS like getting to know each other :). I'm a windows user cause of my job. I'm an old school programmer. I'm using VB6 until now. Currently my dev tool was installed in Windows8 Ultimate but been encountering errors on my compiled application. 

I would like to reformat my old laptop from windows8 to ubuntu. Can I virtualize my windows applications inside ubuntu? Can I still develop vb6 application with windows in ubuntu? How? Need help. 

Shifting from windows user to Ubuntu.

First thing that comes to my mind would be to use Virtualbox and run WinXP in a virtual machine and see if VB6 will run then. Or install WINE in Ubuntu and then try VB6. From what I just saw over in the WINE App database no one's tested it in over 4 years and that was with a much older version of WINE so, who knows, it may just work fine if you go this route.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325&iTestingId=15428](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325&iTestingId=15428)

---

### Post by fantab on 2014-04-23
Since you need Windows for work I suggest that you Dual-Boot both Windows 8.1 and Ubuntu, each from its own separate partition. There are many users here who have regretted removing Windows completely. There will always be something which only Windows can do, given the percentage of Windows users around us. Don't use it if you don't have to but keep it around. 

Wine, as suggested, can come to the rescue. However. personally I'd say avoid WINE if you can.

I don't know much about VB, but check out the following:
[URL="http://www.picohelp.com/1264/how-to-run-windows-xp-in-windows-8-with-virtualbox-6-simple-steps.html"]http://www.picohelp.com/1264/how-to-run-windows-xp-in-windows-8-with-virtualbox-6-simple-steps.html
[/URL][URL="http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox"]http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox
[/URL]

---

### Post by 3rdalbum on 2014-04-23
You can dual-boot, which keeps Windows 8 in one partition and Ubuntu in another. Whenever you start your computer you can choose an operating ssystem to boot into. The Ubuntu installer can set one of these up for you easily.

Your other option is to install Ubuntu on the whole disk and then install a fresh copy of Windows into a "virtual machine". You can then have Windows running in its own little window while you are using Ubuntu.

If you want to go down this route, you can use the program Virtual box to set up the virtual machine.

Another poster suggested Wine, I don't think it will work for your purpose.

---

### Post by SeijiSensei on 2014-04-23
I would recommend VirtualBox as well, but only if you have at least 1.5 GB of memory.  WinXP can run in 512MB, but it will swap to disk a lot if you have a number of programs open.  Ubuntu is happier in 512MB than WinXP, but it, too, would prefer more memory.  I have a 2 GB machine with Windows in a VirtualBox VM.  I think I gave Window 768M and left the remainder for Ubuntu.

You'll be asked how much memory to allocate to the virtual machine during installation.  You can change the allocation later on if needed as well.

---

