---
title: "Unsuccessful update"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by tami2 on 2015-06-21
Hello!
I had Windows7 on my computer, then installed Ubuntu 14.04. Everything was ok, but while Ubuntu was updating the last time my computer shut down. Now when I'm trying to itch it on, there appears a message:

GNU GRUB version 2.02~beta2-9ubuntu1.2
Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

After that there is a list of errors, some symbols in whih are replaced by square symbols and question marks.
I tried to open BIOS, but such message appears just after switching on.

It isn't very neccesary for me to save all the files, which were used in Ubuntu, so it will be ok just to reinstall it.

Could somebody help me, please?

---

### Post by Bashing-om on 2015-06-21
tami2; Hello; Welcome to the forum.

If -and only IF :
> 
I tried to open BIOS, but such message appears just after switching on.
 this is true and that these error messages appear in bios - Before the operating system boots - then
And I do hate to be the bearer of bad news -
You are looking at hardware failure at some point .
Like a hard dive has failed.

Triple check that bios sees your hard drive(s). If so - maybe best now to check the health of the hard drive.

Can you boot a liveDVD(USB) to run the SMART test ?

Else another common issue is the power supply failing ->
and the list of what can fail can go on and on and on . One would need the exact reported errors to make a better assessment of the failure.

[INDENT][INDENT]nothing short of faith last forever
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-06-21
As regards reinstalling if you use the Ubuntu live session to make copies of any documents you do not want to lose, then that will be sufficient. Of course, you will also need to reinstall any applications that you installed that were not part of a default installation.

If you are getting a Grub boot menu then you have gone past point where the BIOS has control. It is most likely that Grub is unable to find the Linux kernel for some reason. You can try Boot Repair. That repairs our boot options. It does not fix problems that come when Linux and Ubuntu are being loaded.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

---

### Post by tami2 on 2015-06-22
Thanks for your replies. But I still can't enter BIOS. I did it before this problem, but now the best thing I get is the sound of opening BIOS with Grub prompt appearing.

---

### Post by Bashing-om on 2015-06-22
tami2; Hey ;

I do not 'know' weather this is a true statement or a misunderstanding of what is meant:
> 
But I still can't enter BIOS.


If you are unable to access the mainboard firmware; then yeah, there also exist another serious problem. Nothing is more paramount at this time than accessing the firmware.
When you 1st boot the system the firmware loads and displays what key to press to access the settings utility. Do you see this screen prior to continuing to boot the operating system of choice ?
At this time we want to rule out the operating system as the problem. To that end we want to boot the liveDVD, To do that we must insure that the firmware is set to boot that medium ( or a USB thumb drive ). What do you have on-hand to work with in this instance of a alternate to boot up with ?

[INDENT][INDENT]we try
[INDENT][INDENT][INDENT]but, to soon to make a call
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

