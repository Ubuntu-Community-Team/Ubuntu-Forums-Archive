---
title: "Dual Boot - NOT your typical question"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by threadhead on 2007-01-03
**Problem:**
[INDENT]Need to be able to change the boot OS _without seeing the boot loader_. This is a **headless server** so I can not set/choose the OS during a reboot.[/INDENT]

**Setup:**
[INDENT]XP is installed on hd1 (ntfs), another drive for XP on hd0 (ntfs), installed Ubuntu Desktop on hd2,0, and Ubuntu Server on hd2,2, Swap drive on hd2,1. Everything works very well. I just installed Ubuntu Server to play with, BTW.

I'm a bit new to Linux installs, so I just followed the prompts and accepted the defaults for most things. So I'm pretty sure that Grub installed it's loader on hd0 in the MBR, whick is not the XP system drive, just an internal backup drive.[/INDENT]

**In Ubuntu, Reboot into XP:**
[INDENT]Fairly easy, I can edit the menu.lst and change the 'default' to the XP title, do a restart, and after a few seconds it reboots into XP.[/INDENT]

**[COLOR="DarkRed"]In XP, Reboot into Ubuntu:[/COLOR]**
[INDENT]I'm stumped here. There is no Grub client to be able to change the 'default' number from XP, and I can not see the menu.lst to be able to edit it (unless it's hidden somewhere, I don't know how to find it).[/INDENT]

Any ideas?
Karl

---

### Post by raul_ on 2007-01-03
Mount the ext3 drive in XP (use the fs-drivers) and change menu.lst from there ;) i don't use XP so i really can't help you with permission problems, i.e, being able to access linux system files, since you can't do "sudo" in XP. But i'm sure that's in another thread =) [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by tagra123 on 2007-01-04
Might be a dub question, but why are you booting into xp ? Maintenance? etc?  

Maybe theres a way to fill the need without booting XP?

---

### Post by tagra123 on 2007-01-04
Heres an idea
In the menu.lst
Copy Your default Ubuntu that you boot into above the automagic section

Next copy the XP section  just below the Ubuntu you just copied, but still above the automagic section. By keeping the entries above the automagic section the only way they will get changed is if you change them/ You will now have duplicate entries, but Ubuntu will always be 0 and XP will always be 1

Set the default boot to item 0 -- Its near the top of the menu.lst

This is so it will always reboot into ubuntu unless you tell it differently.

Now when you are ssh'ing into ubuntu and want to reboot into XP you can issue the command

grub-reboot 1

and XP should reboot.

I just discovered this command

Take a look here:

[http://www.cyberciti.biz/tips/force-grub-to-reboots-into-the-specified-os.html](http://www.cyberciti.biz/tips/force-grub-to-reboots-into-the-specified-os.html)

---

### Post by raul_ on 2007-01-04
> **tagra123 said:**
> Heres an idea
In the menu.lst
Copy Your default Ubuntu that you boot into above the automagic section

Next copy the XP section  just below the Ubuntu you just copied.  You will now have duplicate entries, but Ubuntu will always be 0 and XP will always be 1

Set the default boot to item 0 -- Its near the top of the menu.lst

This is so it will always reboot into ubuntu unless you tell it differently.

Now when you are ssh'ing into ubuntu and reboot into XP you can issue the command

grub-reboot 1

and XP should reboot.

I just discovered this command

Take a look here:

[http://www.cyberciti.biz/tips/force-grub-to-reboots-into-the-specified-os.html](http://www.cyberciti.biz/tips/force-grub-to-reboots-into-the-specified-os.html)

This seems the best option to me :)

---

### Post by tagra123 on 2007-01-04
Followup and let us know how it works for you.

---

### Post by threadhead on 2007-01-04
> **raul_ said:**
> Mount the ext3 drive in XP (use the fs-drivers) and change menu.lst from there[http://www.fs-driver.org/]("http://www.fs-driver.org/")

This does work. I mounted the ext3 drives and it was simple to change the menu.lst. Good idea!

---

### Post by threadhead on 2007-01-04
@tagra123:
Your idea is brilliant. But if Ubuntu was set as the default, and I 'grub-reboot 1' to get back to XP and there was a power outage (aka my 3yo unplugs the cord again) it would reboot back into Ubuntu. I need it to 'stay' on an OS until I make a change again.

I did test it and it does work!

And your question was not dumb, I still need to run a VB app that controls lighting, thermostats, etc. in the house. I don't think it will run under Wine, but I will give it a try. Also, I have a couple of XP apps I have to use for business, but I'll work on replacing those too (might run under a VM).

Thanks, you guys really came through.

---

### Post by tagra123 on 2007-01-04
Between wine and VMware I freed the harddrive of Windows.

If I can't get it to work in wine and need the Windows App -- VMWare to the rescue.

I like the idea of windows being contained in a virtual machine.  Easy to make backups too.

---

### Post by tagra123 on 2007-01-04
> **threadhead said:**
> @tagra123:
Your idea is brilliant. But if Ubuntu was set as the default, and I 'grub-reboot 1' to get back to XP and there was a power outage (aka my 3yo unplugs the cord again) it would reboot back into Ubuntu. I need it to 'stay' on an OS until I make a change again.

I did test it and it does work!

And your question was not dumb, I still need to run a VB app that controls lighting, thermostats, etc. in the house. I don't think it will run under Wine, but I will give it a try. Also, I have a couple of XP apps I have to use for business, but I'll work on replacing those too (might run under a VM).

Thanks, you guys really came through.


Well heres a way around the power outage problem.

Add another user to your machine -- Lets call it winreboot

Once that is done

Go to

System-Preferences-Sessions

Select the Startup Programs Tab

Click on add

and enter the following

shutdown -a -t 3600 -r now

Also add the windows grubbootwindows.sh

See this site  [http://robotics.caltech.edu/~klk/linux.html](http://robotics.caltech.edu/~klk/linux.html)


of course you'll ave to add /etc/shutdown.all

[http://doc.gwos.org/index.php/NonRootShutdown](http://doc.gwos.org/index.php/NonRootShutdown)



Then you could

System-Administration-Login Window

and tell the computer to automatically login winreboot


Here's what should happen happen

Power fails
  Ubuntu boots and logs in winreboot
     3600 seconds expire
        shutdown/reboot command is issued
        boot to windows once script is called
           computer boots windows

I would also add a cancel reboot script for normal logins that I would have to manually enter.  It would undo the the reboot to windows once script and cancel the shutdown.

I don't expect you to use this but it looked interesting enough to comment on.

---

