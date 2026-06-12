---
title: "How to configure GRUB"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by Mic on 2005-07-11
In my quest for knowledge (my usual excuse) :-) , yesterday I installed UbuntuLinux into my pc. In order not to mess up the already working setup, I had set Ubuntu's grub to a floppy.

now i have:
hda1 - WinME
hda3 - SuSE
hbd6 - Ubuntu

wanted to add Ubuntu into the existing (installed when installing SUSE) Grub so that I can boot Ubuntu without using the floppy. went into the floppy's grub and copied the config, then copied this information into the existing grub.

after reboot, when i select this new option to boot, I get "kernel panic" and the system hangs. Try to mess with grub with after surfing for info but still can't get it working.

1. Any idea how i can add Ubuntu into the existing grub? 

2. I am new to linux and seems like SUSE is very much more easy to start with. In Ubuntu, I can only see Ubuntu and nothing else (no winME and SuSE partition), or is it that I mess up something unknowingly.

3. How can I share SUSE's home partition instead of using another home in Ubuntu.


Many thanks in advance for the advice.

---

### Post by trivialpackets on 2005-07-11
[QUOTE=Mic]In my quest for knowledge (my usual excuse) :-) , yesterday I installed UbuntuLinux into my pc. In order not to mess up the already working setup, I had set Ubuntu's grub to a floppy.

now i have:
hda1 - WinME
hda3 - SuSE
hbd6 - Ubuntu

wanted to add Ubuntu into the existing (installed when installing SUSE) Grub so that I can boot Ubuntu without using the floppy. went into the floppy's grub and copied the config, then copied this information into the existing grub.

after reboot, when i select this new option to boot, I get "kernel panic" and the system hangs. Try to mess with grub with after surfing for info but still can't get it working.

1. Any idea how i can add Ubuntu into the existing grub? 

2. I am new to linux and seems like SUSE is very much more easy to start with. In Ubuntu, I can only see Ubuntu and nothing else (no winME and SuSE partition), or is it that I mess up something unknowingly.

3. How can I share SUSE's home partition instead of using another home in Ubuntu.


Many thanks in advance for the advice.[/QUOTE]
 1.  I'm not at my system, but if you look at the /boot/grub/menu.list, then you should be able to see the format that the OS needs to be in.  Search in the forum, I'm sure you'll find an example of how it should look, then, if suse can see it, you'll be fine.  May need to add it to fstab to make suse see, as that's what you'll need to do for ubuntu to see the others.  See ubuntuguide.org under the windows section.
2.  See ubuntu guide reference above.
3.  I'll leave that to someone else.

---

### Post by Joeb on 2005-07-11
[QUOTE=Mic]In my quest for knowledge (my usual excuse) :-) , yesterday I installed UbuntuLinux into my pc. In order not to mess up the already working setup, I had set Ubuntu's grub to a floppy.

now i have:
hda1 - WinME
hda3 - SuSE
hbd6 - Ubuntu

wanted to add Ubuntu into the existing (installed when installing SUSE) Grub so that I can boot Ubuntu without using the floppy. went into the floppy's grub and copied the config, then copied this information into the existing grub.

after reboot, when i select this new option to boot, I get "kernel panic" and the system hangs. Try to mess with grub with after surfing for info but still can't get it working.

1. Any idea how i can add Ubuntu into the existing grub? 

2. I am new to linux and seems like SUSE is very much more easy to start with. In Ubuntu, I can only see Ubuntu and nothing else (no winME and SuSE partition), or is it that I mess up something unknowingly.

3. How can I share SUSE's home partition instead of using another home in Ubuntu.


Many thanks in advance for the advice.[/QUOTE]

1) you might post your menu.lst so we can see what is in it and try to help troubleshoot it.  For the record, mine looks like (for Ubuntu):
```

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda7 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

```

Of course, you would have a different value for the line beginning with root and your actual kernel might be a different version number.  Make sure that the lines beginning with root and kernel have the correct partitions listed (ie. don't use mine above).

2) If other OSs weren't added automatically, it's pretty easy to add them manually to the menu.lst.  Since you have a working menu.lst for Suse, you can just look at it for an example.

3) The answer to your third question depends.  When you set up Suse, did you make a separate home partition or is it included under the same partition Suse is set up on?  If it's the same, then you can't share it.  If it is a separate partition, then you just need to add something like the following to your /etc/fstab (in Ubuntu):
```

/dev/hda6       /home           reiserfs defaults        0       2

```

You would, of course, need to change the hda6 to whatever partition your /home is on and the reiserfs to whatever filesystem you used on your /home partition (or try auto if you aren't sure).

One word of caution, between sharing /home between different distros of Linux.  Since different distros use different versions of kde or gnome or applications, things might not work as expected, because the configuration files for your user ID are stored in your home directory and they may not be compatable between distros/versions.  It might be better to have a common area under home, where you put documents, downloads, pictures, mail, etc.  and then make separate user IDs for each distro.  Then in their respective home directories, you can make symbolic links to the common area.  Of course, you need to make the common area accessable to both ids.  You should only do this if you have a separate partition for home.  

If you are doing it with, say the Suse partition, so that you can access data while in Ubuntu, you need to remember that you can't reinstall or remove Suse because that will remove your data that is linked to your directory in Ubuntu.  A lot of experienced Linux users create a separate /home partition because it doesn't get deleted with each install of Linux (unless you tell the installer to use the entire disk or format the partition).


JoeB

---

### Post by mingus on 2005-07-11
*wanted to add Ubuntu into the existing (installed when installing SUSE) Grub so that I can boot Ubuntu without using the floppy. went into the floppy's grub and copied the config, then copied this information into the existing grub.*

I'm not sure I understand exactly what you did.  Can you still boot into SuSE?  (If you can't from grub but have the SuSE install CD, there is a menu option to boot from it that bypasses the boot loader).  The solution is easy, two alternatives.  Get into the YaST boot loader configuration and add a section that explicitly boots the Ubuntu kernel, just like the SuSE stanza does.  You can take the syntax from Ubuntu's /boot/grub/menu.lst file.  Or, install grub in Ubuntu to whichever partition /boot is on, get into YaST and have SuSE regenerate a menu.lst file for you; it will find Ubuntu and add it as a chain-loaded entry (like how W$ is done).  Personally, I prefer the latter (one of my boxes has a similar setup to yours).

*How can I share SUSE's home partition instead of using another home in Ubuntu.*

Hmm . . . IMO, a bad idea.  Some applications get installed to home, there are pointers and control files there, etc.  You don't want to mix that between 2 distros.  If you want to share data, create a separate partition just for that and mount it in both SuSE and Ubuntu's fstab.

---

### Post by Mic on 2005-07-12
Item 1. 
the grub config BY Ubuntulinux is as what Joeb had mentioned, I just made changes to the references to the different partition and drive when added to SuSE's grub config. Unfortunately, i gives kernel panic.

anyway, I'm still trying, googling, hope I'll get it right
all for the love of learning and the feel of banging my head against the wall  ](*,) 


Item 2. 
Reading the Unofficial Guide now and possibly will get the answer there :)


Item 3.
Gave up the idea after some consideration on your advice, thanks.

---

### Post by Mic on 2005-07-13
> 
title Ubuntu 5.04
    kernel (hd1,6)/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb7
    initrd (hd1,6)/boot/initrd.img-2.6.10-5-386


Finally, with the above I'm able to boot Ubuntu from SuSE's grub.

A big THANKs to all.

---

