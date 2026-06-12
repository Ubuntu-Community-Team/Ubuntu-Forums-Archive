---
title: "WinXP + Win7 + Ubuntu boot?"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by silverspoon on 2010-01-03
OK, so when i bought my PC it had WinXP and Win7 (trial) installed by default. It's a shared PC, so I can't get rid of them.
Now at startup &quot;Windows Boot Manager&quot; appears and lets you choose the OS. Can I install Ubuntu and add it to the list, or should i add WinXP and Win7 to GRUB and remove &quot;Windows Boot Manager&quot;? And how?

---

### Post by Herman on 2010-01-03
When you install Ubuntu it will automatically install the GNU GRUB 2 boot manager and loader for you in the MBR of your first hard disk.
The GNU GRUB 2 boot loader boots Ubuntu, and also performs the role of boot manager to pass the boot of Windows over to whatever you normally use to boot Windows with.
You will then have the choice of which Windows you want to boot, the same as you have always done.

In 99.9% of cases, if you have a fairly normal computer everything will go without a hitch.
There's a small chance something could go wrong though, so you should make a backup of all your files first.
You should also have on hand some kind of boot disk just in case you do have some boot loader issue at first. 
It's rare for anything to go wrong if you only have one or two hard disks.

---

### Post by silverspoon on 2010-01-03
So when i install ubuntu, grub adds, say, &quot;ubuntu&quot; and &quot;other&quot; options and if i click &quot;other&quot; im taken to Windows boot manager?

---

### Post by Herman on 2010-01-03
> So when i install ubuntu, grub adds, say, "ubuntu" and "other" options and if i click "other" im taken to Windows boot manager? 	
You'll have a line with a title for Ubuntu,
another line for Ubuntu's Recovery Mode
one or two lines for the memory diagnostic tool,
and a line that will say something like 'Windows Vista', probably.

There will be a white selection bar and you can move it up or down with your arrow keys and press enter to boot the selected operating system.

If you selected Ubuntu, GRUB will boot Ubuntu,
if you selected Windows, GRUB will boot the Windows boot loader,
the Windows boot loader will come up and you'll see the same screen you're probably used to with the choice of whatever the Windows boot loader had in it already.

---

