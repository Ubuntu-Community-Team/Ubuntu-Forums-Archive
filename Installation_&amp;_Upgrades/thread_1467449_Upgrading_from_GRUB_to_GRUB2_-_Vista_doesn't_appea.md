---
title: "Upgrading from GRUB to GRUB2 - Vista doesn't appear in menu"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by klytu on 2010-04-30
I tend to update stuff slower than most - I'm still using Hardy and I probably won't upgrade to Lucid until June-ish. I wanted to test drive GRUB2 so I upgraded following instructions here:

[[COLOR="Blue"]_https://help.ubuntu.com/community/Grub2_[/COLOR]]("https://help.ubuntu.com/community/Grub2")

When I chainloaded GRUB2, I got a menu that only contained Ubuntu; my Windows Vista bootloader entry had disappeared. I couldn't find a sample "40_custom" entry to modify when I tried to create an entry for Vista myself. Had no problem booting into Ubuntu and I could still boot Vista from the old menu. Spent about 20 minutes on it, then I gave up and reinstalled legacy GRUB. 

Anyone have success getting both Windows and Ubuntu to dual boot with GRUB2?

---

### Post by keforex on 2010-04-30
I have no problems. I have Vista, Ubuntu, Mint 7 and Xubuntu - each of them have their own hard drive and the boot loader is only in one of them, the one with Ubuntu.

The grub.cfg file is now read only but I find this so annoying that as root I changed it to read and write and edited it myself.

grub.cfg is the new menu.lst

Here's my Vista entry:

menuentry "Vista" {
	insmod ntfs
	set root=(hd2,1)
	chainloader +1
}

Modify the "set root" parameter to fit your needs.

---

### Post by 23dornot23d on 2010-04-30
I too boot Vista + Linux Mint + 3 versions of Ubuntu .... only thing I lost was the boot for Mandriva 2010 ..... 

no Idea why that is the only one I have not got to work yet ,,,

The other OS's  are ok now ..... and great idea ..... why didn't I think of that manually 
edit it and make as read only ..... that way every update to grub should not revert it back again .... 

after manual edit ...... ty.
( as one still points to the wrong boot device ... )

Don't be in any rush for Grub2 ..... if I could have left mine the old Grub I would have done .....

Maybe in time Grub 2 will get better ..... but its still not right yet .... for me anyway .....

---

### Post by klytu on 2010-04-30
> **keforex said:**
> I have no problems. I have Vista, Ubuntu, Mint 7 and Xubuntu - each of them have their own hard drive and the boot loader is only in one of them, the one with Ubuntu.

The grub.cfg file is now read only but I find this so annoying that as root I changed it to read and write and edited it myself.

grub.cfg is the new menu.lst

Here's my Vista entry:

menuentry "Vista" {
	insmod ntfs
	set root=(hd2,1)
	chainloader +1
}

Modify the "set root" parameter to fit your needs.

Thanks! ... I'll give that a shot since it worked for you. I didn't want to risk futzing with grub.cfg on the first go because the community docs (as well as grub.cfg itself) stated explicitly **NOT** to edit it.

---

### Post by keforex on 2010-04-30
> **23dornot23d said:**
> I too boot Vista + Linux Mint + 3 versions of Ubuntu .... only thing I lost was the boot for Mandriva 2010 ..... 

no Idea why that is the only one I have not got to work yet ,,,


If you edit grub.cfg just copy one entry that works and paste it where you want the mandriva entry to appear. After that, change the title to Mandriva and with System->Administration->GParted select the disk where Mandriva is installed, right click on the mandriva partition and choose Information. Copy that UUID number and paste it in your newly created mandriva menu entry inside grub.cfg - at the appropriate spots.

After that, mount that mandriva disk and with nautilus navigate to File System/boot and copy the name of the most recent shell (intrd.img.....etc) and vmlinuz....etc to their appropriate places in the grub.cfg mandriva entry. You're set! (Of course, don't forget to adjust the (hdx,x) parameter accordingly.)

---

### Post by klytu on 2010-04-30
> **23dornot23d said:**
> I too boot Vista + Linux Mint + 3 versions of Ubuntu .... only thing I lost was the boot for Mandriva 2010 ..... 

no Idea why that is the only one I have not got to work yet ,,,

