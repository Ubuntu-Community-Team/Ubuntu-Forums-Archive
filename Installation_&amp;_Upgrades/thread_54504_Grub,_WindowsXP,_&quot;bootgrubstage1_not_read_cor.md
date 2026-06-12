---
title: "Grub, WindowsXP, &quot;/boot/grub/stage1 not read correctly&quot;"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Asher on 2005-08-04
Oh boy...  I installed Ubuntu the other day on my ThinkPad T40 -- was overjoyed with how flawless everything was, my first for a Linux distro.  

I had to boot into Windows last night for the first time, so I chose the Windows entry in grub...only to find out it wouldn't boot anymore.  It would show the grub output (chainloader +1 or whatever, etc) then do nothing.

So I booted the Windows XP rescue console, typed fixboot.  Did nothing.  Typed "bootcfg /rebuild" to rebuild NTLDR, and nothing -- I get some error about not being able to see the filesystem as it may be corrupt.  This is odd, because I can traverse the filesystem using the rescue console...and it let me log into my windows install it found (C:\Windows).  It tells me to run chkdsk.  I do (chkdsk /R /p), but it doesn't fix anything.  Out of desperation, I try "fixmbr".

Now nothing boots.  "Whatever", I said, so I resigned to just reinstalling Windows first.  Boot with the Windows CD, it copies files to C:\Windows2, then says it needs to reboot to continue...only, it reboots and nothing will boot!  It won't even boot my Windows setup files.  

I can understand if you guys can't/won't help me with that, that's a Windows problem on an Ubuntu forums (though it must've been caused by Ubuntu somehow IMO). 

I then tried to recover ubuntu.  This is my real problem for you guys. 

I can boot from the DVD, I choose the rescue mode, it can see my filesystem fine.  All of my files are here.  Looking all over these forums and the internet, the solution is to type "grub-install /dev/hda".  I try this, and I'm told: "The file /boot/grub/stage1 not read correctly"  But this file exists (512 bytes) at the path it cannot read it from...

Similarly, when I try to do a "fdisk -l", I'm told "cannot open /proc/partitions".

Other instructions involved launching grub via "grub" and running commands: when I try this, it probes the devices to guess BIOS drives, then says: "Error opening terminal: bterm"

What I really want is for both Windows XP and Ubuntu 5.04 to boot.  Both filesystems LOOK to be intact but nothing wants to boot...and no methods to repair them are working.  Anyone have any ideas?

---

### Post by Hikaru79 on 2005-08-04
[QUOTE=Asher]What I really want is for both Windows XP and Ubuntu 5.04 to boot. Both filesystems LOOK to be intact but nothing wants to boot...and no methods to repair them are working. Anyone have any ideas?[/QUOTE]
I hate to say this, but you've messed things up to a very large extent. You should have come asking the second you had problems with your grub.conf booting the Windows partition.

As of right now, there's no choice really but to reformat and reinstall from scratch. Start with Windows, but it doesn't matter either way -- it is trivial to reinstall Grub overtop of Windows' boot loader.

I don't like to brag, but I'm a bit of an expert on Windows/Linux interoperability, having been forced to do it for all my friends and family that I've converted. So once you have your Windows installed, I can help you out from there. Get back to me here when you have a working Win32 installation :)

---

### Post by Asher on 2005-08-04
[QUOTE=Hikaru79]I hate to say this, but you've messed things up to a very large extent. You should have come asking the second you had problems with your grub.conf booting the Windows partition.

As of right now, there's no choice really but to reformat and reinstall from scratch. Start with Windows, but it doesn't matter either way -- it is trivial to reinstall Grub overtop of Windows' boot loader.

I don't like to brag, but I'm a bit of an expert on Windows/Linux interoperability, having been forced to do it for all my friends and family that I've converted. So once you have your Windows installed, I can help you out from there. Get back to me here when you have a working Win32 installation :)[/QUOTE]

Awesome.  I'm confused though, if the files are all in tact and can be accessed from each OS' respective rescue modes, why is a reformat required?  There's no way to repair?

---

### Post by Hikaru79 on 2005-08-04
[QUOTE=Asher]Awesome. I'm confused though, if the files are all in tact and can be accessed from each OS' respective rescue modes, why is a reformat required? There's no way to repair?[/QUOTE]
Oh, it's all good? You said you attempted to reinstall Windows, which usually requires you to first format your hard drive. Or you just installed it over top of an existing partition? Either way, this doesn't sound good. Was there any vital data that needs to be preserved? I always prefer to have a clean start when troubleshooting something where you're not quite sure exactly what was wrong and what you have already attempted to do to fix it.

If you really want to, though, we can try and go from where you're at.

---

### Post by Asher on 2005-08-04
[QUOTE=Hikaru79]Oh, it's all good? You said you attempted to reinstall Windows, which usually requires you to first format your hard drive. Or you just installed it over top of an existing partition? Either way, this doesn't sound good. Was there any vital data that needs to be preserved? I always prefer to have a clean start when troubleshooting something where you're not quite sure exactly what was wrong and what you have already attempted to do to fix it.

If you really want to, though, we can try and go from where you're at.[/QUOTE]
I reinstalled Windows without a format (I wanted to preserve the data).  I didn't even overwrite c:\Windows, but I tried to install it to C:\Windows2.  The install didn't finish because it failed to continue after the reboot.

I'm very fortunate in that the Windows partition on my ThinkPad was just imaged on there (I just upgraded an old 40GB HD to a 100GB HD, so I imaged the 40GB onto the 100GB then partitioned from there).  I still have my old 40GB HD with a complete duplicate of the Windows install, so if need be I can reinstall that one and image it again to the new drive to restart.

The problem was I spent about 10 hours customizing Ubuntu as well.  Not that big of a deal if I have to kill it all, but it'd still be a kick in the nuts and a few days work.

But from what I can tell using the Windows XP boot CD and the Ubuntu rescue DVD, the filesystems themselves are in tact.  I just can't get them to boot properly. :)

---

### Post by blasedeviant on 2006-11-28
I get the same error message, the only difference being that I'm not dual-booting.

---

### Post by blasedeviant on 2006-11-29
Has GRUB been updated from Ubuntu 5.04 to 6.10 to solve this problem?

---

### Post by gn2 on 2006-11-29
.

---

