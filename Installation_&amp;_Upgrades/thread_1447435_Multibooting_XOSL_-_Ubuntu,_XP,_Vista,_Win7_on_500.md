---
title: "Multibooting XOSL - Ubuntu, XP, Vista, Win7 on 500gb hdd"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by fishfinger on 2010-04-05
[FONT=Arial][SIZE=3][FONT=Arial]Hello, 
[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=3][FONT=Arial]
[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=3][FONT=Arial]I have a 500gb hdd and want to install the below os’s. I have used a previously great step by step tutorial that illustrated Ubuntu, XP and [/FONT][FONT=Arial]Vista[/FONT][FONT=Arial] but can’t find a guide on what I would like to do below…[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=3][FONT=Arial]I intend to use ranish for partitioning and xosl as a[/FONT][FONT=Arial] bootloader.[/FONT][/SIZE][/FONT]
  
              [FONT=Arial][SIZE=3][FONT=Arial]Ubuntu[/FONT][/SIZE][/FONT]
         [RIGHT][RIGHT][FONT=Arial][SIZE=3][FONT=Arial]15GB[/FONT][/SIZE][/FONT][/RIGHT]
[/RIGHT]
             [FONT=Arial][SIZE=3][FONT=Arial]XP[/FONT][/SIZE][/FONT]
         [RIGHT][RIGHT][FONT=Arial][SIZE=3][FONT=Arial]40GB[/FONT][/SIZE][/FONT][/RIGHT]
[/RIGHT]
             [FONT=Arial][SIZE=3][FONT=Arial]Vista[/FONT][/SIZE][/FONT]
         [RIGHT][RIGHT][FONT=Arial][SIZE=3][FONT=Arial]40GB[/FONT][/SIZE][/FONT][/RIGHT]
[/RIGHT]
             [FONT=Arial][SIZE=3][FONT=Arial]Windows 7[/FONT][/SIZE][/FONT]
         [RIGHT][RIGHT][FONT=Arial][SIZE=3][FONT=Arial]70GB[/FONT][/SIZE][/FONT][/RIGHT]
[/RIGHT]
             
         
          [RIGHT]   
[FONT=Arial][SIZE=3][FONT=Arial]Total OS[/FONT][/SIZE][/FONT][/RIGHT]
         [RIGHT][RIGHT][FONT=Arial][SIZE=3][FONT=Arial]165GB[/FONT][/SIZE][/FONT][/RIGHT]
[/RIGHT]
          [RIGHT]   
[FONT=Arial][SIZE=3][FONT=Arial]Shared data drive formatted   with NTFS so all os’s can read/write to this.[/FONT][/SIZE][/FONT][/RIGHT]
         [RIGHT][RIGHT][FONT=Arial][SIZE=3][FONT=Arial]Approx 335GB[/FONT][/SIZE][/FONT][/RIGHT]
[/RIGHT]
      
[FONT=Arial][SIZE=3]
[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Thanks[/SIZE][/FONT]

---

### Post by oldfred on 2010-04-05
I know nothing about [FONT=Arial][SIZE=3][FONT=Arial]xosl but you need to know this about windows or you will only have two boot entries:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
[/FONT][/SIZE][/FONT]

---

