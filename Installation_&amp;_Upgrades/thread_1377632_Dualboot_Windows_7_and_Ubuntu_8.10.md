---
title: "Dualboot Windows 7 and Ubuntu 8.10"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by CEW11 on 2010-01-10
I had Windows Vista on my laptop and then installed Ubuntu 8.10 on the D: drive. When I started the computer, it gave me the option to choose Vista or Ubuntu. That was working fine until I upgraded Vista to Windows 7. Now when i turn on the computer it boots straight into Windows. Is there any way to get it back to giving me the option of choosing an Operating System? Or is there a way to recover my data from the 'ubuntu' folder that was created in windows and then restoring that data to a new install of Ubuntu?

---

### Post by Elieser on 2010-01-10
I have the same problem, installed Windows 7, then installed Ubuntu. But I never receive the screen where I can choose which OS to start up. Simply starts up in win7.

---

### Post by kansasnoob on 2010-01-10
> **CEW11 said:**
> I had Windows Vista on my laptop and then installed Ubuntu 8.10 on the D: drive. When I started the computer, it gave me the option to choose Vista or Ubuntu. That was working fine until I upgraded Vista to Windows 7. Now when i turn on the computer it boots straight into Windows. Is there any way to get it back to giving me the option of choosing an Operating System? Or is there a way to recover my data from the 'ubuntu' folder that was created in windows and then restoring that data to a new install of Ubuntu?

This should be helpful:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2010-01-10
> **Elieser said:**
> I have the same problem, installed Windows 7, then installed Ubuntu. But I never receive the screen where I can choose which OS to start up. Simply starts up in win7.

Your situation seems different because you installed Ubuntu after installing Win 7, eh?

You also don't mention what version of Ubuntu?

The OP has 8.10.

I would suggest **starting your own new thread** and providing more details. It might be necessary to see the reults of The Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by CEW11 on 2010-01-10
> **kansasnoob said:**
> This should be helpful:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Thanks for that link.
I did try follow something similar to that earlier and it did not work.
I tried again now and did the following:
Booted from CD.
Chose the option: "Try Ubuntu without any change to your computer"
At the Ubuntu desktop, I opened a terminal from the menu
Typed 'sudo grub'
The following came up: minimal bash-like line editing is supported...
Typed 'find /boot/grub/stage1'
It said: Error 15 File not found

This is the same thing that happened earlier and I cant understand why?

---

### Post by kansasnoob on 2010-01-10
> **CEW11 said:**
> Thanks for that link.
I did try follow something similar to that earlier and it did not work.
I tried again now and did the following:
Booted from CD.
Chose the option: "Try Ubuntu without any change to your computer"
At the Ubuntu desktop, I opened a terminal from the menu
Typed 'sudo grub'
The following came up: minimal bash-like line editing is supported...
Typed 'find /boot/grub/stage1'
It said: Error 15 File not found

This is the same thing that happened earlier and I cant understand why?

Are you sure you have Ubuntu 8.10 and not 9.10?

Karmic (9.10) fresh installs now have grub2 and the grub shell is deprecated.

If you're unsure just post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by CEW11 on 2010-01-10
> **kansasnoob said:**
> Are you sure you have Ubuntu 8.10 and not 9.10?

Karmic (9.10) fresh installs now have grub2 and the grub shell is deprecated.

If you're unsure just post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Ok heres the results attached

---

### Post by ajgreeny on 2010-01-10
> **CEW11 said:**
> I had Windows Vista on my laptop and then installed Ubuntu 8.10 on the D: drive. When I started the computer, it gave me the option to choose Vista or Ubuntu. That was working fine until I upgraded Vista to Windows 7. Now when i turn on the computer it boots straight into Windows. Is there any way to get it back to giving me the option of choosing an Operating System? **Or is there a way to recover my data from the 'ubuntu' folder that was created in windows and then restoring that data to a new install of Ubuntu?**
I assume from this that you used wubi to install ubuntu, rather like another application inside your windows system.  If I am right, a lot of what you have been told here will not apply, as you will not have a separate ubuntu partition.  I hope the ubuntu folder you say was in windows is still there after your upgrade to windows 7, but unfortunately I do not know how to enable your recovery of that folder and its files, though I am pretty sure there is a fairly simply way to do so.

EDIT:
OK, I've just read the output from your boot info script and was correct, you used wubi.  I have no idea if this works or not as I know almost nothing about using wubi, nor the files it produces in windows, but see if you can still see the folder ubuntu, and if so see if you can navigate down to ubuntu/disks/home/username.  That may be your ubuntu home files and folders, but for all I know this may be an encrypted filesystem of some sort that windows makes, and it may all be undecipherable from within windows.  Worth a try though.

---

### Post by warfacegod on 2010-01-10
I don't if this will help or not but I've been seeing lots of threads about wubi installs crashing after 9.10 update and this seems to work:


