---
title: "Can I switch my default boot order?"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-08-27
Hey folks!

I've got Dapper housed on my Ide master.  I do not wish to dist-upgrade it to Xubuntu. Instead, I want to install Xubuntu onto my Ide slave.

After installing, Xubuntu will reinstall grub onto the MBR and end up becoming the default OS upon booting.

How can I reverse this and make Dapper the default OS?

I tryed it once, by booting into Dapper and reinstalling grub, but then I lost Xubuntu (lost my dual-boot option).  

Thanks!

---

### Post by scxtt on 2006-08-27
you can have grub boot any OS listed by "default" simply by changing the line in /boot/grub/menu.lst which says:```
default         0
```change it to whichever entry you want to be default.

---

### Post by randell6564 on 2006-08-27
> **scxtt said:**
> you can have grub boot any OS listed by "default" simply by changing the line in /boot/grub/menu.lst which says:```
default         0
```change it to whichever entry you want to be default.

Hi!  Which menu.list, Dappers or Xubuntu's?  Right now Xubuntu boots by default.  I want Dapper to boot by default, and dapper's menu.list is
[B]## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
[/B]

I believe Xubuntu's will show
hd0,1 or hd1,0, something like that.

I think I'm confused! lol!  Hd0,0 IS what I want, so I'm guessing that it's Xubuntu's menu.list that I want to change correct?

Thanks!

---

### Post by randell6564 on 2006-08-27
Sorry, I posted the wrong part of the menu.list! In Dapper it's default 0, so I want to go into Xubuntu and set it to default 0 Correct?

---

### Post by confused57 on 2006-08-28
Here's how to change the default OS to boot in grub:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

When you install Xubuntu onto your slave drive(hdb1=(hd1,0) in grub), Xubuntu's grub will be written to the Dapper mbr on hda.  The Dapper grub menu.lst entry will probably be toward the bottom of the file under other OS.  Grub OS boot entries start at 0, so the 4th OS entry would be "default 3".

You'd need to edit your Xubuntu menu.lst to make these changes:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```
If you've never used nano, the ^ stands for pressing Ctrl key.

If you want to get adventurous and use Dapper's grub, you could reinstall grub, using the live cd, to the mbr of hda and manually add the entry to the Dapper menu.lst to boot Xubuntu.  If you think you might want to do this, let me know and I'll attempt to walk you through it.

---

### Post by randell6564 on 2006-08-28
> **confused57 said:**
> Here's how to change the default OS to boot in grub:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

When you install Xubuntu onto your slave drive(hdb1=(hd1,0) in grub), Xubuntu's grub will be written to the Dapper mbr on hda.  The Dapper grub menu.lst entry will probably be toward the bottom of the file under other OS.  Grub OS boot entries start at 0, so the 4th OS entry would be "default 3".

You'd need to edit your Xubuntu menu.lst to make these changes:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```
If you've never used nano, the ^ stands for pressing Ctrl key.

If you want to get adventurous and use Dapper's grub, you could reinstall grub, using the live cd, to the mbr of hda and manually add the entry to the Dapper menu.lst to boot Xubuntu.  If you think you might want to do this, let me know and I'll attempt to walk you through it.

Thanks you guy's!  I got it!  I changed 'default 0' to 'default 4'.
That automaticaly highlites hda1 at the grub boot screen. So if I forget, it will count down and boot to Dapper which is what I wanted.

Sorry if this seemed like a stupid question, but I am finally a fulltime Linux user (Windows is in her box, tucked away in a drawer, in the dark and unused where she belongs!)

I've learned so much, and it is totally due to you guy's and this forum!

I alway's thought that it would be cool to have an Ubuntu party somewhere where we could all put a face to eachothers screen names!  "So YOU'RE 'confused57'!  Nice to to meet ya!  Now grab that bat, and the first one to smash that Windoze PC swinging on that tree gets to control the Keg!

Thanks again!

---

### Post by confused57 on 2006-08-28
> **randell6564 said:**
> 
I alway's thought that it would be cool to have an Ubuntu party somewhere where we could all put a face to eachothers screen names!  "So YOU'RE 'confused57'!  Nice to to meet ya!  Now grab that bat, and the first one to smash that Windoze PC swinging on that tree gets to control the Keg!

Thanks again!

Back at ya'...sounds like a good idea to me.

---

