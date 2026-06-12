---
title: "Encrypted /home fiasco"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-02-18
So I did a fresh install of Alpha 4 yesterday (I had been up to date on updates, but needed a fresh system for some testing) and now my encrypted /home won't open. I've tried reinstalling again and again, tried running 'ecryptfs-mount-private' to which I get the response "Encrypted Private is not setup properly".

This is not *horribly* a big deal, b/c I've got most of my files backed up. But there were a couple almost-mission-critical files I didn't snag. Is there any way to open this guy back up? or am I SOL?

---

### Post by scaine on 2009-02-18
From :
[http://www.ubuntu.com/testing/jaunty/alpha4](http://www.ubuntu.com/testing/jaunty/alpha4)

There are two entries which could trip you up :
> 
Known Issues

[LIST]
[*]Migrating documents and settings during installation will not work when the home directory encryption option is enabled. [325257]("https://bugs.launchpad.net/bugs/325257")  	
[*]Encrypted 	Home Directory support has been integrated in Alpha4, on both desktop 	and server installs. While home directory encryption includes 	encrypting filenames on the Desktop Installation, filename encryption 	is broken on the server installation. Server systems which need 	encrypted home directories with filename encryption will need to be 	installed with Alpha 5 or later. [326184]("https://bugs.launchpad.net/bugs/326184")  	
[/LIST]


Either of those relevant?

---

### Post by zaomaster on 2009-02-18
Jam, that might be what's going on, as the previous install of Jaunty I was using was Alpha 3.

Does anyone have an iso of alpha 3? It's nowhere to be found on the ubuntu site (for obvious reasons I suppose).

---

### Post by simon_wrafter on 2009-02-18
check this site: [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

---

### Post by zaomaster on 2009-02-18
Thanks for the help, but that just takes me to the Alpha 3 page. I've been there, and when you try and download the iso it takes you to the cdimage.ubuntu.com site, where they no longer have the alpha 3 iso.

---

### Post by eyelessfade on 2009-02-18
You can't get it out using a 8.10 then?

---

### Post by zaomaster on 2009-02-18
You know, the thought had crossed my mind, but I've formatted the drive with ext4. Darn me and my incessant desire to be on the bleeding edge. 

What I'm trying now, which will require starting another thread (perhaps), is to install /home on a bit of free unpartitioned spaced I had on the drive. Once I can get logged in and everything then I'll need to know how to mount an encrypted partition so that I can move the info off.

Thank you all for your help.

---

### Post by Archmage on 2009-02-19
Do you have a seperate home-partition, than this should be pretty easy:

Install new, use a different partition with encryption with the same password and after the installation change the home-partition in fstab to the old home-partion.

I can't gurrante that this will work, but I'm pretty curious about the outcome. ;)

---

### Post by zaomaster on 2009-02-19
You know, that's a great idea. I don't know if it will work, but I'll sure try it.

---

### Post by zaomaster on 2009-02-19
Well, it mounted as home, but it didn't unlock any of the files. Any idea as to why this might happen?

---

### Post by Archmage on 2009-02-20
Did you reinstall with a encrypted home-partition? I think if you do a unecnrypted install it wont install all the nessacary packages.

I would really appriacate if you find a solution, since my ext4 also just decided to stop working. :(

---

### Post by zaomaster on 2009-02-20
> **Archmage said:**
> Did you reinstall with a encrypted home-partition? I think if you do a unecnrypted install it wont install all the nessacary packages.

I would really appriacate if you find a solution, since my ext4 also just decided to stop working. :(

I did re-install with an encrypted partition. The closest I could get was that it opened the partition, but the file name were all still encrypted. So I could open some files (.txt, .xml), but none of the binary type (.doc, .odt, etc). 

Oh well, I've done what I can, and I've also redone all the work that I lost, so... wipe the drive it is!

---

