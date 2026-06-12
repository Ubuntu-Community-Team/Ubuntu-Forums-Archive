---
title: "install without grub"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by DKGert on 2006-12-09
Can anyone advice me how to install from liveCD without installing grub. The liveCD woudl like to install grub on hd0. I've already grub for starting RH-8 Debian Fedora and --SORRY-- MS. I dont like to overwrite my present grub.

---

### Post by bulldog on 2006-12-09
Don't think it's possible,but no worry,it will list all your OS's again.
You only have to point it to the right disk.[alternate install cd]

---

### Post by bscbrit on 2006-12-09
Copy your existing grub to somewhere safe, install ubuntu, restore your original grub, add the extra entry to enable ubuntu to boot.  Finished.

---

### Post by DKGert on 2006-12-10
**That was a no-good answer.**

I've a RH-8 on disk 1 to control my system ( /boot, /, /user, /home, /user/local )  and my other OS on disk 2.
The Ubuntu took over the grub install and removed my RH-8 form boot splash, which i did not like at all.
Staritng up the sysyen by my startdiskette for RH-8 and reinstalling grub with all mu OS's again the boot loader refused to load the new Ububntu.

 :( :( :( :( :(

---

### Post by bscbrit on 2006-12-10
OK. Please tell me exactly what you have installed and on which drive/partition.  Please show me a copy of /boot/grub/menu.lst or whichever grub file you are trying to use to control your system.

Does the recovered grub allow you to start RH-8 and your other OS?  Is it just Ubuntu that it will not start?

---

### Post by DKGert on 2006-12-10
It is just Ubuntu which cannot be started.
The boot loader starts but the kernel panics because it cannot load the filetype of ubuntu. cannot give you more presice info just now as i am installing on the machine concerned.
I'll post complete info later when i've reinstalled Ububtu once more.:cool: :cool: :cool: :cool:

---

### Post by louieb on 2006-12-10
[LIST]
[*]I have a PC that boots to half a dozen flavors of Linux including xUbuntu and Ubuntu.
[*]When installing a new distribution I go through the install screens until the install comes to the boot loader part. Then I quit the installation. In all the installs I have done on this machine, Linux has been install, but it can't be booted to just yet.
[*]Then its just a matter of adding the new Linux distribution to   the menu.lst (aka grub.conf) that appears when the machine boots.
[*]You need to know 3 things in order to add the entry.[LIST=1]
[*]drive and partition installed to
[*]kernel name
[*]initrd name (some distributions don't have one. But Ubuntu and RH do).[/LIST] [/LIST]T0 find the kernel and initrd names look in the /boot directory of the new distribution. 
Typical menu.lst entry for Linux. [COLOR=Blue]Stuff that normally changes.[/COLOR]
```

title        Ubuntu, kernel 2.6.15-27-386
root        (hd[COLOR=Blue]0,0[/COLOR])
kernel       /boot/vmlinuz-[COLOR=Blue]2.6.15-27-386[/COLOR] root=/dev/[COLOR=Blue]hda3[/COLOR] ro quiet splash vga=788
initrd         /boot/initrd.img-[COLOR=Blue]2.6.15-27-386[/COLOR]

```Hope this helps.

---

### Post by DKGert on 2006-12-10
I've tried to install Ubuntu once more.
This time I got in real problems.
The last time Ubuntu was installed upon a partition with Fedors 5.
Ubuntu makes it impossible to choose a new free partition to install and wants to have more partitions mounted than / and swap.
The automatic chooses the Fedora 5 partition for / and complains if changed " no root partition".
So I give up and stick to my Fedora.
Good luck with Ubuntu and by-by.
 ](*,)

---

### Post by DKGert on 2006-12-10
to louieb: I've RH-8,  Fedora 5 + 6, Debian 3.1 so far without problems on the same machine, only Ubuntu seems to make trouble.

---

### Post by bscbrit on 2006-12-10
Ubuntu DOES give you the opportunity to tell it where to install itself, it is just not on the same screen as the partition information.  The next page allows you to specify which partition is used for what purpose.

Sorry that you didn't stick with Ubuntu.  Just because its different from RH to install doesn't make it all bad :-D 

Nevermind, good luck with RH et al.

---

### Post by louieb on 2006-12-10
Sorry to see you give up on Ubuntu. Its installer is just a flexible  as any distribution I have tried. You may want to try the alternate CD It's installer for all that I can tell is the Debian installer.  
But what you said is interesting. You say Fedora,  Debian, and RH installers found the previous Linux install menu.lst and all they did was add themselves to it.   
I've install Debian and Fedora 5 before plus Vector, Zenwalk, Arch, Slackware, PClinuxOS, Puppy and DSL. And have never seen that as an option. Most just give the option of installing grub or quiting. A couple of them let me choose between grub and lilo.
Another thing I have experienced is most Linux installers can detect Windows and install the boot loader entry for it. But when it comes to detecting other Linux operating systems they fail miserably. 
Thats my experience and 2 cents worth.

---

