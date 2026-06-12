---
title: "Lubuntu install not working on old Sony Vaio"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by cgrooms on 2013-01-23
My computer was recently stolen and a friend of mine gave me an old Sony Vaio laptop that is a piece of crap. It ran xp and couldn't even connect to internet it was so slow. I used an ethernet to download lubuntu and booted into it using UNetBootin, which installed lubuntu to my harddisk.

Lubuntu runs fine, everything works, but it is not properly installed which means I can't save more than a megabyte. When I run 'Install Lubuntu 12.04', which is automatically in the top left corner of the desktop.... it:
Opens, says 'you may wish to update this installer', but clicking on this does nothing, so with english selected on the left I just hit continue.
Then it says Preparing to install Lubuntu. For best results check that computer connected to internet, power, and has 4.4 GB of available drive space. it also has options for downloading updates and installing 3rd party software while it installs. I leave each of these unchecked. I hit continue...

now here is the problem. it says 'Installation type' then has an area for all the partition information that I see in screenshots and other forum threads. I have nothing. blank, empty. no bar saying what is used and empty. no file structure in the blank area. Clicking 'New Partition Table, Add, Change, Delete, Revert' each do nothing. It then says 'device for boot load installation:' and then has a drop down menu containing only /dev/sda. When I check the files on the computer, there is no /sda under /dev. Also, fdisk doesn't recognise /dev/sda, it says "fdisk: unable to open /dev/sda: Permission denied."
Hitting continue at this point with the blank partition area gives the popup "Not root file system is defined please correct this from the partitioning menu"

Here are the links to two ubuntu pastebins from before and after running a boot fixer, they might help:
[http://paste.ubuntu.com/1564265/](http://paste.ubuntu.com/1564265/)
[http://paste.ubuntu.com/1564283/](http://paste.ubuntu.com/1564283/)

Any help would be greatly appreciated. I don't want to go out and have to buy a new computer.

---

### Post by TheFu on 2013-01-23
If you don't need any of the data on the HDD, I would wipe it and recreate the partition table - 15G for Ubuntu, 1G for swap and the rest for /home.

If you boot using the liveCD and everything appears to work, then the install should be fine. If when running the live version there are issues, then you need to do lots more research before continuing.  I would google "ubuntu install {sony model number}" to see if someone else has posted any boot options you will need.

---

### Post by cgrooms on 2013-02-05
> **TheFu said:**
> If you don't need any of the data on the HDD, I would wipe it and recreate the partition table - 15G for Ubuntu, 1G for swap and the rest for /home.

If you boot using the liveCD and everything appears to work, then the install should be fine. If when running the live version there are issues, then you need to do lots more research before continuing.  I would google "ubuntu install {sony model number}" to see if someone else has posted any boot options you will need.


I have tried to figure out a wipe- I did one reset sort thing not complete wipe. Cannot figure out the full wipe though- all the programs I've gotten have issues or don't make any sense.
If anyone could elaborate on maybe a step by step for this, that would be immensely helpful.

Thanks.

---

### Post by TheFu on 2013-02-06
I hope you aren't still waiting for an answer.

"Wipe" means to delete all partitions and possibly use a random tool to lay down a pattern across all the bits stored on the HDD with a tool like DBAN, [http://www.dban.org/](http://www.dban.org/) .

Deleting all the partitions is enough for you.  Use any tool you like, but gparted is probably the easiest to use.  I'd strongly recommend setting up your partitions **before** attempting the installation.  The partition tool inside the install is an unknown to me. I know that parted and gparted handle all HDDs optimally for Linux.  
* MBR or GPT - fine.
* 512b or 4K sectors - fine.
* HDDs over 2TB in size - fine.

Other commonly used tools, like fdisk, sfdisk, cfdisk **don't do the right thing** automatically. That is an issue.  **gparted **FTW.

---

