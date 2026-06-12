---
title: "Edubuntu 10.04 and RHEL dual boot"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by sindhughanti on 2011-05-16
Hi
I have a system with RHEL 5 installed on it.
I installed Edubuntu 10.04 LTSP side-by-side without installing the boot-loader.
Now I can detect Edubuntu thro RHEL, but have to make an entry for Edubuntu in the grub menu through RHEL. Kindly help me with this.
How do I do this? I need to know how i can find the kernel version number etc. Detailed help would be appreciated as i am new to this. Thanks :D

---

### Post by MAFoElffen on 2011-05-16
> **sindhughanti said:**
> Hi
I have a system with RHEL 5 installed on it.
I installed Edubuntu 10.04 LTSP side-by-side without installing the boot-loader.
Now I can detect Edubuntu thro RHEL, but have to make an entry for Edubuntu in the grub menu through RHEL. Kindly help me with this.
How do I do this? I need to know how i can find the kernel version number etc. Detailed help would be appreciated as i am new to this. Thanks :D
Problem you have at the moment is that you have 2 operating systems that  boot off of 2 separate versions of GNU Grub (Grub2 and Legacy)... and only have one of those  GNU Grub versions (Legacy) installed right?

Some older Operating system will load from Legacy Grub, but not from Grub2.  Some newer system will load from Grub2, but not from the older Legacy Grub. 

You can chainload from Legacy Grub to Grub2... and from Grub2 to Legacy-- But you HAVE to have both "Versions" loaded to do it.

Which ever version you keep as your primary/default  "Boot Loader" and chainload from is your personal chioce... But easiest at the point you are at, at this moment in time... Since you are going to have to Load Grub2 anyway... would be to install Grub2 and let it do everytihng "for you."

Doing it from Legacy as your primary boot loader means you are gong to have to: 
Install Grub2
Reinstall Legacy Grub (because the step before is going to overwrite the MBR)
Manually add the menu item with chainloader call to Legacy Grub to it's menu.lst.

Doing it from Grub2 as your primary/defualt boot loader means:
Installing Grub2
Configurating Grub2 (It shouldl find and add the chainload to rhel)

I'll continue this in another post, so this doesn't get too long and lose you in mass info.

Before I continue though... decide and tell me what "you" have decided as your default boot loader.

---

### Post by MAFoElffen on 2011-05-16
(bump)
What did you decide or do?  Haven't heard from you yet...

---

### Post by sindhughanti on 2011-05-17
Hi MAFoElffen,
right now my status is RHEL on my machine with Edubuntu. What i have decided is: I will
a) Install grub2
b)reinstall grub legacy
But i need a little light on installing grub 2 on legacy!

And sorry for the late reply!
Thank you so much for helping me out!!
Appreciate this a lot! and i am actually new to this! So sorry in advance if i seem out-of-this!

---

### Post by MAFoElffen on 2011-05-17
> **sindhughanti said:**
> Hi MAFoElffen,
right now my status is RHEL on my machine with Edubuntu. What i have decided is: I will
a) Install grub2
b)reinstall grub legacy
But i need a little light on installing grub 2 on legacy!

And sorry for the late reply!
Thank you so much for helping me out!!
Appreciate this a lot! and i am actually new to this! So sorry in advance if i seem out-of-this!NP.
Here is instructions for doing from LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

a sample menu.lst entrie would look like this:
```

[FONT=courier new]title        Ubuntu Linux BlahBlahL [/FONT]
[FONT=courier new][COLOR=Red]root        (hd0,8)[/COLOR][/FONT][COLOR=Red]
[/COLOR][FONT=courier new][COLOR=Red]kernel /boot/grub/core.img[/COLOR][/FONT][COLOR=Red]
[/COLOR] [FONT=courier new][COLOR=Red]boot[/COLOR][/FONT]

```But the test you are going to need to run first, is to drop down to Your Leagcy's CLI (Grub prompt) and see if it will "read" the ext4 partitions. Some versions of legacy can't read that filesystem... If not, then go Grub2-to-your Leagacy.

Manual test would be go to Leacy menu > hit "c" will drop you down to CLI > enter the commands above in red (changing to point to "your" install0 > see if it boots.

---

### Post by sindhughanti on 2011-05-20
> **MAFoElffen said:**
> NP.
Here is instructions for doing from LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

a sample menu.lst entrie would look like this:
```

[FONT=courier new]title        Ubuntu Linux BlahBlahL [/FONT]
[FONT=courier new][COLOR=Red]root        (hd0,8)[/COLOR][/FONT][COLOR=Red]
[/COLOR][FONT=courier new][COLOR=Red]kernel /boot/grub/core.img[/COLOR][/FONT][COLOR=Red]
[/COLOR] [FONT=courier new][COLOR=Red]boot[/COLOR][/FONT]

```But the test you are going to need to run first, is to drop down to Your Leagcy's CLI (Grub prompt) and see if it will "read" the ext4 partitions. Some versions of legacy can't read that filesystem... If not, then go Grub2-to-your Leagacy.

Manual test would be go to Leacy menu > hit "c" will drop you down to CLI > enter the commands above in red (changing to point to "your" install0 > see if it boots.
  Okay so let me tell you what i did:
1. Booted to RHEL
2. at the terminal, went to /boot/grub/grub.conf
3. in this file, i added the following 

title Edubuntu 8.04
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID="421dbea3-62ab-4da4-9f29-c330d286b3a0"  
initrd        /boot/initrd.img-2.6.24-19-generic

this file also had the entries of RHEL and Windows.

So i restart my machine and select Edubuntu which is now shown in the boot options menu. But then the followin error shows up

Error 15: file not found

So what do i do? how do i find the correct kernel path, initrd image file etc? also should i change grub.conf or menu.lst because i can see both
Thanks

---

