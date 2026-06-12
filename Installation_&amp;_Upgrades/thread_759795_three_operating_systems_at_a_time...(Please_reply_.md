---
title: "three operating systems at a time...(Please reply quickly)"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by kshtjsnghl on 2008-04-19
HI everyone,
 I have got ubuntu on my pc currently but due to some project i need to have windows xp as well as solaris 10 in addition to ubuntu. As the applications that i would be requiring on the other 2 operating systems are heavier i cannot have them through virtualization. So, i just wanted to ask how should i install all of them so as to i can boot in any of it during the initial booting.
 Besides, i would like to keep ubuntu as my primary operating system in the sense that all my data and other applications to fiddle with would be in ubuntu. 
 Please tell me what should be the sequence of the installatons of various operating systems and how should i partition my hard disk( my hard disk size is 60 gb) and what should be the distribution of various partitions.
Thanks.

---

### Post by wpshooter on 2008-04-19
I don't know about solaris 10 but generally you should install XP first and then Ubuntu.  My guess is that XP would also come before Solaris but I have no idea as to whether Solaris would be installed 2nd or 3rd !!!

I would say that 10gb would be a good plenty of Ubuntu O/S and perhaps 15gb for Ubuntu/home.  I don't know what Solaris would be require.

---

### Post by the8thstar on 2008-04-19
Okay, I've done it in the past myself. It doesn't really matter who's second or third, but installing XP first usually is a little easier on the whole.

But since you already have Ubuntu installed, here's what you can do to save yourself some time.

In the terminal, open:

> sudo gparted

Create a new partition for XP and another for Solaris. You can leave them blank, but XP usually prefers to have its partition set to NTFS. Set the XP partition with the 'boot' flag otherwise XP will bitch at you saying that you can't install on that partition (that works for Vista too). Just so that you don't screw yourself up, make the partitions with different sizes, just so you'll know which is which when you have to tell them apart.

Now leave gparted, close the terminal and insert the XP CD in the drive. Reboot.

Follow the onscreen instructions for XP and install on one of the partition you created earlier with gparted (the one you formatted with NTFS for instance).

The computer will probably have to reboot several times, so just follow what XP wants and go on. When everything is fine, XP should run smoothly, but Ubuntu will be inaccessible. This is **NORMAL** because XP erased Grub. 

Don't worry and put your Solaris 10 DVD in the drive.
Reboot.

Again, follow the instructions for installation... Solaris 10 takes 30-45 minutes to install completely. Of course you're going to choose the last partition you created in gparted as the destination for the OS! Since it's UNIX, the partition is called a slice in the installation process... nothing to write home about. Just follow what's proposed and Solaris will create partitions within the slice itself... i.e. sub-partitions.

Finally, when everything is done, Solaris will reboot with its own version of Grub, which should include all the aforementioned OSes, Solaris, Ubuntu and XP. If it doesn't work for some reason let me know and I'll help from there.

---

### Post by kshtjsnghl on 2008-04-19
thanks for the reply. I will do it that way
But i had one more query.Now the data (like movies, music and some of my academic materials) are there on the hard drive partition used for ubuntu then after the installations of windows and solaris (as replied) will this data still be available to both windows and solaris ( so that i can listen to music while working on windows)?? Or i have to do something else..

  Also when i installed ubuntu, i gave the swap partiton 1.5 gb but now i think its not being used more than 512 mb. So i also wanted to free some of my usable memory by reducing the size of my swap parttion.Is that possible without resintalliing ubuntu?

---

### Post by kshtjsnghl on 2008-04-19
hey i tried to make a new partition but when i opened gparted it is showing only two partitons- ext3 nad external(swap). but i am unable to make a new partition out of them. I dont know there is also some lock sign beside these partitions. help

---

### Post by the8thstar on 2008-04-20
Okay.

Looks like you've maxed out the number of physical partitions (max =4). You could always try to set extended partitions, but since Solaris doesn't install on an extended partition, I'm not going to go there. So... here is an idea. First of all, you need to run gparted with sudo in front, aka **sudo gparted **to be granted administrator privileges.

Partitions with little locks next to them are likely to be 'mounted', which means that Ubuntu has locked them in order to make use of them. You can right-click on each partition and select 'unmount'. From there you should be able to resize your partitions and add new ones. But doing so is risky because it can cause your system to become unstable and crash during the procedure. 

My advice to you is to [COLOR="Blue"]use the LiveCD [/COLOR]you installed Ubuntu with [COLOR="blue"]and run gparted from there instead[/COLOR]. Boot from the CD, choose the 'install' option. Since the CD is not installing anything but running in RAM, you won't crash the system. When you get to the main screen, open the terminal and type 'sudo gparted'. You will find the familiar screen again, where you will be able to access all your existing partitions.

From there, it's likely that your current Ubuntu partition and swap partition take up the whole disk space, which means that you can't install any new ones unless you size down ubuntu and swap first. Doing so is fairly easy and you can use the mouse to literally crop and extend your partitions size at will. For instance, let's say that you have a 80Gb hard drive, with 78Gb for Ubuntu and 1.5Gb for swap. These numbers are for tutorial only. Feel free to adapt them to your configuration and system.

1. Size down your ubuntu partition to 38Gb - select apply (this could take a while) If you have more than 38Gb of data, choose a bigger number. Your documents and files won't disappear.

2. Resize your swap file the same way from 1.5Gb to 512Mb and move it to the left next to your ubuntu partition. This step is important for Solaris installation later - see PPS below. Select Apply.

3. There should be 40Gb free (in gray) to the right of these two partitions. Select them all and create two partitions, the first for XP/Vista of 25Gb and the second for Solaris of 15Gb. These are standards values that should make these OS comfortable enough to run fine. Select Apply.

4. The partition you chose for Windows can be left blank or can be formatted to NTFS, but I've seen instances when Windows doesn't like that (for some reason) so you can format it to FAT32 instead. Windows will reformat it to NTFS later. IMPORTANT: select the 'flag' and set it to 'boot'. Select Apply.

3. The partition for Solaris can be left blank or formatted to FAT32. If you use EXT3, Solaris might not like that. Eventually, during the Solaris install, the partition will be reformatted with Solaris proprietary format anyway. Select Apply.

All these operations should be done fairly quickly (The longest will be the resizing of Ubuntu which will move files around quite a lot). Eventually, you should get something like:

**Ubuntu || Swap || new partition for Windows install || new partition for Solaris install**

Once you've done all that, close gparted and the terminal and shut down the LiveCD. [COLOR="Red"]DON'T DOUBLE-CLICK ON THE INSTALL UBUNTU ICON [/COLOR] that's sitting on your desktop as Ubuntu is already on your system. Shutdown the system, remove the LiveCD and press Enter to reboot. If all goes well, Ubuntu will boot just fine. This is a check to make sure we haven't actually destroyed anything with gparted. Once you are reassured with Ubuntu, it's time to move on and install your other OSes (see my previous post).

Now, when it comes to being able to see documents in Ubuntu from Windows or Solaris, I can only help partly with what I know. Once in Windows, look here: [http://sourceforge.net/projects/ext2fsd]("http://sourceforge.net/projects/ext2fsd") and download the latest version. Go to Control Panel, start the applet and assign your ubuntu partition a drive letter. As simple as that. For Solaris, I must say that I have no idea.

Good luck. Keep me updated on your progress. :)

[I]PS: there is a known issue going on between Linux based systems and Solaris systems. Linux OS can sometimes confuse Solaris partitions with their own swap partitions if they are installed next to each other. This result in the destruction of Solaris OS. The problem can be prevented if the actual Linux swap is set to sit next to the main Linux partition. With a Windows partition residing between the swap and Solaris partition, there shouldn't be any problems.

PPS: swap is not really needed if you have more than 1Gb of memory. You can safely remove the partition in gparted and Ubuntu will do the rest upon the next reboot.[/I]

---

### Post by kshtjsnghl on 2008-04-21
thanks the8thstar 
I understood it now and i will do it that way...

---

