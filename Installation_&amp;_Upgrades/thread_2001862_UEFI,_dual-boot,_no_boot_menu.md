---
title: "UEFI, dual-boot, no boot menu"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by NoahsMyBro on 2012-06-11
I've seen several posts that appear similar to my situation, but none that seem similar enough for me to try and apply the responses to my own system. I apologize if I've overlooked the answer; I suspect it's already here somewhere.

This weekend I tried to build a new system dual-booting Win 7 & Ubuntu 12.04. I've already formatted and re-installed both OS'es 3 times, and don't want to have to do it again, so I've stopped trying to guess how to fix this, and I'm hoping somebody here can advise me how to proceed.

1) Booted the system off of the Windows 7 DVD, using the UEFI choice from the system.
2) Within the Win installer I created an approx. 400Gb partition on the hdd. Windows also created a couple of addl partitions - I don't recall the exact sizes, but I think one was 100Mb and the other 128Mb. I assume these are UEFI-related.
3) Following the advice here - [http://askubuntu.com/questions/91437/uefi-hardware-and-dual-booting-with-windows](http://askubuntu.com/questions/91437/uefi-hardware-and-dual-booting-with-windows) - I confirmed that Windows is using UEFI.
4) I created a system recovery DVD in Windows and backed the system up to my NAS. Hopefully I won't need to re-install Windows yet again.
5) I booted from the Ubuntu LiveCD, using the UEFI boot option from my system BIOS (wonder what to call that now?).
6) I selected to try before installing. Confirmed the /sys/firmware/efi/ directory existed.
7) Launched the installer. Chose 'Something else' and created a swap partition and used the remainder of the disk for / .
8) When I got to the selection of where to install the boot loader, I was stumped. I couldn't find anything online that seemed like a clear answer.

I wasn't sure what I should choose, but ultimately selected to install the boot loader to the EFI partition.

The Ubuntu install completed successfully.

At power-up the computer shows no boot menu at all. If left alone the system will load Ubuntu.

If I quickly hit the F12 key during POST the BIOS will display its own boot menu, from which I can choose Windows or Ubuntu.

Previously this weekend I've tried (and failed) to fix things using Boot-repair and EasyBCD.

*Warning: EasyBCD is not UEFI-compatible and WILL trash your boot structures on the disk. Afterward I was unable to repair Windows and ultimately gave up and reformatted.*

How can I add a boot menu ?

Thanks,
Steve

---

### Post by oldfred on 2012-06-11
I think with UEFI you are just supposed to use the UEFI menu.

Some have posted this, but I do not know if it works.

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

---

### Post by NoahsMyBro on 2012-06-11
Oldfred,

Thanks for the advice.

I'm afraid the threads you linked to went a little over my head though. Assuming I do absorb and comprehend those two threads, are they talking about:
[LIST=1]
[*]installing Grub (presumably from within Ubuntu)
[*]Configure Grub with entries for both Ubuntu & Windows
[*]Configure the motherboard to always launch the Ubuntu bootloader
[*]The Ubuntu bootloader will display the Grub menu, and from there the user can select either OS
[/LIST]

Is that the gist of those discussions?

"Just using the UEFI menu" sounds perfect, but I can't find a UEFI menu. Are you meaning I should just use a menu served up by the firmware on the motherboard?

I'd expect that to be an option, but within the motherboard setup I can find no option to have the motherboard display a boot menu. All I can find is a place to specify the boot order, but nowhere to have the mobo present the choice at boot-time.

If that wasn't what you meant, where else would I find a UEFI menu?

Thanks again for your time and explanations.

---

### Post by oldfred on 2012-06-11
I think the UEFI menu is your f8. I do not know if there is a way to make that a default or not. One or two users have posted screenshots of their UEFI menus, but I do not know enough about them to tell. And from BIOS can you set one as a default?

You have grub installed if you can boot Ubuntu and then you may be able to add the windows boot entry back to the efi partition into 40_custom.

Do you have a boot maintenance manager like the one user posted and what options does it have. Each vendor's implementation of UEFI is different.

---

### Post by hansdown on 2012-06-11
Hi NoahsMyBro.

Hope this helps.

I intended to triple boot linux mint, ubuntu 12.04, and solusos.

I started with mint, taking entire drive.

This worked well, and I found, that F12 was needed to get to the boot menu, otherwise it sat with a cursor, that gave no options.

I now had a mint boot option, and a UEFI boot option.

Both worked.

Next I installed 12.04 sise by side.

Had to update grub, to get 12.04 to show up.

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I still need to hit F12, but it's not enough of a problem, that I've gone any further.

---

### Post by YannBuntu on 2012-06-12
Hello
> **NoahsMyBro said:**
> Previously this weekend I've tried (and failed) to fix things using Boot-repair

What was the resulting BootInfo URL please?
and please could you indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1")? (it won't change your boot)

---

### Post by NoahsMyBro on 2012-06-12
> **YannBuntu said:**
> Hello


What was the resulting BootInfo URL please?
and please could you indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1")? (it won't change your boot)

