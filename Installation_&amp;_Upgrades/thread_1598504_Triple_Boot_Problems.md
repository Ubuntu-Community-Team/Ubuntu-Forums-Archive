---
title: "Triple Boot Problems"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2010-10-16
Windows 7 (64 bit)
Ubuntu 10 (64 bit)
Windows Server 2008
 
I've been having nightmare problems getting these to go together. The 2 Win OS's are fine together of course. But when I install Ubuntu with 'em I get conflict.
 
1 SATA HDD (with two partitions for each Win OS)
1 IDE HDD (for Ubuntu 10)
 
1. First I had errors and had to replace the hard drive.
 
2. Second time, I had started to install Linux, then it failed. Here I found out the stupid Ubuntu 10 disc overwrote the Windows 7 100MB partitition which has the boot loader. That made me have to start from scratch.
 
3. Thirdly, I finally got a successful triple boot (by unplugging the Windows drive), but.... It won't boot to Linux. Sometime I can press F12 and it will allow me to choose the device to boot to (but it only works sometimes). Therefore, I can choose the HDD which Linux is on.
 
I need to figure out how to either customize the Win Boot Loader to fit Linux in there (I don't where that is in Win7) there is no more 'edit' button in Sys Properties (not sure where the file is), maybe do it in Server 08. OR I could get rid of the 100 MB and install Grub Loader. I had issues with GRUB 2 (fyi) I prefer the original Grub that came with Ubuntu 8.
 
By the way, what happened to root in Ubuntu 10? I don't see it listed in the Users console. Is there a default password for it. I can't do a su or sudo.???

---

### Post by arpanaut on 2010-10-16
I've seen people who have issues with grub and grub2 have success with using:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I used it with a Vista + Ubuntu install where the owner of the rig didn't want the mbr overwritten by grub.
Has worked flawlessly for a couple of years, Just have to be careful where grub is installed on updates and upgrades.

Good Luck!

---

### Post by kakashi_12 on 2010-10-16
I don't care which way I go, as long as it works. I don't want to overwrite any system files any more. I could also try to find out which key it was that I hit to choose the boot device. I swore it was F12, but it only worked one time. Maybe it was a different key or at a different time.

---

### Post by drs305 on 2010-10-16
You should be able to set it up this way:

Install Grub to the MBR of the IDE drive and put the Grub files in their normal position in /boot/grub. Running "sudo update-grub" from within the Ubuntu install should put the Window OS's into the Grub menu.

Leave your Windows MBR alone. If you change the boot order to boot this drive first, it will boot to the Windows menu with no Ubuntu option.

Change your BIOS to boot the Ubuntu drive first. It will see the Grub MBR instructions and boot to the Grub menu. Ubuntu and Windows selections should be visible.

If you post the information (RESUTLS.txt) from the boot info script we can see what the status of your boot files is:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by kakashi_12 on 2010-10-16
Unfortunately... and stupidly enough... my bios does not let me set the IDE to a boot device....
 
unless i change it to be the first hard drive and then it MIGHT become an option in the boot device priority list instead of the SATA drive.
 
Do I need to be online to run an update grub cmd? I don't have internet service yet.

---

### Post by drs305 on 2010-10-16
> **kakashi_12 said:**
> Unfortunately... and stupidly enough... my bios does not let me set the IDE to a boot device....
 
unless i change it to be the first hard drive and then it MIGHT become an option in the boot device priority list instead of the SATA drive.
 
Do I need to be online to run an update grub cmd? I don't have internet service yet.

Setting it as the first drive is probably how your BIOS will allow it to boot first.

No, you do not need to be online to run the "update-grub" command. The command runs scripts in the /etc/grub.d folder, which update the /boot/grub/grub.cfg file. The command does not use off-system resources.

---

### Post by kakashi_12 on 2010-10-17
THANK YOU! Worked like a charm. Now I have two boot loaders. I will go ahead and post pics too... cause i know someone saying awhile back that pics of multiple boot loaders here would have 100 words or something.
 
I still have a couple of preferences i want to change. First, how do I not show my username at the login? I want to input UN and PW both, i dont' want the UN to show automatically.
 
Second, I want to edit the menu.lst . I haven't done it in so long, I don't remember what directory it is in or how to cd the directory back to filesystem from home folder. Plus when I try to go to "su" or "sudo" i get access denied. What is the default pw for root in ubuntu 10? It wont show up in the users management console. Do I need to add root manually to be able to access it first or what?
 
Third, anyone know where the file is located in Windows 7 to edit the boot menu. I just want to edit the names of the OS's that display.
 
Thanks again.
 
(Pic: First it goes to GRUB, then you have ubuntu boot options or the option that says "Windows 7 Loader". The Loader option goes to the Windows Boot Loader to give you the choice of Windows 7 or Windows Server 2008. If I need to go back to GRUB, I can press Escape from Windows Loader and reboot.)

---

### Post by drs305 on 2010-10-17
Glad it worked.  :-)

To not display your user name, I believe you can adjust this from System, Administration, Login Screen. There is an option for "Show List of Users". I would assume unchecking it might be what you want.

Normally you don't become root, but rather use "sudo" or "gksudo" with another command. For instance, in order to edit your fstab file you would enter:
```
gksudo gedit /etc/default/grub
```
It will ask for *your* password, not root's. If you can't use these, you may not be a member of the "admin" group. You can add yourself - there are posts explaining how to do so.

There are various files for editing Grub. If you tell us what you want to change we can tell you where to look. The basic settings are contained in */etc/default/grub*. After saving changes, you must run "sudo update-grub" to have the changes take effect.

---

### Post by kakashi_12 on 2010-10-17
Like I said... same with the windows loader, just want to edit the names of the OS's and then edit out a few lines in grub like the OS choices I don't need just by putting comments in (so that i can always uncomment later if i want). maybe i will try to change the color of the text too. i think i had a program to do that part. but anyway ya, that's what i want to do.
 
Example: Linux Ubuntu 10 (64 Bit)
Root Terminal
 
Windows 7 Professional (64 Bit)
etc

---

### Post by drs305 on 2010-10-17
> **kakashi_12 said:**
> Like I said... same with the windows loader, just want to edit the names of the OS's and then edit out a few lines in grub like the OS choices I don't need just by putting comments in (so that i can always uncomment later if i want). maybe i will try to change the color of the text too. i think i had a program to do that part. but anyway ya, that's what i want to do.


With Grub 2, the only easy way to do this is to make a custom menu and edit the choices within that file.  That is very easy. Otherwise, you will have to edit multiple scripts and it won't be easy. 

See the "Title Tweaks" link in my signature line for what's involved in changing menu titles. It's not rocket science, but it's certainly not child's play either. ;-)

As for coloring things, you can change the default selected and non-selected colors, and background colors. Here is the link for doing that:
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming]("https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming")

---

### Post by kakashi_12 on 2010-10-17
I use to be able to just edit the menu.lst file before in ubuntu 8.
any idea how to do the boot manager for win7?

---

### Post by kakashi_12 on 2010-10-17
Nvm. Finally found the answer. bcdedit. There is also a gui version. I'm going to try to do this the way im use to by editting the menu.lst like i use to. i think i can find it now. i should only have to edit the one file right (just renaming an entry) if it does not work, then i'll try that grub 2 with the link you gave me.

---

### Post by kakashi_12 on 2010-10-18
Nope. Su and sudo still does not work. i made myself admin but still dont have access to root through terminal. this is even a bigger problem. cant get updates, apps, or anything.

---