See post #8
[http://ubuntuforums.org/showthread.php?t=1377175]("http://ubuntuforums.org/showthread.php?t=1377175")

---

### Post by CEW11 on 2010-01-10
> **ajgreeny said:**
> I assume from this that you used wubi to install ubuntu, rather like another application inside your windows system.  If I am right, a lot of what you have been told here will not apply, as you will not have a separate ubuntu partition.  I hope the ubuntu folder you say was in windows is still there after your upgrade to windows 7, but unfortunately I do not know how to enable your recovery of that folder and its files, though I am pretty sure there is a fairly simply way to do so.


When I installed, I did it from the cd inside windows (I think) and after clicking install a box came up, where I could choose where to install ( I chose d:) and to chose the size and a username and password ( As far as I can remember)
And yes that ubuntu folder is still there.

---

### Post by CEW11 on 2010-01-10
> **ajgreeny said:**
> I assume from this that you used wubi to install ubuntu, rather like another application inside your windows system.  If I am right, a lot of what you have been told here will not apply, as you will not have a separate ubuntu partition.  I hope the ubuntu folder you say was in windows is still there after your upgrade to windows 7, but unfortunately I do not know how to enable your recovery of that folder and its files, though I am pretty sure there is a fairly simply way to do so.

EDIT:
OK, I've just read the output from your boot info script and was correct, you used wubi.  I have no idea if this works or not as I know almost nothing about using wubi, nor the files it produces in windows, but see if you can still see the folder ubuntu, and if so see if you can navigate down to ubuntu/disks/home/username.  That may be your ubuntu home files and folders, but for all I know this may be an encrypted filesystem of some sort that windows makes, and it may all be undecipherable from within windows.  Worth a try though.

I can get into that ubuntu folder but can only go as far as ubuntu/disks. Dont see any home folder there - all i can see is boot, shared, root.disk, and swap.disk

---

### Post by PRC09 on 2010-01-10
I think when you do a Win 7 upgrade over a Vista install it asks at some point if you wish to save your files for Vista or not.When it saves them it will create a folder called win.old or windows.old on your C drive....If I remember correctly.I am assuming that all the Vista files and folders including the Ubuntu folder would be in that file in Win7......

---

### Post by CEW11 on 2010-01-10
> **PRC09 said:**
> I think when you do a Win 7 upgrade over a Vista install it asks at some point if you wish to save your files for Vista or not.When it saves them it will create a folder called win.old or windows.old on your C drive....If I remember correctly.I am assuming that all the Vista files and folders including the Ubuntu folder would be in that file in Win7......


I'm sure that does happen - but ubuntu was installed on my D drive which was left untouched after upgrading - so its all still there

---

### Post by kansasnoob on 2010-01-10
> **ajgreeny said:**
> I assume from this that you used wubi to install ubuntu, rather like another application inside your windows system.  If I am right, a lot of what you have been told here will not apply, as you will not have a separate ubuntu partition.  I hope the ubuntu folder you say was in windows is still there after your upgrade to windows 7, but unfortunately I do not know how to enable your recovery of that folder and its files, though I am pretty sure there is a fairly simply way to do so.

EDIT:
OK, I've just read the output from your boot info script and was correct, you used wubi.  I have no idea if this works or not as I know almost nothing about using wubi, nor the files it produces in windows, but see if you can still see the folder ubuntu, and if so see if you can navigate down to ubuntu/disks/home/username.  That may be your ubuntu home files and folders, but for all I know this may be an encrypted filesystem of some sort that windows makes, and it may all be undecipherable from within windows.  Worth a try though.

I'm in the same boat. I don't know Wubi well enough to be of any help, sorry.

---

### Post by PRC09 on 2010-01-10
Sorry, missed the D: part....

---

### Post by PRC09 on 2010-01-10
Dont Know if this will help but this is a similar scenario,read it all before using any of the commands tho.....

[http://ubuntuforums.org/showthread.php?t=1007816](http://ubuntuforums.org/showthread.php?t=1007816)

---

### Post by CEW11 on 2010-01-10
> **PRC09 said:**
> Dont Know if this will help but this is a similar scenario,read it all before using any of the commands tho.....

[http://ubuntuforums.org/showthread.php?t=1007816](http://ubuntuforums.org/showthread.php?t=1007816)

Well I followed the instructions and for the first time for me something actually worked!
Now thankfully I have all my files back.
Thank you very much for the link

---

### Post by PRC09 on 2010-01-10
Your welcome.....

---

### Post by CEW11 on 2010-01-10
now just is it possible to copy the files to a usb - when I tried it wont allow me - says I dont have permissions: when i right click and enter permissions it says im not the owner so i cant change permissions

---

### Post by PRC09 on 2010-01-10
I dont know what commands you are using but you may have to use sudo in front of the command to enable you to copy them to another location.....

---

### Post by CEW11 on 2010-01-11
thanks that worked

---

