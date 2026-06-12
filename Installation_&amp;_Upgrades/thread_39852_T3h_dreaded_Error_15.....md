---
title: "T3h dreaded Error 15...."
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by senkila on 2005-06-06
hehe, hey again guys...got another error here....this time its t3h dreaded error 15.
Story goes, after the 20th (or 30th) boot you have to run fsck or something like that....anyway so i got my dad to fix it (always go for the fail-face option  :-) ).
Anyway, i thought he sorted it, so after he left i booted it up and got this:-

Verifing DMI Pool Data......
Boot from CD:
GRUB loading stage 1.5

GRUB loading, please wait....
Error 15

And thats all I get. Seeing i'm still inexperienced with Linux, i'm tempting to go back to Windows (please don't say i'm commiting blasphemy =p). Although i'm sure there's a way of fixing this without wiping my harddrive clean... i have to much Anime on it, I would get my dad to fix it again...but my mum would get annoyed that he's spending to much time on the computer....
So if anyone that could help, it'll be greatly thanked ^^.

---

### Post by mingus on 2005-06-06
Looks like grub is not properly installed.  Probably easiest first thing to do, and since you cannot boot, use the install CD with :rescue at the prompt.  You will be taken thru a series of setup screens like before, and then asked to tell the installer which partition root (/) is installed on.  You are then dropped into a shell.

Do
#update-grub
to have grub's menu.lst file rebuilt, and then
#grub-install
to reinstall the loader

---

### Post by senkila on 2005-06-06
erm...sorry about the lack of intelligence butthat just wentright over my head, think i'll go grab a coffee and attempt to figure that out.....sorry for not figuring it out  ](*,)

---

### Post by mingus on 2005-06-06
sorry about that . . . I'll try to make it more clear . . .

GRUB is the program that boots the operating system.  It does what ntldr does for Windows.

When you install Ubuntu and get to the boot loader step, if you take the defaults the installer will install create a control file for GRUB (/boot/grub/menu.lst) and will install GRUB.  GRUB is actually 2 programs, called Stage 1 and Stage 2.  Stage 1 starts the boot process and Stage 2 loads the OS.  The error messages you got indicate something may not be right in how GRUB got installed or in the control file that was created.  

The instructions below are to re-create the file and re-install GRUB.  This is the easiest thing to try first to fix the problem.

1.  Boot from the Ubuntu installation CD
2.  At the : prompt, where you would usually type :linux or :expert to begin the install, instead type :rescue
3.  The rescue mode goes thru some of the same steps you did when you installed Ubuntu.  Answer them just like you did when you installed.
4.  After about 10 steps there will be a screen that will show you all the disk partitions and ask you which one the root or / directory is on.  This is very important.  After you tell it which one, it will mount that partition.
5.  Because you are in "rescue" mode, you will now be put in a terminal or "shell" where you can execute commands.
6.  At the prompt, type "update-grub" and hit Enter.  This will rebuild the GRUB control file, menu.lst.
7.  Then type "grub-install" and hit Enter.  This will re-install the GRUB loader.
8.  Then type "reboot" and hit Enter.  Your computer will restart.

Give it a try.

---

### Post by senkila on 2005-06-07
Yay it worked. Thank you  :razz:..... guess i need to learn alot more about linux than i first thought.

---

### Post by Miguel on 2005-08-30
OMG!!!!

If I had only read this a few hours sooner... I just reinstalled Ubuntu 5.04 a month and a half away from installing 5.10.

The thing is... all threads I've seen pointed to the command 
grub-install /dev/hda

Which replied to me with a "error at the end of stage 1". This is weird, because GRUB was pointing to the error 15 at stage 1.5 (I guess it was because menu.lst was not found).

As this failed, I reinstalled everything. Heck. Who told me to mess with Partition Magick when everything was working fine?

Anyway, thanks for your answer.

---

### Post by jsuen on 2005-09-04
sorry to wake an old thread, but i'm still having problems off getting my server past this error 15.

i've gone through the steps mentioned above, and all works fine up to the point where i have to update grub through the shell mounted - my problem is that it can't find the commands that i need to run.

i.e. i'd run
~# update-grub
sh: update-grub: not found
~# grub-install
sh: grub-install: not found

is there something i'm missing here? i'm booting from the installation cd with the 'rescue' option. just hope not to lose any information here...

thanks for any help,

jon

---

### Post by mingus on 2005-09-05
Been quite a while since I worked this problem, so I'm going from memory . . .

First, make sure that the root (/) partition was mounted.  Once you are in the shell, do:
#cd /
#ls

and you should see the top of the filesystem tree (the directories lib, usr, opt, dev, etc . . .).  If you don't, then you will need to mount it yourself or go back thru the steps.

You can also do Ctrl-Atl-F2 to take you to another tty (session), which I think uses the bash shell.  From there, after making sure the partition is mounted, try grub-install again.

If you installed the /boot directory on a separate partition, you will also need to mount it from within the shell.

Fiinally, if grub-install is not found (it's a shell script), you can do:
#grub
to take you into grub interactively.  It is fairly simply to install from here.  See:
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

Also make sure the /boot/grub/device.map has your boot devices in the file.

---

