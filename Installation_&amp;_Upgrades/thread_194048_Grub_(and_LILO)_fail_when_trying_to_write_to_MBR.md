---
title: "Grub (and LILO) fail when trying to write to MBR"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2006-06-10
I have been going through hell with this installation, I've been literally loading these files all day. I'm finally at the very last step of the installation, and I get the error that grub failed to run grub-install hd0 (not exact error). LILO gives a similar error.

I have the installer (alternative install/text based) running with ide=nodma as one of the options if that makes a difference.

What do I do?

If I 'finish' the installation w/o a boot loader, won't the system be unusable??

---

### Post by skelooth on 2006-06-10
I went and opened a console, and tried to run grub-install that way, and it's not on the command line.... could that be why it's failing??? (would it even be on the command line??)

---

### Post by skelooth on 2006-06-11
i give up for tonight... I spent all day on this and it's getting nowhere.

I burned a grub cd from the apt-get grub-disk package.... apparently this image does not have stage1 image on it, so it won't let you install grub on the hard drive....

so i go to a grub console... and it goes something like this:

> root (hd0, 1)
type is ext2fs blah blah
> kernel /vmlinuz
[says it's okay stuff]
>boot root=/dev/hda2
screen full of normal boot stuff then error please append valid root= to boot

:(

---

### Post by Herman on 2006-06-11
> I have been going through hell with this installation, I've been literally loading these files all day. I'm finally at the very last step of the installation, and I get the error that grub failed to run grub-install hd0 (not exact error). LILO gives a similar error.Hello, skelooth, you should check your BIOS settings for some kind of MBR protection option or antivirus in your BIOS that might be blocking your MBR from being written to by any program. That is to stop boot sector viruses for corrupting your MBR. You can turn that off temporarily until you install GRUB.
If you use the 'altenate' install CD, you can also have the option of installing either GRUB or Lilo to the first sector of your Ubuntu partition rather than to MBR. Then you can boot with [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") on a CD or floppy.
You can also install GRUB to a floppy with the 'alternate' install, and that would be okay too, if you can't install GRUB to MBR. Just make sure your BIOS is set to boot from a floppy before the install begins though.
For a web-site about the alternate install CD, [*click here*]("http://users.bigpond.net.au/hermanzone/").

[IMG]http://users.bigpond.net.au/hermanzone/p6/20fat32.gif[/IMG]
To get into the alternative boot options, when it offers to install GRUB to MBR, (you can try that again one more time), and if it still doesn't work choose either <Go Back> or <No>.

<No> Will give you options for where else you might like to install GRUB like to (fd0) or to /dev/hda1 or somewhere.

<Go Back> will place you in the 'Ubuntu Installer Main Menu' , where you can scroll down one line and choose "Install Lilo" instead. Then you'll get another screen offering you a choice as to where you would like to install Lilo.
If you install Lilo to your new Ubuntu partition (the first sector of it), you can boot with GAG Boot Manager for now. 
Then later when you do figure it out how to get GRUB on your MBR you'll have two ways to boot. GRUB can be on MBR, and Lilo on your first sector of your Ubuntu partition. They don't erase each other, and you can boot with either. That's what I do. 
I hope soemthing here will be some help, good luck, regards, Herman :D

---

### Post by skelooth on 2006-06-11
Actually herman I figured out what the 'real' problem was...

The installer was actually saying 'unable to install grub to /target/' ..... DOH

This samsung cd drive is going to be the death of me. Mom's gonna woop my butt when she gets back from vacation and finds out I fried her computer instead of making it better :)

---

