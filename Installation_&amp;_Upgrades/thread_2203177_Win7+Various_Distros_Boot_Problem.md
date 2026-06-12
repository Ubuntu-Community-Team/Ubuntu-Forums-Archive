---
title: "Win7+Various Distros Boot Problem"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by Lightning Dragon on 2014-02-02
Hello,

Because of the problem I was unsure if I should place this here or the  "Ubuntu, Linux and OS chat" section, or even someplace else. If I placed it wrong, please except my sincerest apologies. :(



So I upgraded my hardware and found that I can no longer dual boot! I was horrified! How could I live without my Ubuntu and Linux Mint? How could any new hardware justify this? I googled and googled and found out that I was, thankfully, wrong. Dual booting is still possible. However, I can't seem to get it to work. Let me explain what is happening, it might help some. Ahem, anyway!

After I upgraded my motherboard and CPU I reinstalled Windows 7 Professional first. Next, I popped in my other two HDDs. One, I needed more space for Windows and two, I wanted to boot into Ubuntu 12.04. However, one of the drives I intended to use for storage space only had SteamOS on it, so when I connected the drives thinking I'd boot safely into Windows 7 so that I could erase the HDD, I was given multiple problems. First, Windows would load anyways halfway and recovering drives (a black screen with a white loading bar) and once that was over, it would reset and boot into SteamOS and then SteamOS threw back all sorts of errors that went by in seconds. This forced  me to shutdown my computer manually and then unhook the drive with SteamOS on it. I thought, "Fine, no biggie!" and then booted into Windows to let it recover the files SteamOS (I'm guessing?) erased when it was accessed. Windows 7 is fine after this step. So then I think, "Okay, I guess I'll just go ahead and put in Ubuntu's drive and dual boot" but....I am meant with the same problems! The only difference is that it loads Ubuntu and Linux Mint absolutely fine after the same screen of Microsoft's black recovery seen ends--no errors, just a straight up boot after that. 

The only difference between my older board, is that the newer board has something called UEFI? I'm not entirely sure what that means, but I went into my BIOS to disable it and it "sorta" fixed the problem. Only, it wouldn't recover Windows (good sign) and instead just straight up boot into Ubuntu or Linux Mint (whichever drive I was testing). So, my question is...what is wrong? How can I make it so I have that selection screen again so I can pick which OS to get into? Is this option no longer available on new motherboards?

_**Motherboard:**_ MSI Z87-G55

Any help would be greatly appreciated, thank you!

LD~

_**P.S**_

So to clear up the post: all of my operating systems are installed on separate hard drives. I would like to be able to dual boot again and erase one of my extra hard drives clean for storage use--which is impossible if it breaks Windows every time I install another HDD.

---

### Post by tfrue on 2014-02-02
I would need to see your Boot-Info script before I could determine if you have a GPT/UEFI disk, or just a normal MBR/BIOS disk. I would suggest plugging in all your drives and boot from a cd and install boot-repair, go to this site and follow the instructions.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I would also say that you probably don't have grub installed on the first HDD that BIOS is looking to for booting. I believe once you install Grub, some problems will go away, but we may have to edit a boot file so grub will know to look on the other HDD for your Linux installations. 

The boot-info script will give us a plethora of options

---

### Post by Lightning Dragon on 2014-02-02
Hello,

