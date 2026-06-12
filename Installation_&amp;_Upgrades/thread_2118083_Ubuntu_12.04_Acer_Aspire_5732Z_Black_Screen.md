---
title: "Ubuntu 12.04 Acer Aspire 5732Z Black Screen"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by IssacSierra on 2013-02-20
Right I have been battling with this black screen issue for the past few days and this is what I have found:

When booting from live DVD, hold shift once MOBO splash screen disappears.
When the options menu appears select language and hover over install from live DVD.
Press F6 to select other options, select nomodeset.
Also add the command “acpi_osi=Linux” to the end of the boot command this will allow you to install the OS.

Once the install has finished and the machine has been reset again once the MOBO splash disappears hold down the FN key and press the right arrow to increase brightness.
This should allow you to boot without receiving a black screen. You will need to increase the brightness each time you boot the machine. 

You may need to add the command line “acpi_osi=Linux” to the boot command permanently. To edit the grub and add this command open the Terminal, use the command “sudo gedit /etc/default/grub”, this will open up a text editor, look for this line:

GRUB_CMDLINE_LINUX_DEFAULT="quite splash"

Add “acpi_osi=Linux” such that it looks like:

GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi=Linux"

Save and exit and from within the terminal use the command “sudo update-grub” to put the changes into effect.

To avoid pressing FN and the arrow key during boot you can edit the grub and add a nomodeset command, the downside to this is that you will be forced down to a lower graphics setting and loose a few functions within Linux.

To edit the grub and add this command open the Terminal, use the command “sudo gedit /etc/default/grub”, this will open up a text editor, look for this line:

GRUB_CMDLINE_LINUX_DEFAULT="quite splash"

replace the “quiet splash” part with “nomodeset”.

Save and exit and from within the terminal use the command “sudo update-grub” to put nomodeset into effect.

I have pre-marked this thread as solved as it does work, could be better as I sometimes forget about adjusting the brightness when I boot. Are there any other solutions available so I do not have to adjust the brightness each time I boot aside from nomodeset?

---

### Post by Toz on 2013-02-20
> I have pre-marked this thread as solved as it does work, could be better as I sometimes forget about adjusting the brightness when I boot. Are there any other solutions available so I do not have to adjust the brightness each time I boot aside from nomodeset? Try also adding **acpi_backlight=vendor** to the grub command line like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

---

### Post by IssacSierra on 2013-02-21
No luck with acpi_backlight=vendor, will double check when I have a little more time at my disposal. Any other suggestions?

Cheers,
Issac.

---

### Post by Toz on 2013-02-21
When you try it, post back the results of:
```
cat /proc/cmdline
```
...to confirm it is active.

You might also want to try:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
```

If neither work, post back:
```
lspci | grep VGA
```
...(See: [http://ubuntuforums.org/showpost.php?p=10740136&postcount=3]("http://ubuntuforums.org/showpost.php?p=10740136&postcount=3"))

---

### Post by IssacSierra on 2013-02-21
"lspci | grep VGA" yields the following:
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

after checking the other thread you linked and following the instruction to add

Code:
setpci -s 00:02.0 F4.B=00

to /etc/rc.local. All seems to be working properly.

Thank you very much.
Issac.

---

