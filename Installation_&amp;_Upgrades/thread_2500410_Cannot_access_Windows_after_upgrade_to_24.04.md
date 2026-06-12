---
title: "Cannot access Windows after upgrade to 24.04"
date: 2024-09-01
forum: Installation &amp; Upgrades
---

### Post by 63245aa on 2024-09-01
Have been using version 22.04 with no trouble, but made mistake upgrading to version 24.04.
24.04 works fine but I was able to choose either Win or Ubuntu on startup before now no option to do so.
Is there a file I can download to correct this or is an update planned? If not can I fix this?
Thanks

---

### Post by Rubi1200 on 2024-09-01
The fix may be as simple as updating grub.

In a terminal,

```
sudo update-grub
```

Reboot.

If this fixes it, great.

If not, run the boot info script (see my signature).

Do not repair but choose the option to create a summary report with a pastebin link.

You can then post the link back here.

---

### Post by 63245aa on 2024-09-01
Update grub seemed to work but when rebooted still no choice as with 22.04. 
Will try next option and report back.
Thank you]

---

### Post by 63245aa on 2024-09-01
Finally figured out there are three separate lines that require enter after each and the && is not part of the line.
Hope this is correct:  https//paste.ubuntu.com/p/zbnYpPcYP3/

Many hours ago I found a suggestion to modify the   /etc/default/grub   by adding   GRUB_DISABLE_OS_PROBE=false   save file and exit.
But was not able to find the /etc/default/grub line to modify it.

Thanks again

---

### Post by yancek on 2024-09-01
> But was not able to find the /etc/default/grub line to modify it.
 

That is the full path to the file and if you do not have it, you have some serious problems.  That is likely the change you need to make.  To check if the file exists, run the command below, it won't change anything but you will see if it exists:

```
cat /etc/default/grub
```

If the file shows with the command use a text editor prefaced with sudo to get root privileges to modify the file.   You can use:  vim /etc/default/grub OR nano /etc/default/grub.  vim and nano are text editors.  If you are familiar with either, use it and preface the command with sudo.

Another option is to manually create an entry for the grub.cfg file (or for a permanent entry, the /etc/grub.d/40_custom file) but in order to explain that we would need to know whether windows is installed in UEFI mode or Legacy mode and whether it is on the same hard drive as Ubuntu.

---

### Post by Rubi1200 on 2024-09-01
I don't know what the original disk layout was or how you upgraded.

The script results seem to show that Ubuntu is in working order.

However, the only part of Windows it detects is the Windows Recovery Environment.

lines 103-106:
sda1 is the Windows recovery partition and then you have 3 Linux partitions.

Ubuntu is on sda3 but 46.6GB seems pretty small for a regular install.

What was on sda2? This is a 229.9GB partition

Finally, sda4; is this a separate /home partition?

I hope you have backups of Windows.

---

### Post by yancek on 2024-09-01
How old is this hardware and which windows are you using?  Boot repair shows it as XP?/

---

### Post by 63245aa on 2024-09-01
Yanek: sudo cat/default/grub showed much info but when I tried to insert image and send got a message that security token was missing.
Rubi 1200: Yes very old Win XP but it has many programs and info that I like.
I have computer specs from Belarc advisor but don't know if I can specs. I tried sending the file but I think that coused the security token problem.
Will try if this message goes trough.

---

### Post by 63245aa on 2024-09-01
Specs:

---

### Post by 63245aa on 2024-09-01
Results of sudo cat etc/default/grub:

---

### Post by 63245aa on 2024-09-01
Results 2nd page:

---

### Post by 63245aa on 2024-09-01
I think the answer is to modify the "/etc/default/grub"  file by adding  "GRUB_DISABLE_OS_PROBER+false".
But I don't know how to do this. I have limited programming skills, so will need some details.
Appreciate any help.

---

### Post by oldfred on 2024-09-01
You show both old XP and some newer Windows boot files.
Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

And I see mention of plop boot manager line 153, but I do not think Boot-Repair even looks for that old boot, so not reported.
Is plop in your sda1?
And you have unetbooti which is more for booting live installer.

