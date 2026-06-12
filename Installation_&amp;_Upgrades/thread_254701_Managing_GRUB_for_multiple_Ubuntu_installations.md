---
title: "Managing GRUB for multiple Ubuntu installations"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by andrewski on 2006-09-10
I like Ubuntu so much, I figured why have one when you can have two? :D

I just wiped my Windows XP, which I rarely use, to install Ubuntu Edgy on its own partition.  Thusly, I have Dapper and Edgy both installed.

The trick, though, is managing GRUB.  At the moment, I added a temporary GRUB entry for my new Edgy installation just so I can get into it.  However, one of the nice things that Ubuntu does (well, Debian really) is to update the GRUB entries for all available installed kernels.

Can anyone think of a way to do this for both of these two parallel installations?  Even "chainloading"--loading a second GRUB after the primary one--would be fine, but I don't know if that's possible.

Thanks!

---

### Post by lha on 2006-09-10
> **andrewski said:**
> 
Can anyone think of a way to do this for both of these two parallel installations?  Even "chainloading"--loading a second GRUB after the primary one--would be fine, but I don't know if that's possible.

Thanks!

Chainloading another instance of grub is possible. If you put your secondary grub on hda2, add

title           The Other Grub
root            (hd0,1)
chainloader     +1

into your menu.lst. If you want to be able to return to the primary grub from the secondary and your primary grub is on mbr, use 'root (hd0)'.

---

### Post by Herman on 2006-09-10
I agree with lha, and you will also need to know how to install Grub to the first sector of your Ubuntu partition first too. You may already know that (it's quite simple), but just in case, I thought I'd help a little.
You just do the same as explained in catlett's great how-to for installing grub to MBR, [Click here]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=catlett%27s+grub"), but instead of using 'setup (hd0)' for the second last command, (that will instaall grub to MBR), you replace that with 'setup (hd0,1). (If (hd0,1) is the partition you want to chainload, or whatever your partition number is). That will install grub to the first sector of your (hd0,1) Ubuntu partition so you can chainload it.
It's a good idea to have grub installed in both the MBR and in the first sector of each partition anyway. I install a bootloader to the first sector of all my Linux installs.
Regards, Herman

---

### Post by andrewski on 2006-09-10
That works great, thanks!  I never thought of using chainloader for not-Windows. :P

And Herman, thanks for the extra info; I would not have figured that out.

---

