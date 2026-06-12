---
title: "Triple boot - XP wiped out my Ubuntu and Vista options"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by LazyEngineer on 2008-05-28
This may be a somewhat unique question - I started with Vista, then partitioned and installed Ubuntu.  Both OS booted and worked well with a Dual boot.  Then needed XP for my work VPN system, so installed it in another partition.  but instead of being able to triple boot, I now am only bootable direct into XP.  Any tips on how to make Ubuntu my default boot again?

I tried using the Gnome Partition Manager after doing a Ubuntu non-install boot from the CD, but it didnt' work - it acted like all 150 GB of my HDD was one unformatted disk, rather than 3 partitions each w/ an OS on it.  Not sure if I did something wrong there, but I'm pretty sure all three partitions each still have a workable OS on them.  Just not sure how to convince my booting up of that!

---

### Post by Partyboi2 on 2008-05-28
Did you restore grub after installing xp? You can restore grub with a ubuntu live cd, see [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by oldschoolrockstar on 2008-05-28
The problem is that you don't have a program to boot up the other Operating Systems you've installed on your PC. The very second you've tossed your Window's XP cd in your computer, and rebooted it. The CD had the enemy and terminated your grub loader. 

I had this problem when I accidentally erased the ms dash on my x-box, and I needed to hot swap my drives to recreate for my xbox. The Grub loader screwed up the whole process of the technique. A very risky Technique, but it's was effective once I figured out how to uninstall Grub Loader from my machine, then I had to reinstall the Grub loader. It worked like a charm.

Try using a partitioning program in xp to see/manage your hard drive's partitions. You should be able to see all of your Operating Systems. I use powerquest partition manager 8. You could even delete the partitions or resize them as well.

---

### Post by tigerplug on 2008-05-28
Like the others said you need a bootmanager like grub

---

### Post by housam on 2008-05-28
To be sure about the existance of the 3 OS and your partitions , please boot from ubuntu live CD and type in the terminal 
```
gksudo gedit /boot/grub/menu.lst
```
 and post the results

also take a screen shot ( applications >> accessories  >> screen shot ) to Gparted image ( sys. >> admin. >> partion editor )

---

### Post by LazyEngineer on 2008-05-28
Thanks for all the replys!

I booted from the Ubuntu live CD (8.04 - 64 bit).

Here is the screenshot.  Note that Ubuntu see's the 3 partitions in the "Places" tab, yet the Partition editor thinks my entire HDD is unallocated.  
[IMG]http://i31.tinypic.com/xbmut2.jpg[/IMG]

I followed the link to how to reinstall grub (thank you).  It didn't work though.  Here's a screenshot showing the final result.  
[IMG]http://i29.tinypic.com/j75n36.jpg[/IMG]

As requested, I opened terminal and typed: gksudo gedit /boot/grub/menu.lst
It opened an editor to a file, which was blank and empty.


One other item of strangeness - now when I restart, I see the following three options upon booting:
> 
Microsoft Windows XP Professional
Windows Recovery Console
Ubuntu

Default boot is still WinXP
When I select Ubuntu though, it's not right.  I think this is some kind of hold-over from the installer Live CD.  It launches the intial Ubuntu bootup spash screen, but then terminates in a black text screen with a (initramfs) prompt.

---

### Post by housam on 2008-05-28
from your post , you don't have a grub menu.(menu.lst is empty ) 
Gparted shows no partitions ?? strange !!!!
so, we have to get infos about the partitions , type in the terminal 
```
sudo fdisk -l
```
where -l is a small L and post the results please.

---

### Post by LazyEngineer on 2008-05-28
[IMG]http://i32.tinypic.com/2lm9ssz.jpg[/IMG]

---

### Post by housam on 2008-05-28
Your partition table shows that you have the following :
sda1 a primary partition for vista
sda2 an extended partition which has sda3 & sda5 for Ubuntu
sda4 a primary partition for win-xp

Now we have to make a grub menu that contain the 3 OS.
you'll fix vista boot loader using [[COLOR="Red"]_Easy BCD_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580903")
Then [[COLOR="Red"]_recover grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") after windows

---

### Post by LazyEngineer on 2008-05-28
Thank you for the assistance.  Insufficient understanding to comply with your first linked suggestion: ""Werd" solution to slow boot in Ubuntu 7.10".  Please expand.


> **housam said:**
> Your partition table shows that you have the following :
sda1 a primary partition for vista
sda2 an extended partition which has sda3 & sda5 for Ubuntu
sda4 a primary partition for win-xp

Now we have to make a grub menu that contain the 3 OS.
you'll fix vista boot loader using [[COLOR="Red"]_Easy BCD_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580903")
Then [[COLOR="Red"]_recover grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") after windows

---

### Post by housam on 2008-05-28
Sorry I gave you a wrong link , [[COLOR="Red"]_EasyBCD_[/COLOR]]("http://neosmart.net/dl.php?id=1")

---

### Post by jimv on 2008-05-28
Now that's what I call a screenshot!

---

### Post by spud42 on 2008-05-28
not trying to steal this thread but what would be the proper order to install to get this triple boot to work? i also wish to have all 3 due to some software requirements from work. if i install XP first then Ubuntu that should load grub correct? then add Vista as the third OS ? or Vista then Ubuntu ?

---

### Post by Pumalite on 2008-05-28
The order should be: XP, Vista and last Ubuntu. You will have to allocate space for Ubuntu with the Vista partitioner.

---

### Post by spud42 on 2008-05-28
thanks Pumalite. so what does this sequence end up with? vista boot loader or grub as the boot manager? also which OS would be the default?

---

### Post by LazyEngineer on 2008-05-28
> **housam said:**
> Your partition table shows that you have the following :
sda1 a primary partition for vista
sda2 an extended partition which has sda3 & sda5 for Ubuntu
sda4 a primary partition for win-xp

Now we have to make a grub menu that contain the 3 OS.
you'll fix vista boot loader using [[COLOR="Red"]_Easy BCD_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580903")
Then [[COLOR="Red"]_recover grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") after windows


More information needed.  I have installed Easy BCD into windows XP.  This act alone has not allowed me to boot into Ubuntu.  I've screwed around with the settings in Easy BCD.  This also has not allowed me to boot into Ubuntu.  

Suggestions?

---

### Post by Pumalite on 2008-05-28
> **spud42 said:**
> thanks Pumalite. so what does this sequence end up with? vista boot loader or grub as the boot manager? also which OS would be the default?

Yuo end up with Grub (the best boot loader around), Ubuntu is default for booting, but you have a menu where to choose. You can also change the default in Grub.

---

### Post by spud42 on 2008-05-28
i think he ment to recover Vista first with EasyBCD. then once Vista is back then recover Grub which should give you Ubuntu back....

---

### Post by LazyEngineer on 2008-05-28
> **spud42 said:**
> i think he ment to recover Vista first with EasyBCD. then once Vista is back then recover Grub which should give you Ubuntu back....

Do you have any suggestions on how to do that?  I'm unclear on what setting changes to make in EasyBCD to cause me to get Vista back.  Dispite making some seemingly logical changes in EasyBCD that I should have thought would get me to boot into Vista - I still can only boot into XP.

---

### Post by housam on 2008-05-29
> **LazyEngineer said:**
> More information needed.  I have installed Easy BCD into windows XP.  This act alone has not allowed me to boot into Ubuntu.  I've screwed around with the settings in Easy BCD.  This also has not allowed me to boot into Ubuntu.  

Suggestions?

[[COLOR="Red"]_Here_[/COLOR]]("http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista") is the instructions for recovering vista after installing xp.
After restoring vista bootloader and boot it safely , you will go to install grub ( as described in the link I gave to you )which will allow you to boot Ubuntu and the other systems.

---

### Post by meierfra. on 2008-05-29
You have a problem with you partition table. Gparted does not recognize any partitions.  Also "find /boot/grub/stage1" returns (hd0,5), which makes it /dev/sda6, but according to fdisk, Ubuntu is on /dev/sda5.  Maybe "testdisk" (see my signature)  can  fix you partition table.

---

### Post by LazyEngineer on 2008-05-29
> **housam said:**
> [[COLOR="Red"]_Here_[/COLOR]]("http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista") is the instructions for recovering vista after installing xp.
After restoring vista bootloader and boot it safely , you will go to install grub ( as described in the link I gave to you )which will allow you to boot Ubuntu and the other systems.

Thanks.  The quest continues.  Following those instructions and I get a crash of EasyBCD 1.72.  with the following details:
See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

> 
************** Exception Text **************
System.ArgumentOutOfRangeException: Index and count must refer to a location within the string.
Parameter name: count
   at System.String.Remove(Int32 startIndex, Int32 count)
   at ..(String , String )
   at ..(String )
   at ..(Object , EventArgs )
   at System.Windows.Forms.Control.OnClick(EventArgs e)
   at System.Windows.Forms.Button.OnClick(EventArgs e)
   at System.Windows.Forms.Button.OnMouseUp(MouseEventArgs mevent)
   at System.Windows.Forms.Control.WmMouseUp(Message& m, MouseButtons button, Int32 clicks)
   at System.Windows.Forms.Control.WndProc(Message& m)
   at System.Windows.Forms.ButtonBase.WndProc(Message& m)
   at System.Windows.Forms.Button.WndProc(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.OnMessage(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)


************** Loaded Assemblies **************
mscorlib
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll
----------------------------------------
EasyBCD
    Assembly Version: 1.7.2.7
    Win32 Version: 1.7.2.7
    CodeBase: file:///D:/Program%20Files/NeoSmart%20Technologies/EasyBCD/EasyBCD.exe
----------------------------------------
Microsoft.VisualBasic
    Assembly Version: 8.0.0.0
    Win32 Version: 8.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/Microsoft.VisualBasic/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualBasic.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------
System.Runtime.Remoting
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/System.Runtime.Remoting/2.0.0.0__b77a5c561934e089/System.Runtime.Remoting.dll
----------------------------------------
System.Configuration
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
----------------------------------------
System.Xml
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.832 (QFE.050727-8300)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
----------------------------------------
msfeeds
    Assembly Version: 1.0.0.0
    Win32 Version: 1.0.0.0
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/msfeeds/1.0.0.0__7df935e7b230192c/msfeeds.dll
----------------------------------------
Accessibility
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///D:/WINDOWS/assembly/GAC_MSIL/Accessibility/2.0.0.0__b03f5f7f11d50a3a/Accessibility.dll
----------------------------------------

************** JIT Debugging **************
To enable just-in-time (JIT) debugging, the .config file for this
application or computer (machine.config) must have the
jitDebugging value set in the system.windows.forms section.
The application must also be compiled with debugging
enabled.

For example:

<configuration>
    <system.windows.forms jitDebugging="true" />
</configuration>

When JIT debugging is enabled, any unhandled exception
will be sent to the JIT debugger registered on the computer
rather than be handled by this dialog box.




---

### Post by LazyEngineer on 2008-05-29
Ok, to recap, Only WinXP works, Win Vista and Ubuntu do not.  I tried using the EasyBCD.  This failed.  mostly it crashed on me when I followed the posted instructions.  So that's not so good.

I tried using the Testdisk - from within WinXP.  This too failed to actually do or fix anything.  It did find I have several partitions, but there wasn't a "Fix Vista not booting" option anywhere, so not sure what I'm supposed to do with this thing.  I tried playing with it some, but not much luck.

Somewhere along the line I CAN tell it to boot into VISTA, which fails - it gives me a text screen that says > 
Windows Failed to Start.  To Fix the Problem, 1. Insert your Windows Installation disk (blah blah blah)  

Which is cute, since no one actually gives you a Windows CD with your computer anymore.

Anyway, It then says below the above helpful tips:
> 
File: \Windows\system32\winload.exe
Status: 0xc000000f    
Info: The selected entry could not be loaded because the application is missing or corrupt.


So... well... damn.  I'm beginning to think it may be time to just wipe and start all over (not a fun thing to do, since Ubuntu and HP TX1000's are an absolute bear to get to play together well.)

---

### Post by stray77 on 2009-03-22
I'm guessing EasyBCD isn't working because you probably don't have .net framework installed or some other essential update.
If you have actually messed up the vista bootloader, it can be recovered by downloading the correct vista recovery disc from [[COLOR="Red"]_here_[/COLOR]]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") (you can get it from microsoft too but the torrent was faster for me).  Once you can boot into vista, use EasyBCD to add XP to the vista bootloader (if it's not already there). Finally, [_[COLOR="Red"]recover grub.[/COLOR]_]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

To recount, if you want XP, Vista or Windows7, and ubuntu, install them in that order. Vista see's XP's bootloader and incorporates it into Vista's bootloader so you can boot both XP and Vista, then when installing Ubuntu, grub recognizes the Vista bootloader and adds it as an option in the grub boot menu which becomes your final boot loader.

---

