---
title: "Vista doesn't run the iso"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by ethan33 on 2010-02-14
I downloaded Ubuntu 9.10 and burned it to a cd, but I can't get it to run on my vista computer. 

I originally tried it multiple times on a computer running xubuntu, but it wouldn't load from the disk. Not knowing much about linux in general I mostly chocked it up to being normal, so I decided to make sure by trying to run it on my windows pc only to find out it wouldn't run on that computer either. It just brings it up as a file folder, with the .iso file in it. I then re downloaded it to be sure that it wasn't just corrupted on download. Then I burned it to the disk again, and tried to run it, but it still didn't work. My computer is set to ask me what I want to do when any sort of data container is hooked into my computer, but it seems to override that and run it with a folder anyways. Does anyone know what the problem is, and how it can be remedied?

On a side note I used Roxio Creator DE, version 10, which came with my computer, to burn it to the disk. Is there, perhaps, a known issue with that?

---

### Post by night_fox on 2010-02-14
1) Make sure you burn it as a "data disk" or something. This is different to simply copying the .iso as a file.

2) You dont run it from within windows. As soon as you switch the computers power on, you have to quickly press a key to get a "one time boot menu", or edit the bios settings, so the computer boots from the CD and NOT THE HARD DISK.

Hope that helps.

---

### Post by Mencarta on 2010-02-14
If you see the iso file when you view the contents of the cd then it wasn't burned correctly. I recommend [InfraRecorder]("http://infrarecorder.org/").

---

### Post by ubudog on 2010-02-14
Yeah, you can't just copy/paste the .iso onto the cd.  You have to use a .iso burning software.  I think there is one for windows called "MagicISO" or something.  Hope you enjoy Ubuntu!

---

### Post by Mencarta on 2010-02-14
> **night_fox said:**
> You dont run it from within windows.

Actually, you can. The wubi.exe file launches a window that allows you to install it replacing windows or install it creating a dual-boot.

---

### Post by ubudog on 2010-02-14
> **Mencarta said:**
> Actually, you can. The wubi.exe file launches a window that allows you to install it replacing windows or install it creating a dual-boot.

True.

---

### Post by Mencarta on 2010-02-14
Since your here mine helping my problem? [Installation Freezes]("http://ubuntuforums.org/showthread.php?t=1406967")

---

### Post by ethan33 on 2010-02-14
> **night_fox said:**
> 1) Make sure you burn it as a "data disk" or something. This is different to simply copying the .iso as a file.
Roxio has a special tab for making a data disk that I made sure was pressed.

[QUOTE=Mencarta]If you see the iso file when you view the contents of the cd then it  wasn't burned correctly. I recommend [InfraRecorder]("http://infrarecorder.org/").     [/QUOTE]
I was concerned about that. I even started looking for alternatives, so thanks for the recommendation. I'll look into it immediately. 

[QUOTE=ubudog]Hope you enjoy Ubuntu!     [/QUOTE]
Me too. I'm hoping this will be my first linux experience without having wireless troubles.

---

### Post by oldos2er on 2010-02-14
The ISO file needs to be burned as an image, not data. See [http://psychocats.net/ubuntu/burn](http://psychocats.net/ubuntu/burn)

---

### Post by ethan33 on 2010-02-14
> **oldos2er said:**
> The ISO file needs to be burned as an image, not data. See [http://psychocats.net/ubuntu/burn](http://psychocats.net/ubuntu/burn)
Thanks for the link to the tutorial. I'm currently erasing the disk. It looks like it's going to take a while.

---

### Post by night_fox on 2010-02-14
> Actually, you can. The wubi.exe file launches a window that allows you to install it replacing windows or install it creating a dual-boot.

My bad

> The ISO file needs to be burned as an image, not data. See [http://psychocats.net/ubuntu/burn](http://psychocats.net/ubuntu/burn)

My bad again.

](*,)

I should probably keep my mouth shut!

---

### Post by Mencarta on 2010-02-14
Don't worry, everybody makes mistakes. ;)

---

### Post by phillw on 2010-02-14
The Community Documentation has a nice how-to burn a CD on pretty much anything except the toaster you use for breakfast !!

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Regards,

Phill.

---

### Post by ethan33 on 2010-02-14
I figured out that Roxio has the option to burn an image under the copy menu, which doesn't make sense to me, but problem solved.

I would like to thank all of you for your speedy, and very helpful responses.

---