You show this:
C:\plop\plpbt4win.ldr
[https://www.plop.at/en/bootmanager/plpbt.bin.html#rungrub](https://www.plop.at/en/bootmanager/plpbt.bin.html#rungrub)


I have an old grub2 boot entry like this, but know nothing about plop.
If standard Windows XP, entry is a lot different.
```
menuentry "Plop Boot Manager Install"{
set root ='(hd0,1)'
linux16 /boot/plpbt.bin
}

```

You can try editing with your filename  into 40_custom & update grub.
sudoedit /etc/grub.d/40_custom
sudo update-grub

If experimenting you can put more than one example into 40_custom.

Standard Windows XP type entry:
```
# This method applies to BIOS Windows and to FreeDOS
menuentry &#8220;Windows XP on sda1, by chainloader&#8221;  {
 insmod chain
set root=(hd0,1)
chainloader  +1
 }

Or, not sure now which of my old notes is more correct

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4C908D69908D59FA
     drivemap -s (hd0) ${root}
    chainloader +1
}



```

---

### Post by pierrel2 on 2024-09-02
I have the same problem i.e   I cannot choose to run window on boot. I changed grub by uncomenting  "GRUB_DISABLE_OS_PROBER=false" but this did not solve the problem. What can I do next?

---

### Post by 63245aa on 2024-09-02
**Pierel2 ** would you show exactly how you uncomented  "GRUB_DISABLE_OS_PROBER=false.
I understand that you must modify the  "etc/default/grub"  file by adding "GRUB_DISABLE_OS_PROBER=false"
But what exactly do you type on the terminal do do this.
Thanks

---

### Post by pierrel2 on 2024-09-02
I simply removed the # symbol at the beginning of the line

---

### Post by 63245aa on 2024-09-02
I think that is why it didn't work. 
Must add "GRUB_DISABLE_OS_PROBER=false" to the "/etc/default/grub file".

---

### Post by pierrel2 on 2024-09-02
In my knowledge, removing the # symbol at the beginning of the line make it active, so is equivalent to adding the line. The # character change the line as a simple comment.

---

### Post by 63245aa on 2024-09-02
**pierrl2:  **You probably know more than I do so let's wait for an expert answer.
Would have been nice if the programmers gave a choice before we installed 24.04.
Hopefully a future simple upgrade will fix this.

---

### Post by yancek on 2024-09-02
Did you try entering the suggestions by oldfred in post 13 in your /boot/grub/grub.cfg file?  If so, what happened?
Did you try copying the line:  GRUB_DISABLE_OS_PROBER=false in the /etc/default/grub file?  You need to do this with root/sudo privileges.  If so, what happened when you ran update-grub?  If you had that entry in the file you would just delete the # symbol at the beginning of the line.  If it is not there, you need to copy it there.

Ubuntu just changed that entry to have os-prober disabled by default so they are not likely to change it back.

---

### Post by 63245aa on 2024-09-02
[B]yancek:
[/B]Very complicated for me but I am trying.
I typed sudo -i which gave me root privileges (the $ changed to #) then sudo cat /etc/default/grub 
This opened the file where I found that line (GRUB_DISABLE_OS_PROBER=false) was already there but preceded by # which I think
indicates it is commented. I tried to uncomment it by highlighted it and pressing delete and also by trying Ctrl D but both did not work.
Do I have to reinsert GRUB_DISABLE_OS_PROBER=false somewhere or just find a way to remove the preceding # symbol?

Thanks, I know it is difficult dealing with a novice but I appreciate your patience.

---

### Post by oldfred on 2024-09-02
You do not need sudo -i and then use sudo.
You just need an editor, cat just displays the output.

sudoedit /etc/default/grub

sudoedit uses a default terminal editor in sudo mode, often default is nano.

To know a command use man, q to exit:
man cat
man sudoedit

---

### Post by 63245aa on 2024-09-03
Some progress need one more step.
Used sudoedit /etc/default/grub, highlighted the # before GRUB_DISABLE_OS_PROBER=false, pressed Ctrl D which
removed the # symbol. Then Ctrl X to save then Y to apply.
But when file was reopened the change was not made (# still appeared before)
Tried sudo update-grub before closing but had no effect.
What am I missing?

---

### Post by pierrel2 on 2024-09-03
Apparently, your new grub file was not saved. Did you check its time of creation?
Anyway, it seems that this change does not solve the problem (at least in my case).

---

### Post by 63245aa on 2024-09-03
What should I have done to save it?
Time of creation???

---

### Post by pierrel2 on 2024-09-03
I suppose you can visualize your files on the hard disk (using Nautilus for example).  This give the date of creation of each file.

---

### Post by 63245aa on 2024-09-03
**pierrel2:** You said you were able to able to remove the # from the GRUB_DISABLE_OS PROBER=false file.
                Please read my post 23 and let me know what I did wrong to remove it permanently.

---

### Post by pierrel2 on 2024-09-03
I used the basic text editor (it will be proposed with a click right on the file) so that you can modify the text by removing the # sign, then you save the file using the menu of the editor.

---

### Post by tea for one on 2024-09-03
> **63245aa said:**
> Some progress need one more step.
Used sudoedit /etc/default/grub, highlighted the # before GRUB_DISABLE_OS_PROBER=false, pressed Ctrl D which
removed the # symbol. Then Ctrl X to save then Y to apply.
But when file was reopened the change was not made (# still appeared before)
Tried sudo update-grub before closing but had no effect.
What am I missing?
Probably missing Ctrl O
If you are using nano text editor:-
Ctrl O - Write out i.e. apply your change
Ctrl X - Exit i.e. this does not apply the change, only exits

---

### Post by pierrel2 on 2024-09-04
I resolved the problem: look in your grub file. You will find the line:
GRUB_TIMEOUT_STYLE=hidden
Change it with:
GRUB_TIMEOUT_STYLE=menu

Tell me if it works correctly for you too.

---

### Post by 63245aa on 2024-09-04
Yes it does now work. Thank You. 
I was using sudoedit not nano sudo. Changes now stayed and can access my old WinXP.

---

