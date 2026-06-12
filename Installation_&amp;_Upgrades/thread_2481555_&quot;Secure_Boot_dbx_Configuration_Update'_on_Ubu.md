---
title: "&quot;Secure Boot dbx Configuration Update' on Ubuntu 22.04&quot; troubles"
date: 2022-12-02
forum: Installation &amp; Upgrades
---

### Post by astronomertom on 2022-12-02
Not sure if this is the right place for this, but loads of sites describe this update, claim it works, but others seem to be having issues.

I attempted update today, on 22.04.1 using directions in
[https://askubuntu.com/questions/1429678/impossible-to-update-uefi-dbx](https://askubuntu.com/questions/1429678/impossible-to-update-uefi-dbx)
since it seemed recent.

Probably  should have stopped when it kept suggesting I delete/move files from  boot/efi.  But things seemed to progress until I tried update-grub,  which failed.

Now my machine only successfully boots into  Windows.  The UEFI options shows a generic 'ubuntu' entry, but that  fails when selected.

Tried Boot Repair - twice.  It's log  suggests that it sees the Ubuntu 22.04 boot area, but it doesn't appear  in the UEFI options.

I'm wondering if a pointer in a table is pointing at the wrong location, but where to start?  

If  I understand correctly, UEFI  needs to launch grub which presents login  options, which then boot Linux.  Suggestions on what I need to look  for to resolve this?

Are there any *clear* instructions for re-installing dual-boot (or even just single boot to Linux since I so rarely use Windows), perhaps from a USB disk.  Those that I've found are a number of years old, or seem unclear or incomplete.

Thanks,
Tom

---

### Post by astronomertom on 2022-12-03
Solved! Always the last place you look...

The message dialog on Boot Repair had a list of multiple options to try if you still couldn't get it to boot right.
Turned out to be the last one.  It presented a command that you needed to enter via the admin command prompt.
There was also a message in the log that 'EFI variables cannot be set on this system'.

This seems to work and the system starts pretty much as before.
In addition, the 'Secure boot dbx...' entry in the Ubuntu store no longer appears...

Whew!

---

### Post by yancek on 2022-12-03
If you read the boot repair page, you will see that they recommend selecting the Create BootInfo Summary option and then posting the link you get when it finishes somewhere (like this forum) where you can get help.  There will be a lot of information which will help members here who are more familiar with Grub to help you.

> EFI variables cannot be set on this system 

That usually means the computer is not EFI capable.  What version of windows do you have.  If you want to dual boot Linux with windows, both systems must be EFI of both systems must be Legacy.  All the questions in your initial post would have been answered with the boot repair output.

---

### Post by astronomertom on 2022-12-03
Yet F12 on boot-up gives me a menu of UEFI options.  I'm running Windows 10 on a Dell XPS 8930, but until this weekend, had not booted it in *months*.  Was debating over deleting it completely.  

I didn't have a configuration where I could post the log, short of trying to extract it off the Boot-Repair USB drive - but which I was unable to do.  For some reason I could not mount the USB as a readable disk on my working PopOS machine to post.  Ended up examining it manually on the machine with the problem.

Thanks for your input.
Tom

---

