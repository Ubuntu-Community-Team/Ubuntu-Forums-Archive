---
title: "help installing Ubuntu 7.04"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by for3ver on 2007-10-14
Hi I am trying to install Ubuntu 7.04 even tho 7.10 comes out in 4 days so should I wait and will it even work because I can't get 7.04 to work :(

Basically I got a Linux Ubuntu 7.04 disc with a magazine and when I put it in my computer and boot from disc I can see the linux menu options. Which are:
Start or install Ubuntu
Start Ubuntu in safe graphics mode
Install with driver update CD
Install in text mode
Install a server
Text mode install for manufacturers
Install a command-line system
Check CD for defects
Memory test
Boot from first hard disk

I tried the first option (Start or install Ubuntu) and the Ubuntu loading progress bar came up and eventually i think it finished but then it went to a black screen and my comp frooze :confused:
I then restart and clicked the second menu option (Start Ubuntu in safe graphics mode) and the Ubuntu progress bar finished loading and then a dialog on my screen came up saying "input not supported"

My monitor is an ACER AL1714..

My graphics card is a Raedon 9200
My mobo is an ASUS (i forgot the exact model)


Anyone know how i can get Ubuntu working and is my graphics card good enough to have the 3D effects?

How can I see if my 3D card will work? If I need to install the restricted drivers where do I get them from and would I need to install them on windows and then on Ubuntu or just Ubuntu.. I am a bit confused..

Here is another question (kinda of topic and thinking ahead)..: If i install photoshop on windows xp will it work on Ubuntu or do i have to install this on both operating systems?

someone has also recommend i try installing this: [http://wubi-installer.org/](http://wubi-installer.org/)
I am not sure what to do..

---

### Post by logos34 on 2007-10-15
Try text mode install next.  

If and when you complete the install successfully and you are able to load the desktop go to System>Admin.>restricted drivers manager and enable your ATI graphics that way.  Or use Automatix.

More on 3D & compiz-fusion:
[https://help.ubuntu.com/community/CompositeManager/CompizFusionATI](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI)

Wubi installs ubuntu inside widows as a folder which mounts as a loopback filesystem.  It's aimed at people who just want to try out ubuntu and are scared of dual-booting/partitioning.  

I'm not sure you can run Adobe Photoshop on linux with Wine...Maybe Crossover Office will allow you to.

---

### Post by for3ver on 2007-10-15
edit: I have raedon 9200

---

### Post by for3ver on 2007-10-15
can i install adobe photoshop on windows and use it on linux Ubuntu or do i have to install it on Ubuntu seperatly ? So i have to install it twice?
this goes for every program.. if i install nero on windows do i have to install it again on Ubuntu ?

I have got another internal harddrive with just pictures and songs on.. Can i use this in Ubuntu or do i have to format it so i can then view the pictures and play songs when using Ubuntu??

---

### Post by logos34 on 2007-10-15
you can't install Photoshop on linux because there's no linux version...and I'm not even sure you can run the windows version via crossover office--you'll have to google for the details on that.   There is Nero Linux 3 (costs $) but K3B is superior (and free).

For those windows programs that you can run in linux via Wine, you just open them from their location on the windows partition.

---

### Post by for3ver on 2007-10-15
what a dirty mission. I was doing the text installation and i partitioned my c drive leaving 10gb free for windows then i got to the grub stage.. and i figured i should exit the ubuntu installation because i need to use photoshop and dreamweaver.. and it said if i exit now my comp might not be in a stable condition which it isnt so i am having to install xp again..

guess i will try wine..

---

