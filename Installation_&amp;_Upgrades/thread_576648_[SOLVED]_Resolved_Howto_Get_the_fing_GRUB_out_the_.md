---
title: "[SOLVED] Resolved: Howto Get the f***ing GRUB out the MBR, and start Linux from USB d"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by quandary on 2007-10-15
Hi there!

This is to describe the solution to a problem I had, and that I saw many other people having, yet no working general solution seemed to be around. So as I managed to resolve the problem, I thought it might be useful for others when I post the problem's solution here .

Short description of the problem/symptoms:
---------------------------------------------
Having a notebook with a internal HD, with Windows installed on the entire hard drive.
Wanting to install Ubuntu Linux on an external USB hard drive, doing that.
GRUB installs itself in the internal HD's MBR, and you will be unable to boot Windows without having the USB drive connected to your notebook.

...You are annoyed, because you will have to always carry the USB drive with the notebook...

So you erase GRUB from the MBR and reinstate the Windows MBR, which will make you able to boot Windows without external HD again (and preserving all data), but you will not be able to boot Linux anymore...

...This annoys you again...

Now you try to have GRUB in the MBR of the USB hard drive, but somehow, this doesn't work.
Grub puts an error message like 'unable to mount partition'
---------------------------------------------


Description/Solution, in my example:
I have a Notebook, with one 60 GB internal hard drive, on which WinXP is installed (no space left). And so, i wanted to give Linux a try, but couldn't repartition the hard disk (too few space left). So I used the USB hard drive case i used to backup the data from my old notebook (which unfortunately broke down due to a short-circuit on the mainboard) and it's old 40 GB HD. In simpler terms, i installed Ubuntu on a external USB hard drive. 

First, i was astonished that the driver worked, so I could do it. Everything went well, I could start Ubuntu from CD, install it, and then start it from the USB HD. So far so good.

But then i had to notice that as soon as i plug the USB drive out, i couldn't start windows anymore. Obviously, GRUB managed to install itself in the MBR, and needed some data from the USB drive to start Windows, even though Windows was entirely on the internal HD.

Well, so I always had to carry that USB drive with the notebook, which was very annoying, especially if I forgot the USB drive and couldn't boot up anything anymore...

However, I left it that way, out of fear to lose my data when playing around the MBR and the partitions (and because i was to lazy to do a backup)...

Recently I installed Vista (yes, it still is buggy, i know), so had to backup my data anyway.
Of course, Vista overwrote the MBR (without asking or warning, by the way). So I could start my PC without having to have the USB drive connected. Oh what a happy day!

I thought now that the f***ing GRUB is out of the MBR, i simply set the BIOS to boot from USB-Drive first, then it will start Ubuntu. Bad luck. Actually i couldn't start Ubuntu anymore.

So the first thing i thought was: oh ****, i forgot to backup the data on the Linux drive, now maybe it's all lost...

Fortunately I had to move some date from Windows to the Linux drive earlier on in XP.
So I earlier searched for such a thing and found a pluggable/installable ext2/3 file system driver for Windows XP ([http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)).  I thought hopefully it works on windows vista, because then maybe i can read out all the remaining data still left on the drive. Else I would have to reinstall XP first (and some hours would pass by)...

