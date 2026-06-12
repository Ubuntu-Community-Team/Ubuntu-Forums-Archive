---
title: "cannot install ubuntu on toshiba nb 250 netbook"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by paichkash on 2010-09-26
hi
i want to install ubuntu on the nb250 netbook...sice it lacks ither a cdrom or dvd rom .. hosw can i install it ?  i have attached a dvd rom through an ide ton usb converter and it can read the ubuntu dvd flawlesly... but i cannot install it ..double clicking on the dvd icon gives me the option to install or demo ubuntu and then it restarts but win 7 comes back..there is no option in thed boot menuj which could enable me to use a usb as first boot device..

thanks

---

### Post by sikander3786 on 2010-09-26
Most of the netbooks have the ability to boot from USB. And most of the times, flash drives show up under the Hard Disk Menu and you have to change the priority of driver there. Did you try that?

If Ubuntu is unable to install from the DVD, most probably the DVD is defected. Start hitting any key as soon as the netbook gets past the Bios screen and you'll see a menu. Select "Check disc for defects" and see if it is a good burn or not.

---

### Post by paichkash on 2010-09-26
the dvd is perfectly ok.. i have checked it on the same dvd drive on another pc....... 

i have an ATA to USB converter [externally powered dvd drive] and that is successfully attached to the netbook and can run all the dvds ... i rebooted into bios and it did gave me the option of the list of boot devices but the dvd drive sometimes shows in the list and other times it wont... and if select i as first device i could nt get into the ubuntu boot... the windows boots then.. 

the bios version of my netbook is 1.40

---

### Post by paichkash on 2010-09-26
ok i updated the bios to version 1.6 the latest available and now i am able to boot into the ubuntu cd i was able to run live cd but i have now clue as to haw to partition it... i have partition magic how do i use it .....

there is no drivs in ubuntu like c,d,e in windows how should i partition ? currently my windows 7 ultimate is showing only one drive c and its size shown is 124 GB and it has 106GB of free spacde ... i want  to resize this partition and make a 30 GB Partition fo ubuntu .. how i do it.. also i am running the Super OS 9.04 DVD .. during the installation the dialog/windows are not shown compete they are off the screen i cannot see the forward arrow in the lower right corner only the back arrow is shown .,, and that too only half of it..

---

### Post by sikander3786 on 2010-09-26
Use the partitioning tool in Windows instead to free up space for Ubuntu. You can also use gparted that is present on Ubuntu Live CD.

If you are unsure about partitioning, just free up space as you mentioned 30GB, leave it unallocated i.e, don't create a partition in it and during the Partitioning Step in installer, select "Use the largest continuous free space". Installer will automatically create partitions in the free space according to its need.

---

### Post by Kingcheese26 on 2010-09-26
just get the universal USB installer (pendrivelinux.com) on a windows pc other than your netbook (you have to have a USB drive with 2 gb or more free space). You don't have to download the iso before creating the USB, just check off "download iso." I hope htis solves your problem!

Kingcheese26

---

### Post by sikander3786 on 2010-09-26
> also i am running the Super OS 9.04 DVD .. during the installation the dialog/windows are not shown compete they are off the screen i cannot see the forward arrow in the lower right corner only the back arrow is shown .,, and that too only half of it..

Sorry I missed that part of post in my 1st reply. Why are you still using 9.04? Why don't you go for 10.04.1 instead?

> 
just get the universal USB installer (pendrivelinux.com) on a windows pc other than your netbook (you have to have a USB drive with 2 gb or more free space). You don't have to download the iso before creating the USB, just check off "download iso." I hope htis solves your problem!


New version of pendrivelinux has got a strange bug. After download/copy to USB, some folders need to be renamed. There is an easy solution still I will go for unetbootin in that case. It also has got the ability to download images directly from the servers.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by paichkash on 2010-09-27
unfortunatelly it seems that as usual i have once again ruined my pc[this time laptop..netbok..] . here is what i did..

