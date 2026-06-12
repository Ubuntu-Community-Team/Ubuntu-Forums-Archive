---
title: "Ubuntu - Wubi-  Does not Uninstalll"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2012-06-22
[color=red]_**solved**_[/color]

---

### Post by Frogs Hair on 2012-06-22
If the disk was reformatted three months ago Windows including Ubuntu should have been removed and Windows would have had to been installed again. Wubi installs Ubuntu in a folder inside Windows.

With a Wubi installation in local disk C there is a Ubuntu folder with uninstall icon. I don't understand how the folder or Ubuntu could be there if the disk was reformatted.    

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by balkrish999 on 2012-06-22
> **Frogs Hair said:**
> If the disk was reformatted three months ago Windows including Ubuntu should have been removed and Windows would have had to been installed again. Wubi installs Ubuntu in a folder inside Windows.

With a Wubi installation in local disk C there is a Ubuntu folder with uninstall icon. I don't understand how the folder or Ubuntu could be there if the disk was reformatted.    

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Thanks Solved

---

### Post by Frogs Hair on 2012-06-22
Did you locate the folder I wrote  about ?  There is a trouble shooting guide for removal at the link posted .

Wubi Mega Thread:  [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by balkrish999 on 2012-06-23
> **Frogs Hair said:**
> Did you locate the folder I wrote  about ?  There is a trouble shooting guide for removal at the link posted .

Wubi Mega Thread:  [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)


Yes, there folder is still there

Im Guessing i should do this right?

>  
**How do I manually uninstall Wubi?**

 Remove C:\ubuntu and C:\wubildr*  
In  Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi  line. Alternatively you can modify the boot menu via Control Panel >  System > Advanced > Startup and Recovery and pressing "Edit". For  Windows 98 you have to edit C:\config.sys and remove the Wubi block. For  Windows Vista/7, you can use the built-in *bcdedit* command or install [EasyBCD]("http://neosmart.net/EasyBCD/") to edit the boot menu. To use *bcdedit*, run *cmd.exe* as an administrator, then enter *bcdedit* to show all boot entries, note the {GUID} specified for the Ubuntu entry, and then remove it: *bcdedit /delete {GUID}* 
To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\[CurrentVersion]("https://wiki.ubuntu.com/CurrentVersion")\Uninstall\Wubi 
An  easy method of removing this registry key is to paste the following  text into a plain editor such as Notepad, close and save the file as  something like removeWubiKey.reg (you may wish to go to Folder Options  > View and disable the "Hide file extensions for known file types"  option to check that the .reg extension has been applied correctly).  Then you can perform the rest automatically by opening the file in the  normal Windows manner, or choosing the "Merge" option from the right  click context menu. Note: The formatting is rather strict, so copy the  text exactly for best results. *You may need to be logged in as the  administrator to delete the key, depending on the version of Windows you  are using. User Account Control in Vista may also ask for permission,  in the typical fashion.* 

REGEDIT4  [-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]After  deleting the registry key, Ubuntu may still appear in the program list.  If this is the case, you may be asked if you would like to remove the  item from the list. 


---

### Post by Frogs Hair on 2012-06-23
In side the folder is an uninstall icon shaped like a Ubuntu logo , just click it and see if it works.

---

### Post by retchid on 2012-06-23
W drive seems like you have far too many version of windows on

time for a late spring clean.  Copy document folders into a free partition or USB

Reinstall windows on C: it will keep a copy of old windows on C if you need it and you wont lose other partitions.   When you are sure that you have not got rid of anything important delete OLDWindows directory off of c to recover the space.  

Then Install Ubuntu via windows on C:

You bootscreen will show windows on C, UBUNTU and any other windows it finds on your system.

Personally would just dump all other versions of windows and go with Win7 and UBUNTU

Come to think of it that is what I did last weekend.  Problems solved.
(but only because I was Using Opensuse and had to switch back to Ubuntu to get my Mybooklive drive to work)

Sometimes its just easier to start again and quicker than messing about for 3 days.

You can then use W and other partitions for something  useful instead of operating systems by formatting them.

---

