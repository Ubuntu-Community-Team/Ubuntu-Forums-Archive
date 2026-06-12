---
title: "multiple version install problems"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by dgundling on 2011-11-13
After my first attempt to get 11.10 up and running yielded a scrambled hard drive, I wiped the HD (41GB) and repartioned. I made two partitions of 10GB each to start with and left the remaing space open. After several tries I got 10.10 up and running. Next I tried to load 11.04 in the second partition. Got that straightened out after a struggle and all was well for one session. Started the computer up today on 10.10 and it worked fine. Next I tried to load 11.10. When I clicked install ubuntu I was informed that I had insufficient space of the hard drive to load ubuntu. I was not given the option to reformat the disk or repartition. Gave up on 11.10 and wen back and tried 11.04. It had been scrambled and would only work briefly before locking up.
 
Tried a "live" CD in an effort to get to the disk partitioning page. No go. BTW, not one of my 3 ubuntu 11.10 CDs downloaded from the ubuntu download site is functional. I get a page of stuff which looks like a listing of attempts to load modules. At the end of the page it stops and locks up.
 
Can anyone help?
 
Thanks.
 
Dave

---

### Post by oldfred on 2011-11-13
I do not understand. You say you installed it to a 10GB partition, but then it gives you a choice to install? Or did you just do a liveCD install onto the hard drive?

Often if it starts to boot and fails it is a video issue, or with older or very new computers you may need other parameters.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by dgundling on 2011-11-15
oldfred,
 
Thanks for the reply. Sorry I was not clear. I am trying to get 10.10, 11.04, and 11.10 installed and functional on the same hard drive. I have set the HD as 4 10GB primary partitions. First I loaded 10.10 into the first partition and got it running. Next I shut 10.10 down and installed 11.04 in the second 10GB partition. Got it to run my test case which is a game of Mahjong. Mahjong ran once. At the end of the game the computer locked up. Couldn't close the game or shut the computer down through 11.04. Went back and tried 10.10 the game worked twice before the computer froze again. This after the game in 10.10 worked fine for as long as I wanted to play it before I tried to install 11.04. Just for fun I tried to install 11.10 in the 3rd partition. It wouldn't install at all. Got a page full of alphanumerics.
 
All of this mess started when I had WIN98SE, 10.10, and 11.04 running happily on the same HD partitoned as above. My mistake was letting update manager try to update 11.04 to 11.10. That excercise yielded a completely scrambled HD. All versions in all partitions were not working. I wiped the HD and started over with the results as above.
 
I appear to have good 11.04 and 11.10 CDs via download. I can install 11.04 if I try a few times. 11.10 is hopeless when I try to install.

---

### Post by oldfred on 2011-11-15
I doubt if you had to totally reinstall. The last install takes over the MBR and becomes the boot system with its kernel first on the menu. But if any of the other installs were working then you can use the liveCD to reinstall that boot loader to the MBR.

With 11.10 did you get to a grub menu or did grub fail. Usually grub show grub? or grub rescue>. And since you had multiple installs you should have gotten the menu without having to use the shift key from BIOS until menu appears. Some systems require extra boot parameters also. See previous post.

So where are you now.

If you want to see what is installed where, you can run from your install or a liveCD if install is not booting.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Sometimes it is good to have these available as they can fix or boot system.

[Boot-Repair] Graphical tool to repair the PC boot in 1 clic !
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

