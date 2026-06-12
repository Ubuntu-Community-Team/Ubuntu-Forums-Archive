---
title: "Multi-Booting XP/Linux"
date: 2004-12-29
forum: Installation &amp; Upgrades
---

### Post by Sapper2ID on 2004-12-29
I now run a dual-boot with XP, one for games, one for multi-media on my 80gb master. Ubuntu is on my slave 40gb with 3-13 gb partions. I would like to load other linux OS's to try. Lycoris, Mandrake maybe. Will GRUB handle this? What conflicts can I expect? 
Love this Linux thing and am learning much. Not sending my money to Redmond is a plus if I can learn how to use this system.

Very friendly and helpful forums make this much easier, Thanks

---

### Post by TravisNewman on 2004-12-30
It *should* all work. Note, I did say should. I'd suggest setting up another partition of about 2 gigs to try out other distros, so you can keep wiping it and starting over. Grub might get confuzzled sometimes, not sure, but it should always pick up the windows partition.

---

### Post by Sapper2ID on 2004-12-30
Thanks

 I'm doing this to learn, the worst that'll happen is I'll have to wipe and reload everything, oh well!

---

### Post by jbh on 2004-12-30
I dual-boot XP/Ubuntu 64 and have had no problems. I had to manually edit menus.list in the boot/grub directory and uncomment out the Windows options to get it to boot back into XP but other than that everything is perfect. Note I have 2 seperate HDs (1 for Xp/1 for Linux) that could be a plus. 

I only use XP for Half-Life 2/DOOM 3... other than that XP is useless until I can get a decent linux CounterStrike: Source version :D

---

### Post by sfm40 on 2004-12-31
ID software has released the Doom3 port for Linux!

You can find it here: [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)


Scotty

---

### Post by TravisNewman on 2004-12-31
And Cedega runs HL2 flawlessly in linux as long as you have windows fonts in your virtual drive. AND CounterStrike Source. So Windows XP has now been rendered useless for you, go ahead and delete it ;)

No, in all seriousness you should try out HL2, CSS, and Doom3 before completely removing Windows, especially since you use 64 bit... there could be some problems there, I dunno.

---

### Post by physician97 on 2005-01-02
[QUOTE=Sapper2ID]I now run a dual-boot with XP, one for games, one for multi-media on my 80gb master. Ubuntu is on my slave 40gb with 3-13 gb partions. I would like to load other linux OS's to try. Lycoris, Mandrake maybe. Will GRUB handle this? What conflicts can I expect? 
Love this Linux thing and am learning much. Not sending my money to Redmond is a plus if I can learn how to use this system.

Very friendly and helpful forums make this much easier, Thanks[/QUOTE]

You can always try the live CD's as well.  SUSE, Mandrake and Knoppix all have a live CD which can be downloaded, burn .iso image and then play with it in the CD/DVDrom without installing it.  It runs from RAM and off CD. I know that the SUSE requires some 256 megs of RAM, and the knoppix doesnt require much - less than 50 megs I believe.  Theres another distro called mepis too (think thats the name).  hth...doc

---

### Post by Sapper2ID on 2005-01-05
I think I can figure out how to edit the menu/grub thing. One stupid ? though, how do Uncomment something? Don't quite get that.

---

### Post by crane on 2005-01-05
[QUOTE=Sapper2ID]I think I can figure out how to edit the menu/grub thing. One stupid ? though, how do Uncomment something? Don't quite get that.[/QUOTE]
 In linux config files when a line starts with the # symbol it is said to be commented out.
So just remove the # from the line you want to uncomment usinf ypur favorite text editor!

Some file need to be edited as root to uncomment and change things.

You can do this by using  

sudo gedit /path/to/file

---