The other OS's  are ok now ..... and great idea ..... why didn't I think of that manually 
edit it and make as read only ..... that way every update to grub should not revert it back again .... 

after manual edit ...... ty.
( as one still points to the wrong boot device ... )

Don't be in any rush for Grub2 ..... if I could have left mine the old Grub I would have done .....

Maybe in time Grub 2 will get better ..... but its still not right yet .... for me anyway .....

Yeah, I hear you about not rushing to use GRUB2. I noticed a number of folks upgraded to Lucid and ended up with unbootable Windows partitions. I thought maybe the upgrade to GRUB2 was part of the problem, so I wanted to try that out first. Thanks for the feedback.

---

### Post by keforex on 2010-04-30
> **klytu said:**
> Thanks! ... I'll give that a shot since it worked for you. I didn't want to risk futzing with grub.cfg on the first go because the community docs (as well as grub.cfg itself) stated explicitly **NOT** to edit it.

You're welcome. That is true, grub.cfg should not be edited - this is a work around that will be undone next time grub is installed or upgraded. I find this annoying, so I keep a copy of my working grub.cfg handy somewhere else so I can overwrite it back when I need it. Don't forget to do all this as root and change the permissions to read/write before attempting to edit it. Good luck!

---

### Post by keforex on 2010-04-30
> **23dornot23d said:**
> and great idea ..... why didn't I think of that manually 
edit it and make as read only ..... that way every update to grub should not revert it back again ....

BTW that is not true. Read only or not, it will be updated by grub. What I meant is that I manually change it to read/write so I can edit it, and after it is working I save a copy somewhere so I can replace it if I have to.

For every new shell update that is done automatically via update manager, the boot menu will be updated (and messed up). I just overwrite the new one with my old one and modify its entries to reflect the new shells.

---

### Post by 23dornot23d on 2010-04-30
Nice one Keforex ..... 

I will do as you say .... and get Mandriva going again ...

I see what you mean with keeping a copy once its been done too ..... 

I will do the same ... as I am getting fed up with the boot options not working as they should ..... 

I hate seeing any errors on boot up ..... and since grub2 .... I have no idea
how to remove them all ......... its appears to me to be a mess ...... 
but others are ok ..... which makes me think I have something wrong somewhere ,,,,,
But with Grub one I never had any errors .....

Thank you for the good advice and info .....


Yeah, I hear you about not rushing to use GRUB2. I noticed a number of folks upgraded to Lucid and ended up with unbootable Windows partitions. I thought maybe the upgrade to GRUB2 was part of the problem, so I wanted to try that out first. Thanks for the feedback.

Your welcome ..... it will work ok eventually GRUB2 that is .... and I am sure with time all the little problems will be sorted out ...........

---

### Post by klytu on 2010-05-06
> **keforex said:**
> I have no problems. I have Vista, Ubuntu, Mint 7 and Xubuntu - each of them have their own hard drive and the boot loader is only in one of them, the one with Ubuntu.

The grub.cfg file is now read only but I find this so annoying that as root I changed it to read and write and edited it myself.

grub.cfg is the new menu.lst

Here's my Vista entry:

menuentry "Vista" {
	insmod ntfs
	set root=(hd2,1)
	chainloader +1
}

Modify the "set root" parameter to fit your needs.

Keforex: Your info above along with some trial and error using the method in the community docs helped me get this working. I decided not to edit the grub.cfg file directly. Instead, I created (as root) the file 40_custom containing: ```
#!/bin/sh 
exec tail -n +3 $0

menuentry "Windows Vista" {
insmod ntfs
set root=(hd0,2)
chainloader +1
} 
```

Saved this in /etc/grub.d and made it executable: ```
sudo chmod +x /etc/grub.d/40_custom
``` Then updated GRUB2: ```
sudo update-grub2
``` Upon reboot my custom entry appeared in the GRUB2 menu and I'm able to boot into all my operating systems. 

I'm still wondering why GRUB2 didn't pick up Windows Vista automatically and add an entry on its own as the docs indicate it should. Anyway, so far so good.

---

### Post by keforex on 2010-05-17
Klytu that's great! You did the right thing - 40_custom is the file to edit. In fact, I did the same thing and don't have to worry about fixing grub.cfg all the time again. Good call!!

---