Well, bad luck, first I couldn't install the IFS driver (Vista was complaining). So i started the installation in WinXP SP2 compatibility mode (Vista stopped complaining and installed it).
But when trying to give the IFS drive a windows drive letter (in order to see it in Windows Explorer), rundll32 crashes... But before giving up and install XP again, i searched for a alternative, and found Ext2Fsd-0.31a.exe on Sourceforge.net (wow, even OpenSource) 
[[http://sourceforge.net/project/showfiles.php?group_id=43775]](http://sourceforge.net/project/showfiles.php?group_id=43775]). 

I downloaded and installed it, and afterwards, it even worked!!! 
(You have to start the program up, then give your Linux drive a windows drive letter first)

Wonderful, all the data was still left on the drive, you just couldn't boot Ubuntu...
So I immediately evacuated all necessary data from the Linux partition a safe place (on another external HD).

Then, having all the data evacuated, i thought i should anyway fully reinstall Linux on that external HD, because I once had a crash that damaged the partition, and erased some executable data, making the OS somewhat unstable...

So i did what i thought, and swiftly, Linux and Windows could now be booted with the external HD plugged in without any problem. But, oh wonderful, i also had GRUB back in my internal HD's MBR, which meant i couldn't boot anything without the external HD again. Damned! F***ing GRUB!

So, the first thing I wanted to try now, is to throw GRUB out the MBR, without loosing data.
I found advice by searching google, but because of some odd reason, the commands on the windows recovery console didn't work, and on XP I couldn't even get to the recovery console...
Obviously not supplied on my edition of the WinXP install CD. Damn.

So here is how i managed to get GRUB out the MBR without losing any data:
************************************
To do so, do the following:
When your PC starts, make sure the primary boot device is the CD/DVD drive.
(On my PC: Press F2 on startup to enter the BIOS. Select Boot Order. Press Enter. Set the CD Drive as No. 1, the Hard Disk as No 2, Press ESC, select "Save settings and exit". DO NOT ALTER ANY OTHER SETTINGS THAN THE BOOT ORDER, OR YOU might SCREW-UP YOUR COMPUTER!!)

Now you can boot-up using your WinXP/Vista install CD. When it says: press any key to boot from CD, DON'T press any key. Windows should then start using the boot image from the CD, and the rest from your Hard Drive. 

If you are not sure that this works for you, download a boot image CD from the internet (there are quite many out there). Burn the image to cd, AND TEST WHETHER IT WORKS OR NOT.

- Anyway, just find out how to boot Windows. Anything that works will do fine.

Now when you are in Windows, download MbrFix.exe from 
[http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)
Install it/Unpack it.

On your Explorer Bar, click on Start --> Run
type 'CMD' (without the ') , Press ENTER.

Change to the folder you copied MbrFix to. In case you put it on the desktop in the folder MbrFix, do this:
type 'cd "c:\Documents and Settings\YOUR_USER_NAME\Desktop\MbrFix" '

Now type (this is optional, but a GOOD idea):
'MbrFix /drive 0 savembr Backup_MBR_0.bin'
this creates a backup Copy of your current MBR

If you run WindowsXP/2000 type:
MbrFix /drive 0 fixmbr /yes

else If you run Windows Vista, like me, type:
MbrFix /drive 0 fixmbr /vista /yes

The MBR of your Windows is now restored. (This did not delete any of the data that was on your drive, it just puts back the Windows BootLoader to where it belongs).

Now remove any CD from the CD-Rom drive and restart. Windows should now start up normally.

Should anything go wrong, you can boot up Windows again (from CD) and type:
MbrFix /drive 0 restorembr Backup_MBR_0.bin
The program will ask: 'You are about to Restore MBR, are you sure (Y/N)?'
Type 'Y'
With that, you put the GRUB trash back to your MBR.
************************************

Now we basically are back to where we started. (If you did't install Ubuntu the wrong way, you can also start here.)

Now put in the Ubuntu CD in your CD-Rom drive.
Start ubuntu, install it.
As language choose English (or whatever you want)
Answer the question about your timezone and keyboard. If you don't use the US-keyboard layout, it's a good idea not to use characters other than a-z and A-Z  (just in case) for your username/password. Anyway, you can change that later-on. And remember that Linux password, like Windows passwords, are case-sensitive, that is to say if your password is 'HeLLoWoRLd' that's not the same as 'helloworld'... 

Now if asked about the installation, select 'Guided installation'.
Click next

Somewhere, you well be asked where to install Ubuntu to:
in my case i can select:
sda: 60 GB HD
sdb: 40 GB HD

So as my internal HD is 60 GB, sdb must be the USB drive. Select sdb, or whatever you have to. Your settings might be different from mine, so USE YOUR BRAIN, or you will overwrite your windows drive with all the data on it...

Somewhere there should be a button labeled 'Advanced'. Maybe you have to click the next button first. If you click on the advanced button, you can select where you want to install GRUB to. 

In my case the default that you can see there is (hd0). Now hd0 will put GRUB on my/your Windows MBR. Don't do that, or you will have the boot problem i had.
But the good question is what to write there.
I thought, as the default is '(hd0)' it might be logical to write '(hd1)' there. Bad luck. That didn't work. So i tried (sdb). I tried it with and without brackets. Bad luck again. Then i tried '/dev/hd1'. Bad luck again. 
Then I searched the web, and found you have to type: 
/dev/sdb
(and remember: Linux is case-sensitive, put it all in lowercase letters or it won't work...)

Actually I'm not sure whether this is correct, it's just the one i get to work afterwards...

Now complete the installation. Just click next everywhere.
Don't forget to remove the CD before you restart.

PS: You now have to change the BIOS boot order to try it out. Change the primary boot device to USB, second to cd, 3rd to HD.

Now, you have Linux installed on the USB HD, and the Windows MBR should be untouched.
So if you remove the USB drive, and all cd's, windows should start normally.

Now switch the computer off. Plug in the USB external hard drive and try to boot from there.
Basically it should work now, and you should see GRUB asking you what to start.
Select Ubuntu as normal, press enter.

Basically it should work now. But bad luck, at least for me. GRUB outputs an error message, something like 'could not mount drive'.

---*********---
Until now, you could find every info i wrote here on the internet, too.
Now here comes the actual point of this post.
---*********---
Plug out your USB hard drive
restart the computer.
Start Windows (in my case Vista).

I mentioned earlier Ext2Fsd-0.31a.exe from SourceForge.net, which i used to backup the data.
If you haven't installed it yet, install it. If you use WinXP, i recommend to use the IFS utility instead.
You maybe have to restart windows for the driver installation to become effective.

When your logged in, plug your USB hard drive back in.
Now if you're in windows, 

if you use Vista:
start Ext2Fsd from the start menu, give your USB drive the drive letter z (or any letter you want). 

Else if you use XP/2000:
If you use the IFS utllity, you have to open 'Control Panel', IFS drives, and give your USB drive the drive letter z (or any letter you want)
END IF

Now you should be able to see your Linux drive in the WindowsExplorer/MyComputer.

So go to MyComputer/WindowsExplorer now, select z:\boot\grub\menu.lst
(if you use another letter than z, replace z with that letter; that should be self-evident)

Right click the menu.lst file with your mouse, select 'Open With'.
Open it with MS-WordPad (if you open it using Notepad, you will have the problem that Windows does not use the same escape-sequence for each new line, so it will be a holy mess...)

--------------------- Remark ---------------------------------------
In Vista, you find Wordpad @ path:
C:\Program Files\Windows NT\Accessories\wordpad.exe

I think (if i remember right, but i'm not sure.) in Windows XP wordpad is @ path: 
c:\windows\wordpad.exe
--------------------- End of Remark ------------------------------


Somewhere
z:\boot\grub\menu.lst
will probably look something like this:

----------------------------------------------------------------------------------------------
title		Ubuntu, kernel 2.6.20-15-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b78f8799-d1eb-4ab6-9281-9b754eaea4a3 ro quiet splash

initrd		/boot/initrd.img-2.6.20-15-generic

quiet

savedefault



title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b78f8799-d1eb-4ab6-9281-9b754eaea4a3 ro single

initrd		/boot/initrd.img-2.6.20-15-generic



title		Ubuntu, memtest86+

root		(hd0,0)

kernel		/boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Windows Vista/Longhorn (loader)

root		(hd1,0)

savedefault

chainloader	+1
----------------------------------

It found out that all (hd0,0) and all  (hd1,0) had been mixed up. So the only thing i had to do, is to rename all (hd0,0) to (hd1,0), and all  (hd1,0) to (hd0,0) in the menu.lst file. 

Then save menu.lst and reboot. Now, everything should be fine.
Now I can start Windows without having GRUB anywhere on my internal HD, and if i plugged in the external USB HD, it started GRUB, and i could select between Ubuntu Linux-Kernel Versions and Windows Vista to boot, and everything, even booting Vista, worked well :guitar:.



So the whole point is, that in GRUB the HD nubmers get mixed up, and you have to fix them manually. If you do that, everything will work fine. At least it did for me...

So far, give it a try, and see whether it works. Maybe it's a good idea to make a backup copy of menu.lst in case what i wrote doesn't work, or you have screwed it up...




HOWEVER, no matter whether you can boot Linux now or not, with my tip you should always be able to remove the f***ing GRUB from your MBR, and get Windows starting again, without having to reinstall it each time and without loosing any data :lolflag:...
I tried it. It worked for me. I did not loose any data.

However, it's always a good idea to have a backup, whether you are playing around with Linux or not ...



------------------------------------------ Final remark ------------------------------------------
If you have several partitions, then maybe the number after the comma (in '(hd1,0)' or '(hd0,0)' ) is different, in windows use: 
'MbrFix /drive 0 listpartitions'
To see drive0's partition's numbers. 
(You have to subtract 1, because Windows numbering starts at 1, Linux numbering at 0...)

------
You should see something like:
MbrFix /drive 0 listpartitions
# Boot Size (MB) Type
1  Yes     151001    6  DOS 3.31+ 16-bit FAT (over 32M)
2          1623   12  WIN95 OSR2 32-bit FAT, LBA-mapped
3             0    0  None
4             0    0  None
------
with 1,2,3,4 being the partition's numbers (remember as i said, subtract 1 to get the Linux number).
----------------------------------- End of Final remark ------------------------------------------


Hope that helped someone.


Oh: Should you know the GRUB programmer/programmers, give them a kick in the butt, with a nice greeting from me. They've managed to RUIN MY WEEKEND...

---

### Post by maybeway36 on 2007-10-15
Another (free) way to clear the bootloader from the MBR is with DOS:
```
fdisk /mbr
```
You can use a FreeDOS or MS-DOS boot floppy, or even a Knoppix CD by typing "dos" at the boot prompt.

Here's the floppy I use:
[http://www.finnix.org/Balder]("http://www.finnix.org/Balder")

---

### Post by quandary on 2007-10-15
Oh, I have to make an appendum to my post:

I just saw it gets even worse:
AFTER I have done the FIRST UPDATE to my new Ubuntu Linux and played a game, which horribly crashed within 2 minutes, ..., whereupon i had to turn the power of (because CTRL + ALT + DEL as well as CTRL + ALT + BACKSPACE didn't help...), Ubuntu didn't start anymore...
[don't play Scorched 3D, i warned you now]

You will have to UNDO EVERY CHANGE YOU MADE to the /boot/grub/menu.lst 
Probably because of the update, but whoever knows...

Aaaaaaaaaargh... Somebody please kill the GRUB team!!!


However, as to add to my previous post: i just saw you don't have to install the ext2 file system in Windows. When you boot Ubuntu Linux from CD you have a live environment.

Just open the console (under Applications-->System Tools-->Konsole) there.
type 'cd /media/disk/boot/grub'
then type 'sudo gedit menu.lst'
enter your password, do the necessary changes, save and quit.
type 'exit' to exit the console
And restart your Linux.

Works again then. :popcorn:

---

### Post by quandary on 2007-10-15
> **maybeway36 said:**
> Another (free) way to clear the bootloader from the MBR is with DOS:
```
fdisk /mbr
```
You can use a FreeDOS or MS-DOS boot floppy, or even a Knoppix CD by typing "dos" at the boot prompt.

Here's the floppy I use:
[http://www.finnix.org/Balder]("http://www.finnix.org/Balder")

The usage of DOS requires a Floppy drive. Not everybody has one. In new notebooks, floppy drives are inexistent/optional.
Also DOS/Knoppix and some CD-ROM drivers won't work. 
So it's better to use a XP/Vista CD/DVD, which works in (probably) all cases.
Besides, if you already have Windows, using the Windows CD is also Free... 

However, for older systems, the DOS floppy is of course the better and faster way.
I was writing with my notebook in mind. ;-)

---

