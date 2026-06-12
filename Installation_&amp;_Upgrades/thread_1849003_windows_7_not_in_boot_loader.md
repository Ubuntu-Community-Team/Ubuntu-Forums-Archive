---
title: "windows 7 not in boot loader"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by iownahemi on 2011-09-23
Hi new to the forums and Ubuntu, thanks in advance for any help.
I partitioned my 500 gb hd, installed Ubuntu to dual boot, but when I boot the system it goes directly to ubuntu and doesn't give me the options to boot to windows, when I check the hd windows 7 is there. I've been working on this for days and can't figure it out. I'm new to Ubuntu but not to windows, so I guess I'm a semi noob.. 1 ? is can I just reinstall again over Ubuntu or do I have to uninstall first or  is there a way to fix without reinstall? I'm using my other computer to write to this forum so I have a way to research.
My system is
HP Dual core 2.5 gig AMD Athlon
3 gig RAM
500 gig HD
I partitioned 43 gig for Ubuntu
and 43 gig for storage
the rest is Windows
Thanks again for any help

---

### Post by sanderd17 on 2011-09-23
Can you give us the output of the boot info script? [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by iownahemi on 2011-09-23
I tried that and it didn't do anything
I typed:   su bash ./boot_info_script.sh
and it say it doesn't exist

---

### Post by ajgreeny on 2011-09-23
From the folder where the .sh file is sitting you need to run ```
sudo ./boot_info_script060.sh
```su does not work in Ubuntu; we use sudo instead to get temporary root permissions for commands.  Note also you need the full name of the script, now **boot_info_Script060.sh** if my version is the same as yours.

---

### Post by iownahemi on 2011-09-23
I formatted the partition and this time click import other os, which I think I missed the first time, so we will see soon if this worked!!

---

### Post by ajgreeny on 2011-09-23
> **iownahemi said:**
> I formatted the partition and this time click import other os, which I think I missed the first time, so we will see soon if this worked!!
That should not make any difference to your grub problem as the "import" at installation just brings across some of your files and profiles from Windows to the /home/user in ubuntu.  I hope you formatted the right partition!

---

### Post by iownahemi on 2011-09-23
> **ajgreeny said:**
> That should not make any difference to your grub problem as the "import" at installation just brings across some of your files and profiles from Windows to the /home/user in ubuntu.  I hope you formatted the right partition!
I did format the right partition, I know them by heart now lol..and if it doesn't work well thats par for the course for me...it's almost done, so I'll see in a minute or two...thanks

---

### Post by iownahemi on 2011-09-23
> **sanderd17 said:**
> Can you give us the output of the boot info script? [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

> **ajgreeny said:**
> That should not make any difference to your grub problem as the "import" at installation just brings across some of your files and profiles from Windows to the /home/user in ubuntu.  I hope you formatted the right partition!

You were right as I thought you would be, so where do I type that in?
Sorry I'm such a noob, I really appreciate your help

---

### Post by Mark Phelps on 2011-09-23
What you SHOULD be able to do is boot into Ubuntu, open a terminal and enter "sudo update-grub".  That will search for the OSs and kernels on your drive.  Watch as it enumerates what it finds.  You should see something like "Windows 7 Loader on ...".

If you see that in the list, when you reboot, you will be presented with a GRUB menu, from which you can choose your OS.

---

### Post by madjr on 2011-09-23
you can also try Boot-Repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

but with boot info script you will know exactly where the problem was.

---

### Post by iownahemi on 2011-09-23
> **Mark Phelps said:**
> What you SHOULD be able to do is boot into Ubuntu, open a terminal and enter "sudo update-grub".  That will search for the OSs and kernels on your drive.  Watch as it enumerates what it finds.  You should see something like "Windows 7 Loader on ...".

If you see that in the list, when you reboot, you will be presented with a GRUB menu, from which you can choose your OS.

Did it and I found it ,it's on sda 1, so now close all windows and reboot??

---

### Post by iownahemi on 2011-09-23
> **Mark Phelps said:**
> What you SHOULD be able to do is boot into Ubuntu, open a terminal and enter "sudo update-grub".  That will search for the OSs and kernels on your drive.  Watch as it enumerates what it finds.  You should see something like "Windows 7 Loader on ...".

If you see that in the list, when you reboot, you will be presented with a GRUB menu, from which you can choose your OS.


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3

This is what it shows
I had updated  Vista to windows 7 thats why it's showing

---

### Post by aura7 on 2011-09-23
Boot Repair is the best option else you also try Rescatux

[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

---

### Post by iownahemi on 2011-09-23
Thanks for your help..I'm downloading boot repair now, we will see what happens
thanks again for the help!!

---

### Post by Mark Phelps on 2011-09-24
Don't know how good a job rescatux will do on a Win7 boot.  never tried it.

What is more likely to work is an actual Win7 Repair CD -- which you can now obtain from the link below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Be advised though, that you have to PURCHASE these now, as they are no longer offered for free.

Had you used the Backup feature in Win7 when it worked, you could have created and burned such a CD for free.

---

