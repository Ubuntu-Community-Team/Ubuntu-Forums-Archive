---
title: "Which file system?"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by rabot on 2012-12-10
I'm brand new to Ubuntu and have read the installation notes but they haven't really answered my issue.
On my old PC, I used to have a hard drive with 2 partitions, one running Windows and one storing all my data.

I've now got a new PC and would like to have a similar set-up while running Ubuntu instead of Windows, i.e. 1 partition for the OS and one for all my data. 

However, I most likely will be running Windows on this new PC at some point in the future, so Windows will need to be able to read and write all data in the second partition. So that means formating it as NTFS. 

What file system should I use for the partition that will run Ubuntu then? Should it be ext4 or NTFS too? I've read a lot of conflicting advice on this.



My new PC runs an Intel i7 processor. I'm not into gaming at all but want a fast PC like everyone. I'll be watching movies online mostly. Is Lubuntu much faster than Ubuntu? Which one is 'easier' for a total newbie?

---

### Post by haqking on 2012-12-10
> **rabot said:**
> I'm brand new to Ubuntu and have read the installation notes but they haven't really answered my issue.
On my old PC, I used to have a hard drive with 2 partitions, one running Windows and one storing all my data.

I've now got a new PC and would like to have a similar set-up while running Ubuntu instead of Windows, i.e. 1 partition for the OS and one for all my data. 

However, I most likely will be running Windows on this new PC at some point in the future, so Windows will need to be able to read and write all data in the second partition. So that means formating it as NTFS. 

What file system should I use for the partition that will run Ubuntu then? Should it be ext4 or NTFS too? I've read a lot of conflicting advice on this.



My new PC runs an Intel i7 processor. I'm not into gaming at all but want a fast PC like everyone. I'll be watching movies online mostly. Is Lubuntu much faster than Ubuntu? Which one is 'easier' for a total newbie?

Ext4.  Dont know what advice you have read which conflict, but Linux wont sit on a NTFS partition anyways as the permission structure is different. (unless you count WUBI but that is different)

---

### Post by Bucky Ball on 2012-12-10
Welcome to the forums.

Ubuntu will not run on NTFS. Use EXT4. That will be dealt with during install.

Easiest is to leave a partition or empty space at the beginning of the drive for Windows then create an extended partition with logical drives for Ubuntu, swap and your data partition with the rest of the drive. Make the data partition (or logical drive inside the extended partition in this case) NTFS so it can be read and written to by both OSs.

Now for the slightly tricky but fun bit. When you install Ubuntu you will automatically get a /home directory inside the install with folders like Documents, Music, Video, etc.; all the usual personal data stuff. But you want to keep that stuff on the data partition, the NTFS one, to be read by both OSs. So you delete the folder in the /home folder (except Desktop and the hidden folders) and create new ones on the data partition. 