I cannot get LiveCD to work for "Try Ubuntu". It gives me a blank screen. Would the boot-repair work if I used it through the actual installation of Ubuntu? If so, this is what occurred. I opened Boot-repair and it stated, "EFI Detected" and then I clicked the summary and waited. This is the URL it gave back; [http://paste.ubuntu.com/6864619](http://paste.ubuntu.com/6864619)

And as an update, the "loading" screen I mentioned for Windows is all black with a white loading bar stating "Loading Windows Files". This time it didn't go so fast so I could get the words. Also, I used a 32bit install for Ubuntu while I used 64bit install for Windows 7, if that matters.

EDIT 1

I reinstalled Ubuntu, new download, 64bit after I turned off Legacy+UEFI to just "UEFI" just in case. It has improved, a bit. Screen made really wonky color displays though during installation and first access to the OS. After installation and reboot, it automatically takes me to windows after Loading Files again. This time, however, it didn't reset the computer and boot straight into Ubuntu. It continued through to Windows 7. I restarted the computer and used my Boot Option to go directly into Ubuntu to run the Boot-Repair again. This is the new URL it generated;

[URL="http://paste.ubuntu.com/6865174/"]http://paste.ubuntu.com/6865174/

[/URL]After Ubuntu's updates and upgrades, I restarted and instead it took me to a smaller Ubuntu logo screen after a red line went through the screen. At this point, during loading, it reported "checking battery state" for several seconds before it booted me straight into Ubuntu.

EDIT 2

Boot-repair seemed to have done something on its own, unless I accidentally pressed something or my cat did when I wasn't looking. It says it updated and wanted me to change the BIOS boot order to; sda1/EFI/ubuntu/grubx64.efi file

However, I never made the changes. It also gave me a new url; [http://paste.ubuntu.com/6865222](http://paste.ubuntu.com/6865222)

A restart logged me into Windows very slowly and then I manually restarted. This time, though, I was greeted by a purple GRUB screen with my Ubuntu and Windows. Windows, however, had four different things to choose from. So I picked "Windows UEFI Loader" and it went into Windows, though very slowly.

So I guess now I need to fix the GRUB screen so there aren't so many Windows log ins or at least rename the right loader or move it up more, and then speed up the boot time.  Before the GRUB screen I am given three "Disk Read Errors!" and then after I select Ubuntu I am given a black screen that says, "More than 8 ouputs detected!" for several seconds, and then it boots up. 

However, I'd really like to know how to avoid this or to install future Ubuntu/Linux OSes on a UEFI/modern motherboard so that I don't  break anything or further slow my boot time up. 

Thanks!

---

### Post by oldfred on 2014-02-03
Your first link to BootInfo showed Windows in UEFI boot mode in sda and Ubuntu in BIOS boot mode in sdb.
Then your re-install did install Ubuntu in UEFI boot mode on sdb, with its own efi partition on sdb. You should not need to install grub2's efi boot files into the efi partition on sda. Your UEFI should find both drives and offer to boot Windows directly from efi on sda and offer to boot Ubuntu from sdb.

Grub with 12.04 does not create correct chain load entries to Windows from grub menu to efi.
       grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

You can manually add a boot stanza to 40_custom as shown in bug report, or use Boot-Repair. It used to do it automatically, but now has other changes, so not sure what else it might do.


 HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by Lightning Dragon on 2014-02-03
Hello,     

 In the bug report I don't see the instructions to manually add or even what that is. However, I did run boot-repair's recommended option and it states it was successful, however it wanted me to rename Windows EFI files because of buggy kernel. I said no because I wasn't sure what it would be doing and how it would effect my Windows install. Should I redo but accept?     

 As for the link on UEFI boot install and repair in your signature, there is a section that sounds like it is what I need. Which is "UEFI menu clean up (UEFI saves entries)". I would like to remove some of the unnecessary Windows boot options or to move the correct one above Ubuntu. Is this possible via this method? I was reading the link here, [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr),  on the options but I don't understand what a lot of the options actually do.

_**edit**_

Rerunning Boot-repair but saying "no" to the bug kernel fix again led me to have fewer Windows boot options. Now I only have two, is is better than five. I also tried changing it so it booted Windows first, but that didn't bring me the GRUB screen so I had to go into BIOS (not boot-repair as I couldn't get into Ubuntu) and changed the drive manually. I went back into boot-repair and reput Ubuntu as first.

So I guess deleting or changing these options any will not result in the way that I was hoping?

---

### Post by oldfred on 2014-02-03
Do not accept the 'buggy' UEFI option with Boot-Repair. 
That is for those systems that modify UEFI so a ubuntu entry will never work and only a Windows entry works. So it renames the Windows efi file to really be grub or shim to boot Ubuntu. But then you can only boot Windows from grub menu as its name is changed. And updates may confuse the issue. But for some it is the only way to boot Ubuntu.

Some of the better UEFI have tools like or are actually the efimanger built in. So you can add, delete or rename UEFI boot entries.

---

