---
title: "How to Uninstall?"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by NJust on 2006-07-18
I've been searching on the net for ages, I'm still planing on using Ubuntu, but on another PC so I can wipe Windows.

But with this PC, here are the facts

[LIST=1]
[*]On Dapper Drake Release
[*]I have no Windows CD
[*]Using Grub to boot
[*]Partitioned a bit too much on one computer
[/LIST]

Badly need help.

I know I need to remove the partion but HOW?
Lol
Ty
Nate

---

### Post by NJust on 2006-07-18
200 People are viewing this thread surely one of them knows?!

---

### Post by confused57 on 2006-07-18
Here's a thread to remove ubuntu if you have the install CD:

[http://www.ubuntuforums.org/showthread.php?t=211169&highlight=uninstall+ubuntu](http://www.ubuntuforums.org/showthread.php?t=211169&highlight=uninstall+ubuntu)

Since you don't have the install CD and if you have a floppy drive, you can go to:

[http://www.bootdisk.com/](http://www.bootdisk.com/)

Download the Windows 98SE bootdisk, make a floppy bootdisk, boot up with the floppy:

```
fdisk /mbr
```

This should restore your Windows mbr & remove grub, then see the first link for deleting the Ubuntu partition...if I read your post correctly and that's what you want to do.  I've never done this method before, if you'd rather wait until some replies who's actually had experience with it.  It's an option to explore.

---

### Post by NJust on 2006-07-18
Ok, here's an update of whats happening;

My friend said to go on the Admin Tools and delete the partition. I did that, but left the Linux Swap. Grub was still on though and I was left with

Starting GRUB, please wait...
Error 17

So I reinstalled Ubuntu at only 3.7gb, (yes, that is small) so that it would work again, I put it as 3.7gb as I have no intentions of reusing it on this computer.

So.

What my hopes are now:

Find a way for GRUB to automatically go straight to Windows.

Any ideas/comments/abuse on how stupid I am with this or my friend is? :D

---

### Post by confused57 on 2006-07-18
Yes, you can set grub to automatically boot into Windows:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

You'll need to boot into Ubuntu, open a terminal(Applications--Accessories---Terminal), then copy & paste
the commands from the link above, then make the changes in your
/boot/grub/menu.lst.

There's also another way to make Windows the default:
1.) Open your /boot/grub/menu.lst
2.) Move the Windows entry at the bottom of the file & place above
    the line ###BEGIN AUTOMAGIC KERNEL LIST
3.) Make sure the default is 0.
Note: Be sure to backup your menu.lst as described in the first
      link, whichever method you choose.

Take your pick, at least you'll have Ubuntu to fall back on.

---

### Post by NJust on 2006-07-18
Right Okay, One final question though, my list goes:

Ubuntu
Ubuntu (recovery)
Ubuntu (memtest)
Other OS's:
Windows Media Centre
Windows HP Recovery

So, if the first ubuntu would be 0, and Other OS's: in a way is an option as it will highlight, do I change it to 4?

With this does it also mean, it automatically boots the option or it highlights that one?

---

### Post by NJust on 2006-07-18
Hang on.

Have just tried editing that but.

It's read only, and when I try those commands at the beggining it says 'password' and when I type something there's no input and the cursor doesn't move

---

### Post by NJust on 2006-07-18
Bumpidoodaa

---

### Post by NJust on 2006-07-18
Somebody! Please, I am in serious trouble for installing it and need it removing now!! :-(

---

### Post by Carrots171 on 2006-07-18
> **NJust said:**
> Hang on.

Have just tried editing that but.

It's read only, and when I try those commands at the beggining it says 'password' and when I type something there's no input and the cursor doesn't move

When you type a password into the terminal, nothing appears. This is completely normal. Just type in your password and press enter.

---

### Post by confused57 on 2006-07-18
> **NJust said:**
> Hang on.

Have just tried editing that but.

It's read only, and when I try those commands at the beggining it says 'password' and when I type something there's no input and the cursor doesn't move

It doesn't show anything when you're typing your password in, just type in your password & press enter.  From what you've shown me, looks like your default would be 3:

Ubuntu                  default   0
Ubuntu (recovery)       default   1
Ubuntu (memtest)        default   2
Other OS's:
Windows Media Centre    default   3
Windows HP Recover      default   4

Once you're able to open menu.lst in gedit, you'll see the entries and can count down to what default Windows should be.

---

### Post by NJust on 2006-07-19
Ok thanks, I'll try that later :D

---

