---
title: "From Mandrake 10.1 to Ubuntu... [HOW?]"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by bufa on 2005-02-18
Well... I've tested mandrake and it didn't like me...
Then I want to Install Ubuntu, but in the same "partition" that mandrake... how can I "uninstall" mandrake to Install Ubuntu?

Woooow... horrible english here.... ](*,)  :^o

---

### Post by Seandq on 2005-02-18
[QUOTE=bufa]Well... I've tested mandrake and it didn't like me...
Then I want to Install Ubuntu, but in the same "partition" that mandrake... how can I "uninstall" mandrake to Install Ubuntu?

Woooow... horrible english here.... ](*,)  :^o[/QUOTE]
 [IMG]http://shots.osdir.com/slideshows/156/6.gif[/IMG]

At that screen, "manually edit the partition table". Then go into each partition, edit them and instead of something that I believe says "leave unchanged", highlight that one, click enter and change to "format" each partition.

The way Mandrake does it, your bigger one would be / and the smaller one /home.

---

### Post by nikopol on 2005-02-19
[QUOTE=Seandq][IMG]http://shots.osdir.com/slideshows/156/6.gif[/IMG]

At that screen, "manually edit the partition table". Then go into each partition, edit them and instead of something that I believe says "leave unchanged", highlight that one, click enter and change to "format" each partition.

The way Mandrake does it, your bigger one would be / and the smaller one /home.[/QUOTE]
 But I assume you're ok with wiping your home folder? This will destroy the contents of it so be sure to have it backedup!

---

### Post by bufa on 2005-02-19
[QUOTE=nikopol]But I assume you're ok with wiping your home folder? This will destroy the contents of it so be sure to have it backedup![/QUOTE]
 I'm really noob... but I'll try... anyway I've got my "liveCD"... so I can ask it it fails... :D and what about the "boot"? lilo or something like that... :rolleyes:

---

### Post by nikopol on 2005-02-19
[QUOTE=bufa]I'm really noob... but I'll try... anyway I've got my "liveCD"... so I can ask it it fails... :D and what about the "boot"? lilo or something like that... :rolleyes:[/QUOTE]

To boot it uses Grub which is close enough to lilo - it should auto-configure itself with that. 

Suppose your HD is like this
/ 6 Go (/dev/hda1)
/home 4Go (/dev/hda2)
Swap 512 Mo (/dev/hda3)

you want to format the / partition and set the /home partition to be kept and used as a the home directory... That way you will lose Mandrake but keep your files in the home directory.

---

### Post by bufa on 2005-02-19
[QUOTE=nikopol]To boot it uses Grub which is close enough to lilo - it should auto-configure itself with that. 

Suppose your HD is like this
/ 6 Go (/dev/hda1)
/home 4Go (/dev/hda2)
Swap 512 Mo (/dev/hda3)

you want to format the / partition and set the /home partition to be kept and used as a the home directory... That way you will lose Mandrake but keep your files in the home directory.[/QUOTE]
 ok, I did it!!!...but...(don't kill me 4 this cuestion...)

Which are the Username and Pass???...

I'm gonna read the "faqs" and all that staff...but if u know it... 'cause I got to the "orange page" of the login and I don't know what to insert... :(

---

### Post by bufa on 2005-02-19
[QUOTE=bufa]ok, I did it!!!...but...(don't kill me 4 this cuestion...)

Which are the Username and Pass???...

I'm gonna read the "faqs" and all that staff...but if u know it... 'cause I got to the "orange page" of the login and I don't know what to insert... :([/QUOTE]
 at laaast!!... I'm a happy Ubuntu noob user! :D

---

### Post by nikopol on 2005-02-20
[QUOTE=bufa]at laaast!!... I'm a happy Ubuntu noob user! :D[/QUOTE]

So I assume you've sorted out the username and password? You should have set this when you were installing. If you didn't write them down & can't remember, I'm afraid that you'll have to a reinstall (there used to  be a way around this on some other linux distros but I can't remember off-hand)...

---

### Post by bufa on 2005-02-20
[QUOTE=nikopol]So I assume you've sorted out the username and password? You should have set this when you were installing. If you didn't write them down & can't remember, I'm afraid that you'll have to a reinstall (there used to  be a way around this on some other linux distros but I can't remember off-hand)...[/QUOTE]
 nono, luckly I could remember... :D

[audio problemmm :(](http://www.ubuntuforums.org/showthread.php?t=16204)

---

### Post by iakudi on 2005-02-27
[QUOTE=bufa]Well... I've tested mandrake and it didn't like me...
Then I want to Install Ubuntu, but in the same "partition" that mandrake... how can I "uninstall" mandrake to Install Ubuntu?

Woooow... horrible english here.... ](*,)  :^o[/QUOTE]


Im new to this but I did the same as you. Boot off the cd rom, when it comes to installing on the HDD (see the pics from the other responses) you can:

1) Wipe the WHOLE disk
2) Manually configure

option 1 is easy as it auto does it all.

With option do find you linux partitions (I had 2 windows ones as well) press enter on the first linux partion and choose delete (use tab to get to the go back option). In the same way remove any other linux partons, once you have your free space you can use the auto options and Ubuntu allows around 512MB SWAP and the rest for the linux os. I personally preferred 1GB swap.

So basically you remove any linux partions, and in the free spce let Ubuntu auto partition...its easy.

If I can do it so can my grandma !!

ciao

Ish

---

