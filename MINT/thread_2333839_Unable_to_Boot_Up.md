---
title: "Unable to Boot Up"
date: 2016-08-13
forum: MINT
---

### Post by rockdrumr on 2016-08-13
The first thing I get when attempting to boot up, is -


**GNU GRUB version 2.02~beta2-9ubuntu1.2 **


Then, in a window, it shows selections for -


***Linux Mint 17.2 MATE 32-bit**
**Advanced Options for Linux Mint 17.2 MATE 32-bit**
**Memory Test (memtest+)**
**Memory Test (memtest+, serial console 115200)**


Then, below the window -


**Use &#8593; & &#8595; keys to select...**
**Press enter to boot the selected OS, `e' to edit the commands before booting or `c' for a command line.**


In selecting *Linux... it runs through a process ending with -


**Busy Box v1.21.1 (ubuntu 1:1.21.0-1ubu8ntu1) built-in shell (ash)**
**Enter 'help' for a list of built-in commands**
**(intrumfs)_**


With `c' I get -


**GNU GRUB version 2.2~beta2-9ubuntu1.2 **

**Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. ESC...exits**


With `e' I get -


**set params**...


and, I am given several options


I downloaded the Boot-Repair to a USB Drive, but have not tried to use it yet.

[COLOR=#ff0000]**NOTE!!! I have edited this post for not having included sufficient information. Please ignore all posts to **[/COLOR][COLOR=#000000][FONT=Aladin]Moved to the "[/FONT][/COLOR][COLOR=#000000][FONT=Aladin]MINT[/FONT][/COLOR][COLOR=#000000][FONT=Aladin]" forum.
[/FONT][/COLOR]

Thank you for any help! :(

---

### Post by Bashing-om on 2016-08-13
rockdrumr; Hello;

What distribution and release is this ?
Is this a dual boot system ? Windows 10 ?
What has happened recently that led to this condition ? A new kernel install > or what ?

What can you boot to ? Can you boot to grub ? From grub what results when booting a recovery kernel ?

[INDENT][INDENT]gotta find a place to start
[/INDENT][/INDENT]

---

### Post by rockdrumr on 2016-08-14
I don't know anything about computers, nor operating systems, particularly Linux; but I'm pretty sure I have a [COLOR=#333333][FONT=Aladin]Linux Mint [/FONT][/COLOR][COLOR=#545454][FONT=Aladin]Debian, and Rafaela and [/FONT][/COLOR][Cinnamon (32-bit)]("https://www.linuxmint.com/edition.php?id=189") sounds familiar. I never, and I wish I had, installed a Windows OS, along with it. I can't remember what I could have done to cause it. I don't know what a "grub" is, and what I supplied above is what it boots to. That's it! Sorry! lol

How can I help you with music? &#9835;&#9834; lol

---

### Post by yancek on 2016-08-14
The failure to boot message doesn't usually occur unless there has been some software update that didn't function properly or a hardware problem.  So what was being asked in the previous post is what changes were made just prior to the error occurring?  Also, have you been using the system for some time successfully or is this a new install?

Use the installation medium you used to install your system and go to the site below and get the boot repair software and download it and run it.  When you run it, select the option to Create BootInfo Summary and  do not try to make any repairs.  Post a link to the output here as this will provide more details and someone might be able to help.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2016-08-14
> That's it! Sorry! lol

If that is it, then that is what you are stuck with.

Every computer operating system (OS) needs a boot loader. The usual boot loader for Linux is called Grub (GRand Unified Bootloader). If Linux is the only OS on the system the Grub boot menu is hidden as it is not necessary for us to see it.

If there is more than one OS on the machine then we usually see a Grub boot menu with options to load the different OS. Linux Mint is not actually Ubuntu but it makes use of make of the software provided by the Ubuntu developers and that may also include the Grub boot loader. So, if you can see a Grub boot menu you may also see as one of the boot options the label: Advanced Options for Ubuntu.

Advanced options for Ubuntu is a sub-menu that gives us extra options such as loading an earlier Linux kernel. And an earlier kernel might not have this problem. 

Another option in the Advanced options sub-menu is to load a Linux kernel with recovery mode and that will bring us to a menu with some options that may help you to fix this problem.

Regards.

---

### Post by rockdrumr on 2016-08-14
[I][B]_MY MISTAKE!!! Sorry!_ 

[/B][/I]The first thing I get when attempting to boot up, is -

**GNU GRUB version 2.02~beta2-9ubuntu1.2** 

Then, in a window, it shows selections for -

[B]*Linux Mint 17.2 MATE 32-bit
    Advanced Options for Linux Mint 17.2 MATE 32-bit
    Memory Test (memtest+)
    Memory Test (memtest+, serial console 115200[/B])

Then, below the window -

[B]Use &#8593; & &#8595; keys to select...
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command line.[/B]

I remember going to the options, but I don't speak Greek!

I downloaded the Boot-Repair to a USB Drive, but have not tried to use it yet.

---

### Post by howefield on 2016-08-14
Moved to the "*MINT*" forum.

---

### Post by yancek on 2016-09-08
Is this a new install Of Linux Mint?
Did it ever boot?  If yes, did you make any changes just prior to seeing this problem?
If no??
Is Mint the only operating system on the computer?
What happens when you select the Advanced options?

---

