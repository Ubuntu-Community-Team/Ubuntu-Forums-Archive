---
title: "Installed Mandriva cant find Ubuntu"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by benniebrown07 on 2008-02-01
I installed mandriva and now i cant find my ubuntu I asked in a another post before but no one really told me how to fix it. Taurus wrote me:

> **taurus said:**
> Mandriva installed it own version of GRUB to MBR so you need to edit it and add an entry for Ubuntu.  If you are not sure how to add it, just look at the /boot/grub/menu.lst for Ubuntu on how.

This tells me my problem but really not how to solve it. Any one know how to fix this?

---

### Post by logos34 on 2008-02-01
> **benniebrown07 said:**
> This tells me my problem but really not how to solve it. Any one know how to fix this?

Take another look at the top of menu.lst -- there are sample entries for how to add another OS.

Otherwise try [this format]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").

---

### Post by SkittleLinux18 on 2008-02-02
If you haven't already fixed the problem, do this:

1) Go into Mandriva Control Center, navigate to Mount Point, Create/Resize/Delete Partitions.

2) Once in there, look at your partitions and find out which one is Ubuntu. 

3)When you find it, click on that partition. In the info that pulls up, find out what is listed next to "Device:" (it should be something like hda3, or another number)

4) Cancel out of Partition Editor and navigate MCC to Boot. Click on "Set up how system boots." In the screen that comes up, click Next. On the next menu, click the button that allows you to add. It will be near the top right. 

5) make sure the option for LINUX is selected and click next.

6) Another window will come up with a bunch of drop down menus. (be sure to title the boot option whatever you want) one of them will be to select the device. This is where you will select whatever you discovered in step 3.

7) a code will then appear in another text box. something like /boot/vmlinuz... yadda yadda yadda... i dont remember exactly what it says, but you will know it. 

8 ) if there are dashes and numbers that follow after the words, delete them.
-----> EX: /boot/vmlinux-2.3.554.32
-----> delete everything from "-2.3.554.32" on. it doesn't matter what the numbers say, you dont need them. if you forget to do this, expect a kernel panic the next time you boot.

9) click ok, ok, save, make sure a quick window pops up telling you bootloader installed. cancel out of MCC and reboot.

10) select your new boot option when GRUB appears and enjoy!!

---

