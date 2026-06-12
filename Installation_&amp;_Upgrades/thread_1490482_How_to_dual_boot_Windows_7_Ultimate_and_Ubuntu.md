---
title: "How to dual boot Windows 7 Ultimate and Ubuntu"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by X-Windows on 2010-05-22
As my first contribution to the Ubuntu Community I thought I would write up a how-to on dual booting Windows 7 Ultimate and Ubuntu 10.4. I'm sure there are other ways to do this, but this worked flawlessly and is relatively simple for those of you new to Linux and dual-booting.
 
What we will be doing:
 
Creating 3 primary partitions, one for windows, one for Ubuntu and one for Ubuntu-Windows shared space (photos, documents, music, videos downloads etc...) and then configuring Ubuntu and Windows to share the forth "Shared" partition.
 
The difficulty comes with Windows 7 Ultimate's second partition. When you do a normal Windows 7 Ultimate install Windows decides to create another 100Mb ***primary*** partition called "Windows Reserved". This partition houses various restoration and boot files and cannot be deleted safely after installation (Windows will not boot). This is not a huge issue with space, but it eats up an entire primary partition (because the only operating system you will ever need to run is Windows right?). We are installing *Windows 7 first*, because I found if I installed Ubuntu first, Windows 7 would overwrite the bootloader and create unnecessary difficulties.
 
Without further ado here is what you will need:
 
Windows 7 Installation Disc
Ubuntu Installation Disc
About 1 hours of free time

I partitioned a 300 Gb hard drive so my partition sizes may be slightly larger than needed. Feel free to change your partition sizes to whatever you need.
 
_Step 1._ **Backup personal data.** We will be deleting the entire hard drive so make sure all documents and essential files are backed up.
 
_Step 2._ Insert Ubuntu CD and boot into Trial mode.
 
_Step 3._ Go to System > GParted and delete all partitions. You should end up with the entire hard drive as free space. It is very important we have **no** primary partitions left on the HD.
 
_Step 4._ Restart and boot off the Windows Installation CD. This is where things get a little different.
 
_Step 5._ Once you are at the language selection window press **Shift - F10**. Now we are telling windows to not use a system restore partition. Type these commands in order:
 
**diskpart **(Opens DOS partition manager)
 
**list disk **(Show all hard drives)
 
**select disk 0 **(Select hard drive 0, replace 0 with whatever hard drive you are working on)
 
**clean **(Clean all partitions, we already did this in GParted, but it never hurts to be careful)
 
**create partition primary size = [COLOR=red]40000 [/COLOR]**[COLOR=red][COLOR=black](Here we are setting the size in megabytes for the new partition. 1,000 Mb = 1 Gb Here I used 40 Gb). Remember that Microsoft Office installs to this partition, aswell as any windows only antivirus and firewall.[/COLOR][/COLOR]
 
 
[COLOR=red]**[COLOR=red][COLOR=black]select partition 1[/COLOR] [/COLOR]**[/COLOR][COLOR=red][COLOR=black](Select the partition we just created)[/COLOR][/COLOR]
 
 
[COLOR=black]**active **(Set as active partition)[/COLOR]
 
 
[COLOR=black]**format fs=ntfs quick **(Format the active partition to NTFS format)[/COLOR]
 
 
[COLOR=black]**exit **(exit the diskpart utility)[/COLOR]
 
 
[COLOR=black]**exit **(exit the DOS window)[/COLOR]
 
 
[COLOR=black]_Step 6._ Continue[/COLOR] installation, when you reach the "Where do you want to install Windows" screen just left click the partition we created and then hit Next. Finish the Windows installation and boot up Windows to make sure everything works. Go ahead and install Windows updates now to save yourself a reboot.
 
_Step 7._ Boot off the Ubuntu CD and again select Trial. Launch GParted and make sure there is ***only*** one partition on the hard drive. If so, congratulations, you finished that hard part! If not, delete both partitions and try again. It is very important we only have one Windows primary partition.
 
_Step 8._ If there is just one windows partition close GParted and click on "Install Ubuntu 10.4". When asked where to install Ubuntu select ***"Specify partitions manually"***. We don't want Ubuntu filling up the rest of the hard drive.
 
_Step 9._When you are at the screen with a bar graph of HD space, click on "Free Space" and then "Add". Here we are adding a **logical** partition with file format "**ext4**", mount point "**/**"(no quotes) and size it to your liking (I recommend something above 8Gb, preferably 15Gb if you have it). Note that if you plan on using WINE, more space will be needed.
 
Now we need to make sure to add some **logical** swap space, this should be roughly 1.5 times the size of your RAM. Follow the same procedure as above, only in the File System drop-down select linux-swap.
 
[COLOR=black]_Step 10._ Follow on-screen instructions and install Ubuntu. Once Ubuntu loads, install all your updates and drivers. Before rebooting go to Applications > Ubuntu Software Center and search for "GParted". It may be named "Gnome partition editor" and should be the first hit, install and start GParted. Once GParted loads your partition settings right click on the /dev/sda4 partition. Select re-size and drag the right arrow all the way to the end. Now you should have the /dev/sda2 partition holding the Ubuntu install and its logical swap space. Right click the unallocated space at the end and format the it as** primary** "**FAT32**" and add a label, in my case I called it "Shared". Once you click format make sure to click the green "Apply" check mark above the partition graph. Congratulations you successfully partitioned your hard drive for Windows 7 Ultimate and Ubuntu 10.4![/COLOR]
 
[COLOR=black]_Step 11._ Reboot to Windows 7 and verify it still works (no reason why it shouldn't). Now go to My Computer > Users > (Username). There are 6 folders we need to move to the Shared partition; Downloads, Favorites, My Documents, My Music, My Pictures, and My Video. For each one, Right Click > Properties > Location tab > Move. Place them wherever you like in the Shared Partition. Remember this only shares the files for the selected user. Also remember to move the Internet Explorer/Firefox downloads folder to the FAT32.

Editing bookmarks in Ubuntu is much easier. Open your home folder (or any nautilus window) go to Bookmarks > Edit Bookmarks and update all replace the /home segment of the location with /media/Shared, where Shared is the label of your shared partition.
[/COLOR]  
Now we have 3 partitions so you can easily upgrade Ubuntu, share files with your other OS and keep Windows in your back pocked for those pesky "Windows Only" applications.
 
If there are any errors or skipped steps please post them below, I will do my best to keep this post up to date.

Edit: Post updated 6/11/10 and removed the /home partition. For 90% of the users, most of their home partition is documents pictures ect... which should all be on the fat32 filesystem.

---

### Post by kansasnoob on 2010-05-22
Since four primary partitions are the maximum allowable your HowTo makes me shudder. Where would you put the logical SWAP, it can't exist in a primary?

I usually go with 2 or 3 primaries and an extended that can house a lot of logicals:

[ATTACH]157874[/ATTACH]

---

### Post by wilee-nilee on 2010-05-22
Here is a link to some information about the system reserved 100mb partition.
[http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/](http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/)

---

### Post by X-Windows on 2010-05-22
> **kansasnoob said:**
> Where would you put the logical SWAP, it can't exist in a primary?

I usually go with 2 or 3 primaries and an extended that can house a lot of logicals:

[ATTACH]157874[/ATTACH]

Edit: Outdated post, how-to has been updated to only use 3 primaries. I now have Ubuntu in a logical that holds my swap space and other misc logicals.

---