### Post by silverspoon on 2010-01-03
Can I get rid of Windows Boot Manager, add WinXP and Win7 to GRUB list, and set XP to boot by default and how? (just 'yes' won't help)

---

### Post by silverspoon on 2010-01-03
Also I would like to say when I ran Partitioner from Jaunty live cd, both my HD were shown as 'unallocated', which is not true

---

### Post by Herman on 2010-01-03
> Can I get rid of Windows Boot Manager, add WinXP and Win7 to GRUB list, and set XP to boot by default and how? (just 'yes' won't help)No, you can't uninstall the boot manager for Windows because GRUB doesn't boot Windows. GRUB's responsibility is only to chainload the Windows loader at a boot sector, (the first sector of a partition). After that it's up to the Windows boot loader to load Windows.
> Also I would like to say when I ran Partitioner from Jaunty live cd, both my HD were shown as 'unallocated', which is not trueAre you sure? That doesn't sound right to me. I wouldn't advise anyone to proceed with an installation if that's the case until further investigations are carried out.

---

### Post by silverspoon on 2010-01-05
> **Herman said:**
> No, you can't uninstall the boot manager for Windows because GRUB doesn't boot Windows. 

I dont know what you mean by this. I once had XP and Ubuntu dualboot on my old PC. You could choose XP from GRUB. Though I had to manually edit the grub config file from Ubuntu.


> Are you sure?I think you know what I'm going to say...

---

### Post by DemonCat1992 on 2010-01-05
[COLOR=Blue][SIZE=2][FONT=Tahoma]I can see what you are going through and I also had the same problem, it was a little different but still similar. I would like you to go talk to Djsroknrol, I am not sure if you have heard of him, but he fixed this problem up in a jiffy for me. 


:biggrin: It's nice having someone so computer smart in the family...
[/FONT][/SIZE][/COLOR]

---

### Post by silverspoon on 2010-01-05
Why dont you like point me to your thread instead?

---

### Post by presence1960 on 2010-01-05
> **silverspoon said:**
> I dont know what you mean by this. I once had XP and Ubuntu dualboot on my old PC. You could choose XP from GRUB. Though I had to manually edit the grub config file from Ubuntu.

Yes but GRUB did not actually boot windows in that scenario. When the GRUB menu came up at boot and you selected windows- at that instant GRUB pointed or looked to the windows boot files. It transferred booting windows to the windows boot files which then proceeded to initiate the boot process for windows. If your windows boot files are gone GRUB will not be able to get windows to boot because it never does so in the first place. it just points to the windows boot files and that is what boots windows.

I suggest you go to Herman's site- there is a lot of great info there about booting.

---

### Post by silverspoon on 2010-01-05
Hm? But I didn't have 'Windows boot manager' back then. Are you sure removing that program will remove 'the windows boot files' as well?

---

### Post by Herman on 2010-01-05
As far as I know, GRUB does not care about trying to boot a Windows kernel directly like it does for most operating systems.

The way everybody has been booting from GRUB to Windows is by a process called 'chain loading', which means GRUB points to a MBR or a boot sector which in turn contains the code or directions if you like, to start the Windows loader. Then the Windows loader loads the Windows kernel and does whatever other jobs are necessary to start Windows booting up. It's something like a relay race, GRUB 'passes the batten', (or the boot), to some other loader that the boot sector code points to.

GRUB can chainload the MBR of a disk, or the boot sector of a partition if it contains code pointing to some boot loader.
The other boot loader can be another GRUB, or it can be LiLo, GAG Boot Manager or PLOP Boot Manager, or any other boot agent, as long as there's something there to take over the job of booting up whatever other operating system it is that owns the boot sector.
If the boot sector is empty, GRUB will most times return an error message.

In the case of Windows 95 or Windows 98, GRUB would chainload the boot sector which would activate files called IO.SYS, MSDOS.SYS and COMMAND.COM, which would then take over the task of booting Windows up. GRUB doesn't care what files the boot sector points to inside the other operating system, it's job is only to find the boot sector. If you go and delete those files you can't boot Windows 95 or 98. 

Windows XP had different boot loader files than Windows 95 and 98, it had NTLDR, NTdetect.com and boot.ini to start with, and I don't know what those do after that, \system32\hal.dll is a file that comes up in some of the error messages, autocheck is another. Without NTLDR, NTdetect.com and boot.ini it's impossible to boot Windows XP.

Windows Vista and Windows 7 boot files include bootmgr, BCD and winload.exe, and without those files your Windows Vista or Windows 7 systems won't boot.

Well, most people wouldn't be able to. 
If you can do it you'll be the first person I have ever heard of who can do that. :)

---

### Post by silverspoon on 2010-01-05
Uhh, you are basically saying the same thing with more details. Ill try again...

 Are you sure removing that Windows Boot Manager program will remove 'the windows boot files' as well?

---

### Post by Herman on 2010-01-05
> Are you sure removing that Windows Boot Manager program will remove 'the windows boot files' as well?
No,I'm not sure, it depends on how you go about removing it.
Are you just planning on deleting the Windows boot manager yourself or is there a way of uninstalling the Windows boot Manger? (I doubt it). 
If you delete it yourself then only what you delete will be deleted, (of course).

What do you want to delete the Windows Boot manager for though?
If you do, you won't be able to boot Windows anymore.

---

### Post by silverspoon on 2010-01-06
> **Herman said:**
> 
What do you want to delete the Windows Boot manager for though?
If you do, you won't be able to boot Windows anymore.
I want to delete it to not go to another bootloader (Windows boot manager)  from GRUB (doing that everytime i start the PC can get annoying).
I want to be able to select Ubuntu, Windows7 and XP from GRUB (like i did once with XP and Ubuntu, when i didnt have &quot;Windows Boot Manager&quot;(which i think came with Win7))

[U][I]Simple as that - I want to make a tripleboot of WinXP, Win7 and Ubuntu with GRUB
[/I][/U]

---

### Post by Herman on 2010-01-06
I would warn anyone not to do that if they want their Windows to boot.
GRUB does not boot Windows, it only chainloads a Windows boot loader.

---

### Post by presence1960 on 2010-01-06
> **Herman said:**
> I would warn anyone not to do that if they want their Windows to boot.
GRUB does not boot Windows, it only chainloads a Windows boot loader.

Let him go ahead and delete it. Then he can report back the results of trying to get windows to boot. I can't wait for this one!

---

### Post by silverspoon on 2010-01-06
wtf?

---

### Post by presence1960 on 2010-01-06
> **silverspoon said:**
> wtf?

Both Herman & I have explained this to you in detail but you want to stand steadfast in your belief. So go ahead and do it & report back. I am always up to learning new things!

---

### Post by silverspoon on 2010-01-06
Well you just wanted to help but you ended up being sarcastic to me( forget it). So i think it would be better if you wont reply anymoe (not intended to sound rude).
> GRUB does not boot Windows, it only chainloads a Windows boot loader.Yes but is the Windows Boot Manager the 'bootloader', or does it send you to WinXP, Win7 bootloaders/boot files instead? Because then i could like link GRUB to those files instead... Like i said once i didnt have that Windows Boot Manager so it makes me wonder
(dont want dont reply )

---

### Post by Herman on 2010-01-06
When you install Windows 7 it takes over your computer and occupies your Windows XP installation with its boot manager, turning Windows XP into the /boot partition for Windows 7, and making Windows 7 dependant on Windows XP for booting. 
That means if your Windows XP gets a virus you'll lose both operating systems instead of just one, and you can't delete Windows XP and install anything else there or you'll never be able to boot Windows 7 again, (unless you saved the boot loader and its files).

You might be able to copy the Windows 7 boot manager back into Windows 7 where it belongs and get XP booting with its own boot loader, NTLDR again.
That would mean you can chainload either operating system from GRUB and you can probably set things up so you won't see any Windows boot menus.

It would be possible to do that, but the time you would put into it, especially if you don't already know what to do, will add up to much more than the little extra trouble of having to press a button or two on your keyboard when you need to boot a Windows installation. It's probably not worth the effort.
It would be better to keep on learning how to use Ubuntu so you won't care about booting Windows anymore, than you really can delete the whole thing if you want. :D

I don't think presence1960 really meant to be sarcastic, but we're not sure if you're being sarcastic too, because what you were asking is a bit unusual. I wasn't sure if you're an expert and you're going to show us a new trick or somebody here to cause trouble or what. :D

We don't mind helping you if you're just trying to learn.

---

### Post by presence1960 on 2010-01-06
> **silverspoon said:**
> Well you just wanted to help but you ended up being sarcastic to me( forget it). So i think it would be better if you wont reply anymoe (not intended to sound rude).
Yes but is the Windows Boot Manager the 'bootloader', or does it send you to WinXP, Win7 bootloaders/boot files instead? Because then i could like link GRUB to those files instead... Like i said once i didnt have that Windows Boot Manager so it makes me wonder
(dont want dont reply )

That is fine by me after all I am not paid support. I can use my time to help someone else. Hope you get it sorted out anyway.

This my quote: > Both Herman & I have explained this to you in detail but you want to stand steadfast in your belief. So go ahead and do it & report back. I am always up to learning new things!

I am always up to learning new things. Herman, meierfra, merlinus, raymondh & caljohnsmith along with a host of others have helped me learn new things and advance my limited knowledge. For that I am thankful. I was not being sarcastic. Anyone can learn from someone else.

---

