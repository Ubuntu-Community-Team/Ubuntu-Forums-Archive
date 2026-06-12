---
title: "Doesn't even boot from CD"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by afterburner on 2007-04-19
Hi, I downloaded the Ubuntu 7.04-desktop-i386.iso file, and burned it onto a CD, BUT when I put it into the CD-drive, It doesn't boot from it, and therefore I cant install Ubuntu. The machine I tried this one is a Celeron, 1.7GHz, 512 RAM, has a clean windows 2000 pro install on it...

Here is what I did...Downloaded the above-mentioned file, burned it onto a CD as a .iso file...tried to boot from it...nothing...just loads windows 2000 as usual. I DID go into BIOS and change the boot order, so that CD-drive is before hard drive, but the problem still persists. I then thought that maybe I should extract the .iso file, and burn its contents on a second CD...Did that...same problem...for some reason the CD wont boot, and I cant install Ubuntu. 

I then thought that maybe its a problem with my CD-drive, so I tried it on a second computer (p4 2.6Ghz, 2GB ram, has Win XP on it...Same thing with both CDs...they just don't boot for some reason...Nothing happens, except the usual windows startup...Mind you BIOS setting are such, that CD should boot first...But like I said, nothing happens.

By the way, I'm using standard 700MB CDs

What am I doing wrong?
Are there other ways of installing besides the CD?

Thanks

---

### Post by cogadh on 2007-04-19
Did you just burn the ISO to a CD like you were copying a file? If so, that won't work. You need to use a CD burning tool like Nero to extract the ISO image onto the CD. I recommend using a simple tool like IMgBurn:

[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by mikewhatever on 2007-04-19
Can you open the CD in the file browser and check what's on it. If there is just the iso file you downloaded, reburn it, here is how
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29#head-8718146d5b4304ebd1c8234826440128ae10518c](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29#head-8718146d5b4304ebd1c8234826440128ae10518c)

---

### Post by bukwirm on 2007-04-19
EDIT: Or, since two people just said what I was going to say, try that.

---

### Post by bwhite82 on 2007-04-19
Hello, I've found that on many PC's even though you set the boot-order correctly in BIOS, that the PC will still not boot from the CDROM drive unless you press one of the F-keys. Whichever F-key your PC requires to get to a boot-menu, you'll have to figure out yourself. For example, my Dell PC requires F12 to be pressed right when I power it on where it takes me to a boot menu where I can then select "Boot to CDROM".

In many cases, your PC will let you know which key you need to press, it *quickly* displays it right when you power it on, sometimes this isn't the case and it will not hurt anything to simply try hitting all of the F-keys. I hope this helps you out.

---

### Post by Laughed on 2007-04-20
Before i break everything on my desk in frustration I'll submit to noobville status.

There is no ISO in the download. I've searched everyfile. 

I've copied these files onto (several) blank discs, none of which boot. I've used Nero to copy the files onto a bootable CD. Nothing. Well not exactly, it boots up into DOS and is completely useless. I've used the program suggested to burn image put no files are available to burn... 

Oh yeah, and I certainly tried all your boot order sequences before coming to this forum.

So in terms a rere can understand, what gives.

---

### Post by cogadh on 2007-04-20
What did you download? The ISO file _is_ the download, it should be the only file you get.

---

### Post by Laughed on 2007-04-20
Thats what I orgnially thought, but burning this image doesn't copy any files to the disk. 
What should I be using to view the ISO. 

Winrar is my default archiver and is displaying the file. When I use InfraRecorder to burn an Image I select the winrar folder as it is the only one available, but the cd remains blank and unbootable. So I tried opening the archive and copying the files onto a bootbale cd with nero. no luck there either. 

Should I be using another program to view this archive (i cant imagine so).

This is my second download of this program.

---

### Post by lindkvis on 2007-04-20
You are not really listening here. You have to use a specialised tool to burn the ISO image.

An iso image contains much more information than just the files in it. Extracting the files and burning them **will not work**. Also, simply burning the iso onto a CD **will not work**.

The only thing that will work is to use a specialised tool such as imgburn suggested by a different poster.

---

### Post by cogadh on 2007-04-20
An ISO is not an archive, it is literally an image of what the CD should look like that is in a format that can be interpreted by specific CD burning software. You don't open it and extract files from it, your CD burning software "reads" it and lays down the tracks on the CD as the ISO tells it to. Once the tracks are laid down, the CD is bootable. 

I am not familiar with InfraRecorder, but if you have any commercial burning software like Nero, it already will recognize the ISO format and will burn it correctly. If you don't have something like Nero, then I recommend a simple, purpose-specific burning software like ImgBurn (see my post above). The only thing ImgBurn is made to do is correctly burn images. It is a simple insert CD > select image file > click "Go" process that has never failed me.

---

### Post by Laughed on 2007-04-20
To lindkvis: So the InfraRecorder app which is suggested on [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) is just for laughs. Thanks I get it. Btw, now that you've broken your cherry, please actually add something of value to your posts, like cogadh for example.

To Cogadh:I gave Nero another spin around the block and now have a bootable disk. 

But now I have to move onto other threads since ubuntu wont start, pc hangs on a black screen.

thanks

---

### Post by afterburner on 2007-04-20
Thanks guys, I successfully created a bootable CD this time around...Turned out I had a faulty download of the iso image.

---

### Post by Laughed on 2007-04-20
This blank screen is a driver issue with my x800 ATI card. For a work around see [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

---

