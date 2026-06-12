---
title: "Blinking cursor after install asus F50 SV ( ACPI issue?)"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by bboyshane on 2010-10-14
Hello,

When booting live 64bit(and 32bit) the only way I could get it to work was to select "NO ACPI" option under F6 options.

Tried installing, and now, I get the same blinking cursor as when I tried running live CD normally.

How do I select a no acpi option at boot? So I can boot into ubuntu?

thanks

---

### Post by lottomotto on 2010-10-14
SAme Issue Asus F50Sv

---

### Post by taquilla on 2010-11-08
I have Asus F50SV laptop

After upgrade to 10,10 I can't run with new kernel, now I've upgrade the kernel to 2.6.35.23 and no solution. (I tried USB way, and the same)

Blinking cursor :(

Now I use old kernel (2.6.32.25)  to run Ubuntu 10.10

---

### Post by vinceve on 2010-11-28
Got this problem too with my asus F70sl!!!

---

### Post by ceejayf on 2010-11-28
There seems to be some kind of ACPI issue with Asus laptops and Maverick (10.10).

You can make your machine boot by adding the "acpi=off" parameter to your kernel boot line in grub.

To do so:

1.  As the system boots, hold down the shift key to access the grub boot menu.

2.  Move the cursor down to the line that begins with 'linux'.  In my case, this line is:
        
         linux /boot/vmlinuz-2.6.35.22-generic                       
         root=UUID=1105aad8-65d9-4466-9/fec-da3351344292 ro   
         quiet splash

3.  To the end of this line, add 'acpi-off'.  It will now look like this:

         linux /boot/vmlinuz-2.6.35.22-generic                       
         root=UUID=1105aad8-65d9-4466-9/fec-da3351344292 ro   
         quiet splash acpi=off

4.  Press Ctrl-x to boot.  The system should now boot into Ubuntu.

The downside here is that your laptop will have no ACPI data to work with, so you won't have a battery meter or the ability to hibernate etc.

Also, the change isn't permanent.  If you want to make this change permanent, you'll need to update the grub config.

To do this, log into the OS and follow these instructions:

1.  Open a terminal

2.  Type 'sudo gedit /etc/default/grub' - enter your sudo credentials

3.  When gedit appears, the grub config file should be loaded.  Find the line in the first section with the text "GRUB_CMDLINE_LINUX_DEFAULT=".  Add the 'acpi=off' parameter to the end of the line.  The line should now look something like this:

        GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

4.  Save the file and close the gedit window.  Now run 'sudo update-grub'.  Reboot your system.


The ACPI=OFF option should now be part of your permanent boot options.

I'm about to try loading Lucid (10.04) on my machine (An Asus F50sf) - if I'm successful I'll post again.

---

### Post by ceejayf on 2010-11-28
I can confirm that this isn't a problem in Lucid.  I just installed 10.04 LTS (amd64) on my machine, and I have no ACPI issues.

---

### Post by zeppelinux87 on 2011-08-24
I've got an Asus X61SL (motherboard F50SL) and I'll still continue to get same problem also with new kernel release (2.6.36/38/39):
I also compile kernel 2.6.36 from old good work config kernel 2.6.32, but I have again problem hang on boot.

Is there a solution without add "acpi=off"???

How can I know what does it hang my notebook in fake kernel?

Is there something with a precompile good kernel for my notebook?

Thanks a lot.

---

### Post by MAFoElffen on 2011-08-24
> **ceejayf said:**
> There seems to be some kind of ACPI issue with Asus laptops and Maverick (10.10).

You can make your machine boot by adding the "acpi=off" parameter to your kernel boot line in grub.

To do so:

1.  As the system boots, hold down the shift key to access the grub boot menu.

2.  Move the cursor down to the line that begins with 'linux'.  In my case, this line is:
        
         linux /boot/vmlinuz-2.6.35.22-generic                       
         root=UUID=1105aad8-65d9-4466-9/fec-da3351344292 ro   
         quiet splash

3.  To the end of this line, add 'acpi-off'.  It will now look like this:

         linux /boot/vmlinuz-2.6.35.22-generic                       
         root=UUID=1105aad8-65d9-4466-9/fec-da3351344292 ro   
         quiet splash acpi=off

4.  Press Ctrl-x to boot.  The system should now boot into Ubuntu.

The downside here is that your laptop will have no ACPI data to work with, so you won't have a battery meter or the ability to hibernate etc.

Also, the change isn't permanent.  If you want to make this change permanent, you'll need to update the grub config.

To do this, log into the OS and follow these instructions:

1.  Open a terminal

2.  Type 'sudo gedit /etc/default/grub' - enter your sudo credentials

3.  When gedit appears, the grub config file should be loaded.  Find the line in the first section with the text "GRUB_CMDLINE_LINUX_DEFAULT=".  Add the 'acpi=off' parameter to the end of the line.  The line should now look something like this:

        GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

4.  Save the file and close the gedit window.  Now run 'sudo update-grub'.  Reboot your system.


The ACPI=OFF option should now be part of your permanent boot options.

I'm about to try loading Lucid (10.04) on my machine (An Asus F50sf) - if I'm successful I'll post again.
On issues where you add "acpi=off" and it works... Please keep going on and do some more homework.  Using this is a shortcut but not a good solution to an end.  It will cause other acpi problems, including issues with backlighting, suspend, hybernation, hard disks... to name a few.

If acpi=pff works, then try substituting in with the kernel options
```
acpi_osi=Linux vga=[COLOR=Red]xxx[/COLOR]
```...where [COLOR=Red]xxx[/COLOR] is a valid decimal vga mode that your GPU supports.  Then go to the line 
```

# GFXMODE=640x480

```Uncomment it and change it to the same resolution.

Run "sudo update-grub" then reboot.

If that doesn't work, then the other workaround is to set "linux_gfx_mode" to "text" (default is "auto").

Please refer to post one of my sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by Laerten on 2011-11-18
Try follow [this discussion]("http://translate.google.it/translate?hl=it&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C487071.msg3860260.html")!
[http://translate.google.it/translate?hl=it&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C487071.msg3860260.html](http://translate.google.it/translate?hl=it&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C487071.msg3860260.html)

---