this netbook already has 150GB hdd..
it has some 4 partitions 
one was 5mb [unallocated ---no filesystem] 
2nd was 124 GB ntfs partition shown in window as c drive [this was the only drive shown there]
3rd was probably 1.5 GB ntfs hidden
4th was also NTFS and hiden 

now what i didis that i booted live cd and started sudo gparted and then resized the largest partition of 124 gb so the windows primary partition c was reduced to 85gb and it left 38gb unallocated space after this drive.. here goes the heck .. i could not create any partitioin in the newly unallocated space it said something about 4 primary pasrtitions exists create a logical...blal bla dont remember exact wordings i tried to create a partition usin Hiren Boot CD using acronis disk director suite and a host of other softwares but there too i was unabl to create a partition.. 
so i tried to install ubuntu from live cd and in the partitioning process it gave me two choices 
first format entire disk [and remove vista[7] and have just ubuntu
2nd use manual partitioning 
chosing manual and then i think gparted softwarre came and still the same result couldnt create a partition...

so i gave up with ubuntu installation and had to use 7,, but when i restated i could not start windows 7 its startup recovery software waas unable to recover windows .. it gave the reason as something as corrupt boot config datra.. 
have tu re run the gparted got all the drives checked it shows the windows partition as 18gb used but all other softwares show 0 kb free space available........

now i want to just run windows on it what shoiuld i do ?
i min hot aters.. ubuntu has once again rendetred my pc useless and i m pretty sure i have lost all my data....

---

### Post by paichkash on 2010-09-27
after 4 hours of non stp brutforcing i m able tp recover some of my data and install windows 7 ultimate. now my system is back in perfect ondition.. after a lot of troubles  i have no doubt to say that ubuntu is just a piece of ****,, its a useless os,everything there is strange and bizzare.. its not for human deings .. iyts vewry complex .... one cannot run it smoothly with common sense... i,e the name of various softwares are very cryptic nd has no resemblance to what it actually does .. e.,g brassero hhaahah .. goodby ubuntu...

---

### Post by wickedmonkey on 2011-04-17
In case anyone is interested, I think the op has some valid points in his last post. 

A lot of people say that Ubuntu 'just works' but this isn't always the case. It is a shame that USB memory stick creation is difficult for newcomers and it is also a shame that the creation app seems to have a strange bug -- ie, you need to type 'help' when you first boot off of the USB stick. It is bizarre that, considering Ubuntu is perfect for a lot of netbooks that struggle under Windows, more effort is not placed in cleaning up these annoyances in this area. I have an NB250 as well and it works almost flawlessly but this wide-spread bug nearly put off.

Ubuntu is coming to the stage where "ordinary" people are coming across it by chance. Some love it but others find bugs and issues such as the ones mentioned in this thread off-putting -- and rightly so.

Just my two pence worth.

---

### Post by GHerzog on 2011-07-28
I have a Toshiba NT250 with dual boot - W7 Starter and Ubuntu NB edition 10.04 which has now been frequently updated.  

It can work if you sort out the partitions. Toshiba has done some odd things, including several hidden partitions for Windows 7 recovery. One MUST let Windows think it is in control of the boot process of the computer. So it is important to have Windows in the first partition. This gets rather tricky as Toshiba has eaten up all the 4 primary partitions for Windows. I suspect this is a ploy to make it harder to fit in Linux. But I found that Linux will reside happily in an extended partition and Grub2 will sort out whatever W7 desires.

Still, I must say that nearly all the FN+function key features will NOT work. It seems to be an issue about the BIOS and Toshiba isn't willing to provide a Linux friendly BIOS even though this seems to be a next to nothing additional cost to them.

In other words, Toshiba seems to be very cozy with M$.

I still use the Toshiba NB250 everyday without the FN+ features and my only frustration is that the battery life is a bit shorter due to wifi being on all the time.

---

