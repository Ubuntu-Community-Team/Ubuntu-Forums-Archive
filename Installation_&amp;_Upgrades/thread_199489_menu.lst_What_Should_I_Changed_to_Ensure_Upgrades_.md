---
title: "menu.lst: What Should I Changed to Ensure Upgrades Go Smoothly?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Wolfey on 2006-06-18
I've been messing around a bit more with Ubuntu lately, and with some alterations to menu.lst, I no longer have to edit it manually to be able to boot into Ubuntu...Though that particular issue may have been due to incorrect settings in the file when Ubuntu was originally installed.

Upgrading still makes a bit of a mess in the list of what I can boot into, however.  Here's the current contents of my menu.lst file that pertain to this:

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda6 ro console=tty0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,2)
kernel		/vmlinuz root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-amd64-generic Previous 
root		(hd0,2)
kernel		/vmlinuz.old root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img.old
savedefault
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```
A few more entries were present in the list ("Previous" versions for some of the other selections) but were removed, as I wasn't going to be using them.

I want the list to be in this order, with only these selections listed (no more, no less):

[list=1]
[*]Windows XP
[*]Ubuntu (kernel 2.6.12-10-amd64-generic Default)
[*]Ubuntu (kernel 2.6.10-6-amd64-generic Previous)
[*]Ubuntu (memtest86+)
[/list]
Is there a way I can edit the menu.lst file to make sure only these ones show up?  Also, if I do, will future upgrades to Ubuntu on my system also update the current and previous versions of it in the list?

Thank you in advance for any help you can give me here :)

---

### Post by Wolfey on 2006-07-03
*(Bumping topic...)*

Would anyone know what modifications would need to be made to menu.lst to help keep the boot list organized the way I mentioned above?

Also, there's one thing I should've been more clear with when I posted that: #2 and #3 in the list (for Ubuntu) should refer to the current and previous versions (respectively) of Ubuntu that are on the system, not just the two versions listed there.

---

### Post by Akula on 2006-07-10
If I got it right, you wish to remove 'Ubuntu, kernel 2.6.12-10-amd64-generic' from the menu? I have modified the menu.lst myself succesfully for now (in other words nothing has broken down yet ;).

You just have to put # -mark on beginning on every line of the menu option you wish to remove:

REMEMBER that it would be good to make backup of menu.lst!

To edit menu.lst, you have to type:
```

cd /etc
sudo gedit menu.lst

```

These are the lines to be modified:
```

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

```

So that they look like this:
```

# title		Ubuntu, kernel 2.6.12-10-amd64-generic 
# root		(hd0,2)
# kernel	/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
# initrd	/initrd.img-2.6.12-10-amd64-generic
# savedefault
# boot

```

Another way to do it is to remove those lines, but you never know if you need them later (your choice)?

About updates, you might want to save a backup at least when installing new kernel. I noted that whenever a new kernel is installed or old remowed, menu.lst is modified automatically to be up to date.

Anyone please correct if I'm wrong.

PS: This worked for me, but I'm not an expert. Please don´t send an assassin after me if I'm wrong. =)

---

### Post by Wolfey on 2006-07-13
> **Akula said:**
> If I got it right, you wish to remove 'Ubuntu, kernel 2.6.12-10-amd64-generic' from the menu?
Yep, that's what I want to do :)

> **Akula said:**
> You just have to put # -mark on beginning on every line of the menu option you wish to remove:

REMEMBER that it would be good to make backup of menu.lst!
I made a backup earlier, just in case, so that's taken care of.

Thank you very much for supplying that code - the list looks cleaner now! :D

(The fix is a lot simpler than I expected, too :p)

> **Akula said:**
> About updates, you might want to save a backup at least when installing new kernel. I noted that whenever a new kernel is installed or old remowed, menu.lst is modified automatically to be up to date.
I'll keep that in mind - Again, thank you for the code :)

> **Akula said:**
> PS: This worked for me, but I'm not an expert. Please don´t send an assassin after me if I'm wrong. =)
As I said earlier, it worked, so you have nothing to worry about here :lol:

---

### Post by Wolfey on 2006-07-16
I just found something out: updating programs in Ubuntu via Synaptic adds those lines back in :(

Here's the complete contents of my menu.lst file, following a restart after updating those programs:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,2)
# kernel	/vmlinuz root=/dev/hda6 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda6 ro console=tty0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,2)
kernel		/vmlinuz root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-amd64-generic Previous 
root		(hd0,2)
kernel		/vmlinuz.old root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-6-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.10-6-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```
So, my list is now composed of the following, compared to what it originally was (I'm bolding what I want to keep):

[list][*]**Windows XP** (listed outside Automagic Kernels List)
[*]**Ubuntu, kernel 2.6.12-10-amd64-generic Default **
[*]**Ubuntu, kernel 2.6.10-6-amd64-generic Previous **
[*]Ubuntu, kernel 2.6.12-10-amd64-generic 
[*]Ubuntu, kernel 2.6.10-6-amd64-generic 
[*]Ubuntu, kernel 2.6.10-5-amd64-generic 
[*]**Ubuntu, memtest86+**[/list]However, there's something I noticed this time around, that I didn't see before...Would something in this section:

```

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

```
Or this section:

```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```
Have something to do with the extra lines being created in this file?

---

### Post by Akula on 2006-07-18
Yeah, this is something I have to do also when I for example install new kernel or something like that. The menu.lst is changed back and I have to modify it again.

As before you can remove those unwanted menuoptions with '#' on beginning of each of these lines or removing the lines:
```

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-6-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.10-6-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda6 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

```

I have not found any easier way correct the list after update. Anyway the file is quite simple after all...

I do not know about those alternative settings, never used or tried, because in my opinion it is easier to let the system automatically make new boot option and set the paths right. This way I only have to remove unnecessary option lines.

---

### Post by Wolfey on 2006-07-18
It does work, but is only a workaround - having to comment out or remove these lines after every update (or at least the ones that update the version number) gets annoying after awhile.  There's got to be a fix somewhere, to keep those extra entries from showing up in the first place...

Still, thank you for mentioning that :)

---

### Post by Wolfey on 2006-07-31
*(Bumping topic - 2nd Time...)*

If there is nothing I can do about this issue but comment out or remove the lines, I can live with that.  However, I do have the feeling that there *has* to be some way to keep them from showing up in the first place... :-k

---

