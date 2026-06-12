---
title: "edgy doesn't fully boot anymore.  because of gnome update?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by insert_name_here on 2006-12-22
Just now, my Edgy stopped booting fully.  It gets to the login screen, and when I enter my username and pw, the screen turns purple, then turns off, then returns to the login screen.

This happens if I try to boot to Gnome or Xgl/Beryl.  I did just install the new gnome 2.16 in my last session before it failed.

I can boot to "recovery mode".  My specs, if they matter, are: Lenovo T60, 1 gig RAM, 100gb HDD, Ati Mobility radeon x1400, etc.

What do I do to fix this?  If I can avoid it, I would like to not reinstall Ubuntu...

---

### Post by insert_name_here on 2006-12-23
I did some (more) research and found that if I just deleted something large (like a kubuntu iso) it would boot.

It did boot correctly, and is fixed, btw.

---

### Post by 3dimentia on 2006-12-25
ok, after a LONG friggin time of trial and error with Grub, I FINALLY got my ubuntu back.  However, I still need my windows partition to work correctly.  Thats initially what screwed me over.  Windows installed, over wrote my MBR, and I could not get grub/;ubuntu to come back.

Well to make the story short, I got grub working again, have ubuntu again, but I think i screwed the windows partition.  I REALLY don't want to re install windows again only to have it blow away my configuration and have to go through that few hour long mess again.

So here is what fdisk -l lists.

/dev/sda1 boot hpfs/ntfs
/dev/sda2 linux (root)
/dev/sda3 swap
/dev/sda4 w95 etd (LBA)
/dev/sda5 linux
/dev/sda6 unformatted
/dev/sda7 unformatted

Don't flame me for doing this to my HDD ;)  I know its not as elegant as having 2 hard drives, but this drive is huge, and hey, I installed linux only a week or so ago.  Anyway, as I said, I have grub working and it boots into ubuntu just dandy now, however I cannot get it to boot to windows.  I checked out the menu.lst file, and as you probably already guessed, no windows info.  So this is where im stuck.  I'm not sure what commands need to go into there for the windows partition to boot.  Can anyone assist with this?  Any help is greatly appreciated!

thanks much

---

### Post by 3dimentia on 2006-12-25
wouldn't you know it, I got it to work again.  I always seem to do that right after I ask the hard questions.  I just put in:


title		      Windows 95/98/NT/2000
root		    (hd0,0)
makeactive
chainloader	+1

for my windows stuff and now both work, YAY

---

### Post by bulldog on 2006-12-25
You see? it isn't so hard to use GRUB after all,you only have to understand it a little :D 

Nice you find it by yourself though.

---

