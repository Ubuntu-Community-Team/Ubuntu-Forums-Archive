---
title: "A Little Dual Booting Trouble Vista and Ubuntu (EasyBCD)"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by ADZ on 2007-11-25
Hello, I treid following this guide:
[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)
to install linux and then vista. 

This is the situation:
I have 2 harddrive, a SCSI 250GB and an IDE 30GB. I had an Ubuntu installation on the 250GB one. I installed Vista to the 30GB one, and then used the livecd and did:
sudo grub
find /boot/grub/stage1 (got hd1,0)
root (hd1,0) 
setup (hd1,0)
After that, I rebooted, and it booted to the Vista Partition. I download EasyBCD. Then I did Add -> Linux and for Drive I put Drive 0 Partition 0 (the 250GB one). Now this is kinda wierd, why does grub call it 1 and easybcd 0? Anyways...I did add entry, save. and restarted. The Ubuntu choice was there, however when I select it, the screen just blinks and goes back to the screen where you select the os to boot. Then I restarted to Vista, and loaded EasyBCD again. It gave me this error message:
See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

************** Exception Text **************
System.InvalidOperationException: Cannot start process because a file name has not been provided.
   at System.Diagnostics.Process.Start()
   at ..()
   at ..()
   at ..()
   at ..(Object , EventArgs )
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
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll
----------------------------------------
EasyBCD
    Assembly Version: 1.7.1.6
    Win32 Version: 1.7.1.6
    CodeBase: file:///C:/Program%20Files/NeoSmart%20Technologies/EasyBCD/EasyBCD.exe
----------------------------------------
Microsoft.VisualBasic
    Assembly Version: 8.0.0.0
    Win32 Version: 8.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/Microsoft.VisualBasic/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualBasic.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------
System.Runtime.Remoting
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Runtime.Remoting/2.0.0.0__b77a5c561934e089/System.Runtime.Remoting.dll
----------------------------------------
System.Configuration
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
----------------------------------------
System.Xml
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.312 (rtmLHS.050727-3100)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
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

I am a little bit scared to do anything else because I have a few important files on the Ubuntu partition. Any ideas? Thanks...

---

### Post by funkyFlash on 2007-11-25
I'm afraid I'm not familiar with EasyBCD.  I never had to use it.  I looked at that guide, and I thought it seemed a bit silly.  What's the purpose of having the Vista boot loader load Ubuntu?

I currently dual boot Vista and Gutsy, and Grub always did the trick for me.  This is what my menu.lst looks like:
```

<more random crap above>
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=23a5ab12-6be1-452b-af67-871bc87becb3 ro vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-13-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=23a5ab12-6be1-452b-af67-871bc87becb3 ro vga=791
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
And then I let grub do the dirty work.  Once grub passes the proverbial booting torch to Vista, the  Vista boot loader takes off from there, and proceeds to happily eat up my RAM and flood my network with repeated "DOUSPEEKWINDOZ?" requests.

The tricky part was that grub was counting my drives differently at boot than it was in the ubuntu live environment.  That seems like it may be what's plaguing you as well.  When you get to the grub screen, enter command mode (push 'c') and type the find command again.  If you get something different than (hd1,0), than you may be in the same trouble as I.  You will have to change the device.map and menu.lst files accordingly.  Note, when changing the menu.lst file, you'll have to look for the single commented line ```
# groot=(hd0,1)
```. and change that.  Then you can run 'sudo update-grub' to fix your menu.lst file.

---

### Post by ADZ on 2007-11-25
> **funkyFlash said:**
> I'm afraid I'm not familiar with EasyBCD.  I never had to use it.  I looked at that guide, and I thought it seemed a bit silly.  What's the purpose of having the Vista boot loader load Ubuntu?

I currently dual boot Vista and Gutsy, and Grub always did the trick for me.  This is what my menu.lst looks like:
```

<more random crap above>
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=23a5ab12-6be1-452b-af67-871bc87becb3 ro vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-13-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=23a5ab12-6be1-452b-af67-871bc87becb3 ro vga=791
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
And then I let grub do the dirty work.  Once grub passes the proverbial booting torch to Vista, the  Vista boot loader takes off from there, and proceeds to happily eat up my RAM and flood my network with repeated "DOUSPEEKWINDOZ?" requests.

The tricky part was that grub was counting my drives differently at boot than it was in the ubuntu live environment.  That seems like it may be what's plaguing you as well.  When you get to the grub screen, enter command mode (push 'c') and type the find command again.  If you get something different than (hd1,0), than you may be in the same trouble as I.  You will have to change the device.map and menu.lst files accordingly.  Note, when changing the menu.lst file, you'll have to look for the single commented line ```
# groot=(hd0,1)
```. and change that.  Then you can run 'sudo update-grub' to fix your menu.lst file.

"Once grub passes the proverbial booting torch to Vista, the Vista boot loader takes off from there, and proceeds to happily eat up my RAM and flood my network with repeated "DOUSPEEKWINDOZ?" requests." <--------- LOL :lolflag: That's A nice way of putting it!

Anyways....I fixed it! Thanks! This is what I did:
[LIST=1]
[*]Boot off of liveCD
[*]Do sudo grub
[*]type root (hd1,0)
[*]do setup (hd0) to make grub the master boot record
[*]then I rebooted, got ubuntu back :) yay
[*]edited the menu.lst file for grub with your config (except I changed the harddrive)
[*]aaaand... It dual boots! yay
[/LIST]

Kinda weird....why didn't I think of just using grub. Stupid tutorial :(

---

