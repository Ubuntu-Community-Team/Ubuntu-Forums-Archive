---
title: "live CD with Android Studio for offline installation"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by skarosg3 on 2015-05-28
Hi all,
I am teaching an Android course on a school, but they have Windows XP and things dont seem very well! we have major problems running the apps (actually only 4 out of 15 computers can actually launch the apps on the emulator, the rest just launch the emulator with no app running). 
I was thinking to use a live cd and run Android studio from there. This would take some time to set up for all the computers, but I trust ubuntu will do the job million times better.

My question, is it possible to "add" android studio on a live cd so it can be installed at the same time? my quess is no, so the second question would be

Is it possible to add a full version of Android studio on the same DVD with the ubuntu ISO and execute this with a single command with out the need of internet?

Or maybe any other way that would effectivly reduce the installation time for both ubuntu and Studio?

Thanks, ilias

---

### Post by grahammechanical on 2015-05-29
I think that what you are wanting to do is create an offline repository. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I also suggest that you look at Ubuntu Make. It is a command line tool that makes it easy to install development software such as Android Studio & Android SDK as well as other development platforms. New development platforms are being added all the time.

[https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

[http://blog.didrocks.fr/](http://blog.didrocks.fr/)

If you do a web search for "Ubuntu offline repository" you will find other suggestions that may help you. You may store the repository on a hard disk to start with. Then when it is complete copy it onto a CD to be used as an offline repository once Ubuntu has been installed on each machine in the usual way.

Regards.

---

### Post by Bucky Ball on 2015-05-29
Or ...

Why not install on one machine, tweak that to how you want it, then create an .iso of the install and install that on all the machines? Your Ubuntu spin can have whatever you like on it then. You could certainly also incorporate your offline repository as well, if you needed to.

[https://duckduckgo.com/?q=create+iso+of+current+install+ubuntu&ia=qa](https://duckduckgo.com/?q=create+iso+of+current+install+ubuntu&ia=qa)

There's lots of ideas there. I did it once some years ago. I'll see if I can find how I did it. Clonezilla can create an .iso of your current partition, but you may need to tweak with grub on the other machines to get it running. Not sure about if you are using EFI. 

Create recovery ISO with Clonezilla:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Just another suggestion. ;)

---

### Post by skarosg3 on 2015-05-29
> **Bucky Ball said:**
> Or ...

Why not install on one machine, tweak that to how you want it, then create an .iso of the install and install that on all the machines? Your Ubuntu spin can have whatever you like on it then. You could certainly also incorporate your offline repository as well, if you needed to.

[https://duckduckgo.com/?q=create+iso+of+current+install+ubuntu&ia=qa](https://duckduckgo.com/?q=create+iso+of+current+install+ubuntu&ia=qa)

There's lots of ideas there. I did it once some years ago. I'll see if I can find how I did it. Clonezilla can create an .iso of your current partition, but you may need to tweak with grub on the other machines to get it running. Not sure about if you are using EFI. 

Create recovery ISO with Clonezilla:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Just another suggestion. ;)
That would be great! but can i do this with live CD? could create my installation under live CD and install it as live CD. I will not be able to install ubuntu on the machines, i already checked :(
> **grahammechanical said:**
> I think that what you are wanting to do is create an offline repository. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I also suggest that you look at Ubuntu Make. It is a command line tool that makes it easy to install development software such as Android Studio & Android SDK as well as other development platforms. New development platforms are being added all the time.

[https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

[http://blog.didrocks.fr/](http://blog.didrocks.fr/)

If you do a web search for "Ubuntu offline repository" you will find other suggestions that may help you. You may store the repository on a hard disk to start with. Then when it is complete copy it onto a CD to be used as an offline repository once Ubuntu has been installed on each machine in the usual way.

Regards.

I will look into that. in deed offline repository seems like the solution i was looking for. thanks.
 will let you know how it will go

---

### Post by Bucky Ball on 2015-05-30
Yes. You could clone as many USB sticks as you like (rather than CDs, but you could use that too, although a full Ubuntu install will not fit on a CD). Install on one machine, tweak to your liking, use Clonezilla (there are other apps to do this to from memory) to clone an .iso of your install to a (or many) USBs. 

Good luck however you swing. ;)

---

### Post by grahammechanical on 2015-05-30
I was also thinking that if these machines do not have an internet connection or it would be unwise or too expensive for them to have an internet connection, then in Software & Updates we can set a CD-Rom as a repository. An offline repository on a DVD/USB that is updated at regular intervals could then be used to update offline other machines.

Regards.

---

### Post by skarosg3 on 2015-05-31
> **Bucky Ball said:**
> Yes. You could clone as many USB sticks as you like (rather than CDs, but you could use that too, although a full Ubuntu install will not fit on a CD). Install on one machine, tweak to your liking, use Clonezilla (there are other apps to do this to from memory) to clone an .iso of your install to a (or many) USBs. 

Good luck however you swing. ;)
I do not have the ability for a new ubuntu installation. i was hoping i can do this using live CD, but it turns out that live cd installation doesnt allocate much of free hard drive space resulting not to be able to instal Android Studio. I will give it a try to do a virtual box ubuntu installation (under my ubuntu installation :) ), install Android Studio and get the image of that.
If that will not work i will go for the offline repository
> **grahammechanical said:**
> I was also thinking that if these machines do not have an internet connection or it would be unwise or too expensive for them to have an internet connection, then in Software & Updates we can set a CD-Rom as a repository. An offline repository on a DVD/USB that is updated at regular intervals could then be used to update offline other machines.

Regards.

@grahammechanical The problem is not that there is no internet connection. The problem is that i dont have the luxury of the time to wait for the Android Studio to download and install for all the computers.

thanks

---