You can then create symlinks (shortcuts) to these folders in /home. You can also link your Windows install to the folders in the data partition (but I honestly don't remember how, just know I used to do it). To create symlinks in Ubuntu:

[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

There are alternatives but there's one option. ;)

... and yes, Lubuntu or Xubuntu faster and probably easier to get your brain around coming from Windows but you need to take the Windows hat off, turn your brain 10 degrees and hit the learning curve. Good luck and hope you enjoy.

---

### Post by matt_symes on 2012-12-10
Hi
 
> **haqking said:**
> Ext4. Dont know what advice you have read which conflict, but Linux wont sit on a NTFS partition anyways as the permission structure is different. (unless you count WUBI but that is different)
 
Bang on the money.
 
ext4 is the default filing system in Ubuntu for a reason. 
 
My advice is use it for your Ubuntu root partition and have your shared data partition as NTFS.
 
/home also want to be non NTFS.
 
Kind regards

---

### Post by rabot on 2012-12-10
Advice coming thick and fast. Thanks a lot.

I think it's all sorted now. ext4 for Ubuntu install and NTFS for the data partition.

I've read that with the NTFS 3g driver, Ubuntu can read and write on the NTFS file system. But I guess it wasn't made clear it's for WUBI?

And if you look right at the bottom of this page, it says the filesystem should be the same:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

Anyone else care to comment on Lubuntu and Xubuntu flavours and their preferences and opinions?

---

### Post by rabot on 2012-12-10
> **Bucky Ball said:**
> 

Now for the slightly tricky but fun bit. When you install Ubuntu you will automatically get a /home directory inside the install with folders like Documents, Music, Video, etc.; all the usual personal data stuff. But you want to keep that stuff on the data partition, the NTFS one, to be read by both OSs. So you delete the folder in the /home folder (except Desktop and the hidden folders) and create new ones on the data partition. 

You can then create symlinks (shortcuts) to these folders in /home. You can also link your Windows install to the folders in the data partition (but I honestly don't remember how, just know I used to do it). To create symlinks in Ubuntu:


Is there any advatange to doing this little trick with the /home folder? Will I miss anything if I ignore it all and go ahead with my Data partition?

---

### Post by SeijiSensei on 2012-12-10
You'll be happier if you create a separate NTFS partition to share between the operating systems, while putting /home on its own partition with an ext4 filesystem.  Keeping /home separate lets you change the Linux OS without losing data.  You really cannot use NTFS for /home because of the variety of "hidden" files that *nix uses for user-level configurations.  (These are files and directories whose names begin with a dot like ".config".)  Also you cannot enforce *nix permissions on an NTFS filesystem.

If you intend to add Windows, it's much easier to install Ubuntu over Windows than the reverse because Windows is very picky about the boot loader.  If you install Ubuntu second, it will install the grub boot loader which knows how to handle Windows.

---

### Post by zombifier25 on 2012-12-10
> **rabot said:**
> Advice coming thick and fast. Thanks a lot.

I think it's all sorted now. ext4 for Ubuntu install and NTFS for the data partition.

I've read that with the NTFS 3g driver, Ubuntu can read and write on the NTFS file system. But I guess it wasn't made clear it's for WUBI?

And if you look right at the bottom of this page, it says the filesystem should be the same:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

Anyone else care to comment on Lubuntu and Xubuntu flavours and their preferences and opinions?

Linux have support for reading/writing NTFS partitions perfectly. The bottom statement means that the home partition and the system partition should be the same type, but I'm not exactly sure what it means, so disregard it.

> **rabot said:**
> Is there any advatange to doing this little trick with the /home folder? Will I miss anything if I ignore it all and go ahead with my Data partition?

If you do this, then you'll be able to access the files in the Data partition from your home folder. It's not necessary, and you won't miss anything.

---

### Post by rabot on 2012-12-10
> **SeijiSensei said:**
> You'll be happier if you create a separate NTFS partition to share between the operating systems, while putting /home on its own partition with an ext4 filesystem.  Keeping /home separate lets you change the Linux OS without losing data.  You really cannot use NTFS for /home because of the variety of "hidden" files that *nix uses for user-level configurations.  (These are files and directories whose names begin with a dot like ".config".)  Also you cannot enforce *nix permissions on an NTFS filesystem.

If you intend to add Windows, it's much easier to install Ubuntu over Windows than the reverse because Windows is very picky about the boot loader.  If you install Ubuntu second, it will install the grub boot loader which knows how to handle Windows.


I'm waiting for the next version of Windows (W9?) to try out. I tried out W8 and it's a waste of time for desktop. In the meantime I thought I'd get acquainted with the performance that Ubuntu/Lunbuntu has to offer. And maybe stick to that... Or maybe not.

---

### Post by oldfred on 2012-12-10
If anything part of the problem of Linux is too much choice in the way of Windows managers, desktop environments and all the various sets of default applications each flavor installs. Ubuntu has many and then there are all the other distributions and many of them also can be customized.

I got started with Ubuntu, need menus as I cannot remember a name to type into Unity to launch something and consider having to use keyboard when using mouse to not be ergonomic. So I install standard Ubuntu but then convert to gnome-panel or fallback which looks and works almost like the old gnome2. But everyone has a preference and some of the new ways may be better.

I do like to have an extra 25G / (root) partition available to install something new to try. While you can install all the Ubuntu DE into one it gets complicated then and difficult to separate later. 

       All Desktops in one:
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)
Both Unity and standard Gnome classic use Compiz as a WM, whereas Unity-2D and Gnome classic (no effects) use Metacity. 
Gnome shell and Cinnamon (which is a gnome-shell extension) use Mutter as a WM.

            Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

    
Then if you want to get fancy & show off:
       Delectable December Screenshots
[http://ubuntuforums.org/showthread.php?t=2089919](http://ubuntuforums.org/showthread.php?t=2089919)

---

