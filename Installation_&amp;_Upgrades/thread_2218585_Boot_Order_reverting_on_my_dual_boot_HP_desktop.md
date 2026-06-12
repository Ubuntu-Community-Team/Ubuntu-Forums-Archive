---
title: "Boot Order reverting on my dual boot HP desktop"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by stephenesherman on 2014-04-21
I just set up a dual boot, Ubuntu 14.04 and Windows 8.1 on an HP Pavilion Desktop.

Works pretty well, but whenever I restart (or shut down) Windows, it puts Windows back up top in the Boot Order.

I can workaround, by going into BIOS after a Windows session, and moving Ubuntu back. Then I get the proper ubuntu screen offering my a choice of OS's.

Anyone else experience this behavior?

Would others consider this an acceptable workaround? Or would you look for a more permanent fix?

Boot info (from Boot Repair): [http://paste2.org/0mtpnmhW](http://paste2.org/0mtpnmhW)

---

### Post by oldfred on 2014-04-21
Windows seems to like to reset itself as first in boot order. Any maintenance or changes to Windows will reset it.

Some have had this work, but just letting Windows boot and adding grub to Windows.

       Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by ubfan1 on 2014-04-21
Or just use the function key to invoke the efi boot menu, and select ubuntu.  May avoid the "whose first" battle.

---

### Post by stephenesherman on 2014-04-21
oldfred,

**The bcdedit ... definitely had a good impact.** Windows freaked out, and started spewing error messages. :) But we know better. At the moment, Ubuntu is first in the Boot Order. And Windows doesn't not even appear in the BIOS Boot Order list; it is invoked by ubuntu. Not sure I like that, but okay for now.

Interesting learning for me. In the BIOS is showed things thus: "**Fast Boot -->Enable**" which I understood  to mean "Hit F10 to Enable Fast Boot." I.e. It is disabled at the moment.

Maybe not. Maybe that means "Fast Boot is ENABLED RIGHT NOW YOU MORON! Hit F10 to Disable."

So, last time thru the BIOS, I left Legacy Support, Secure Boot, and Fast Boot at "**--->Disable**" I guess that means they are all disabled. 

When I launched Windows from the Ubuntu start-up menu, it really had to chug and rethink and re-set stuff. I'll have to see if that behavior persists, or if was a one-time.

I also expect that after some future (Windows or Ubuntu) update, something in this boot/startup process will break. But I also expect it will be *figure-out-able*.

Thanks for all the help. I'll mark this thread solved after another day of banging around.

UPDATE: At the moment, Windows has once again taken over. :) .. Back to the BIOS!  Twice on shutdown, Windows gave a frowny face, cited an "Unexpected kernel mode trap" and forced a Restart (of course *"fixing things"* during restart.)

---

### Post by oldfred on 2014-04-21
Some have posted that using Windows 8 to dual boot, that it always fully shutsdown and reboots so that may be what is happening.

It seems like it is better to directly boot from UEFI to ubuntu if that is possible. Some elect to just use one time boot key to choose what to boot if that works.

---

### Post by stephenesherman on 2014-04-21
oldfred,

"*Some elect to just use one time boot key to choose what to boot if that works*."

If that means hit F10, enter** UEFI **(not "BIOS" as I originally wrote), and change stuff (after any Windows session), that's tolerable. I plan to use Ubuntu on a daily basis; Windows only occasionally. So if that's the least painful solution, so be it.

Thanks very much for you your prompt and frequent assistance.

---

### Post by oldfred on 2014-04-21
One time boot key should not take you into BIOS, but just show all boot options, similar to the UEFI/BIOS boot option.

On my system it is f12. I use that a lot as I have different versions of grub in each MBR of my several drives. Or when I want to boot flash drive. I tend to turn off os-prober so I do not have all versions in my grub menu.

And UEFI is somewhat similar in that every install is a separate boot folder in the efi partition and UEFI is supposed to let you boot any of them.

---

### Post by stephenesherman on 2014-04-24
Still researching this behavior, where Windows reverts. 

Ran efibootmgr (from within an active Ubuntu session) and got this interesting output:

[I]stephen@stephen-500-214:~$ sudo efibootmgr
BootCurrent: 0000
Timeout: 2 seconds
BootOrder: 0000,0001,0002,0008,0009,0005,0006
Boot0000* ubuntu
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0008* UEFI: Ipv4 Network Card 
Boot0009* UEFI: Ipv6 Network Card [/I]

There's no Windows Boot loader listed!

Someone suggested that (on successful Ubuntu boot/restart) the firmware removes the Windows bootloader, rather than just push it down the list. Note that it **is **possible to launch Windows from the Grub menu. 

But then, when Windows does it's shutdown error-checking, it flags the missing Windows boot loader as an issue, and "fixes" it.

So ... 1) Should efibootmgr list a Windows Boot Loader? 2) If so, how might I go about keeping it there

---

### Post by oldfred on 2014-04-24
It seems like you should have a Windows boot loader listed.

But I have never understood HP's efi partition. If you look at your pastebin, you will also see many HP .efi files in the standard efi boot partition. Many other vendors have the system .efi files in a separate partition.
Or why do not all the HP entries also appear in UEFI menu? Or is there another menu somewhere for HP repairs and Windows is in that?

---