I'm sorry, but the install environment that I used boot-repair in is long-gone, along with whatever the Boot URL results were.

On the current sytem, I get this:
[http://paste.ubuntu.com/1038266/](http://paste.ubuntu.com/1038266/)

-- Steve

---

### Post by NoahsMyBro on 2012-06-12
<off-topic>
PS: WOW! The Boot-Info report is great! And having the integrated, automatic uploading of the result to the pastebin page is doubly cool!

---

### Post by YannBuntu on 2012-06-13
Hi

> **NoahsMyBro said:**
> 
On the current sytem, I get this:
[http://paste.ubuntu.com/1038266/](http://paste.ubuntu.com/1038266/)

-- Steve

Your EFI seem correctly configured: Ubuntu and Windows EFI files are in your EFI partition, and your session is EFI mode. Now what you need is to find a way to setup your BIOS so that it boots on the /efi/ubuntu/grubx64.efi file. For this i can't say better than Oldfred.
If you can't find it please show us pictures (taken with camera) of your BIOS.

---

### Post by NoahsMyBro on 2012-06-14
I didn't find anything in the BIOS that looked like a setting to display a boot menu from the BIOS itself.

Because I'm not sure exactly which BIOS pages would be helpful, I took several photos of the various pages, and have made them all available here:

[https://skydrive.live.com/redir?resid=1E280F753A283066!1232](https://skydrive.live.com/redir?resid=1E280F753A283066!1232)

And here (if anyone has a problem with skydrive):

[http://www.flickr.com/photos/61383932@N00/sets/72157630131050448/](http://www.flickr.com/photos/61383932@N00/sets/72157630131050448/)

Thanks,
Steve

---

### Post by YannBuntu on 2012-06-15
Hi Steve

Did you manually create the "Ubuntu" and "Windows boot loader" entries, or did they appear automatically?

If you set the "Windows boot loader" entry in "Boot option #1" then reboot, can you access Windows?

---

### Post by NoahsMyBro on 2012-06-15
Those labels were created automatically; I did not set those.

And yes, if I configure the BIOS to boot from the choice labeled "Windows boot manager" then the computer will load Windows.

I can also hit F12 at boot, and the boot choices will then be displayed on-screen, and I can choose then which option to load.

I just can't find way to have the choices display automatically.

---

### Post by YannBuntu on 2012-06-15
ok. Everything seems ok, sorry I have no idea to fix this in a clean way.

If nobody has better idea, i would try either:
- to add an Ubuntu entry in the Windows bootloader (eg via EasyBCD or BCDedit, but i don't know if they are ok with EFI).
- OR via gParted to format the entire disk in standard MS-Dos (not GPT) partitioning, they reinstall Windows, then reinstall Ubuntu.

---

### Post by martinr on 2012-06-16
Might [this]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957") help?

---

### Post by NoahsMyBro on 2012-06-16
Thanks for your efforts Yann.

Martin, thanks also for your suggestion, but for now I'm inclined to keep beating at the current config and see if I can make it work using UEFI. The idea of abandoning the ~25 year old BIOS and moving into the more modern platform appeals to me. I just hope I can get it to work.

:)

-- Steve

---

### Post by hansdown on 2012-06-17
Hi NoahsMyBro.

This thread has solved the problem.

[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

In my case, the live usb shows up in the UEFI partition, and an entry for the lexar by itself.

If I boot from the UEFI entry, it makes that partition mounted, and will not work.

Booting from the other entry mounts the usb drive, and works well.

---

### Post by Oubountourette on 2013-01-06
> **NoahsMyBro said:**
> *Warning: EasyBCD is not UEFI-compatible and WILL trash your boot structures on the disk. Afterward I was unable to repair Windows and ultimately gave up and reformatted.*
 
How can I add a boot menu ?
 
You *can* use EasyBCD. Use the newest Version, from Version 2.2< it is ready for Windows 8, Grub2 and EFI machines.

---

### Post by YannBuntu on 2013-01-06
> **Oubountourette said:**
> You *can* use EasyBCD. Use the newest Version, from Version 2.2< it is ready for Windows 8, Grub2 and EFI machines.

Any reference about this please? (Windows8 is not mentioned in [their documentation]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home"))

---

### Post by darkomano on 2013-02-16
Is it really true that EasyBCD 2.2 is EFI/UEFI aware ?
 
I don't think so.
 
Moreover 
1. EasyBCD is violating Microsoft Copyright by disguising ntldr as easyldr.
2. EasyBCD is violating Grub4dos Copyright by disguising grub4dos as neogrub.
 
What people are developing EasyBCD ? 
Are they stupid or just crooks stealing foreign work ?
 
Copyright is not just a word. 
Copyright violation is a criminal act and legal consequences can follow.

---

### Post by darkomano on 2013-03-26
No complains that EasyBCD is violating copyright law ?
Silent agreement ?

---

### Post by oldfred on 2013-03-27
Thread Closed.

If you want info on EasyBCD please use their forums. 
       [http://neosmart.net/blog/](http://neosmart.net/blog/)

---

