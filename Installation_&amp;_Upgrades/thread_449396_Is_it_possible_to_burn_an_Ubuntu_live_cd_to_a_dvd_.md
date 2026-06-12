---
title: "Is it possible to burn an Ubuntu live cd to a dvd with additional files?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by isagani on 2007-05-20
Can I burn an Ubuntu live cd .iso into a dvd with extra files (documents, text, anything else I want)? If yes, how do I do it? Of course it needs to be bootable. Also, when inserted within a different os, the "extra" stuff should be accessible.

I'm giving out DVDs to people and I think it would be great if besides the files I need to give them, they would also have a live Ubuntu installer. There's so much space in a dvd that I think this would be a really great way of spreading ubuntu.

Thanks! :)

---

### Post by mikewhatever on 2007-05-20
Hope you do not put some ugly commercials or spyware there.
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by isagani on 2007-05-20
Of course not :). I think you misunderstood me. I conducted a training program in our school for working with Digital Signal Processing. I have lecture slides and the software used in the training. I need to give these files out to the students and thought it would be great if they get ubuntu with it too.

Sorry for not being clear enough. I hate bloatware too :)

---

### Post by isagani on 2007-05-20
Oops. I'm sorry, I don't think UCK is what I'm looking for. I just want to add files to the ubuntu cd. In a separate folder. Like documents, installers, readme's, videos, while still making a bootable disc.

Is this possible?

---

### Post by Xbehave on 2007-05-20
i think so but im not sure how much space is left on a ubuntu cd

---

### Post by zvacet on 2007-05-20
I´m not sure if it works but you can try APTonCD.It is in Feisty.

---

### Post by bluenova on 2007-05-20
Have you had a look at Reconstructor?

[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by isagani on 2007-05-20
The reconstructor program allows you to add repositories and change the look of the live cd. What I want is just to add some files along with the live cd. Absolutely no change in ubuntu. The files will just be piggy-backing on the live-cd(dvd). Thanks for all the help.

---

### Post by SgtDude on 2007-05-21
I've been fiddleing around with reconstructor today.  Within Reconstructor you can open a terminal (the button's on the lowwer left corner of the Reconstuctor window).  This terminal gives you root access to the live CD you'll be building.  From there you can *wget* files from a web source or use other command line tools to get files from other sources.  You'll probably want to put your files in *programs*, but I don't think it'll hurt Ubuntu if you drop them in their own folder under /

A few things you should be aware of:

I don't think the chroot environment you'll be in in that terminal will allow you to just copy files from the machine you're running on into the "cd-to-be".  You'll have to do a little research and figure out what command-line tools will give you network access to the files you're looking for.  If the files can't be anywhere but on the machine you're building the CD on, you'll probably have to look into installing NFS, SAMBA, Apache, or and FTP server on your machine to get network access.

If I'm wrong about this, someone please correct me.

Annother method that might work (I havn't tried it) is to copy all the files on the Ubuntu CD someplace on your HD, then copy in the files you want to add, then burn all the files onto a DVD (FYI, this DVD won't boot), then use that DVD as the source DVD in Reconstructor to rebuild a new DVD that will actually boot.  If this works, it's a much simpler solution to your problem.

Good luck.  Please post here if either of these methods works.

---

### Post by isagani on 2007-05-21
Thanks! I'll definitely post here if I get either method to work. Thanks for all the help. I'm not really skilled in using the terminal, but I guess this would be a great oppurtunity to learn a little (like "chroot", I'm completely ignorant what this means :D)

---

### Post by SgtDude on 2007-05-22
Don't quote me on this, but I think chroot means "Child Root".  Basically you're kind of emulating annother linux machine from within the linux machine you're physically working on.  In this case it gives you root access to the LiveCD so you can do things like install additional software, or in your case, add files to the filesystem.

And I was thinking about this after I posted.  You don't actually have to waste a DVD burning that first disk, you can use Gnomebaker or K3B to create an ISO containing the LiveCD files and your additional files, then use that ISO as the source disk for Reconstructor.

I know the first method will work, I'm not sure about the second one.  If I get some time today I'll try it out (unless you beat me to the punch).

---

### Post by isagani on 2007-05-22
You're probably gonna beat me to it. I'll be trying it out tonight. I'm a little busy right now. :)

---

### Post by SgtDude on 2007-05-24
I can't believe I didn't think of this sooner.

Adding files should be easy:

On the Third page of the reconstructor GUI you can decompress the contents of an Ubuntu LiveCD into the folder of your choice (default is /home/yourusername/reconstructor).  Once you've done this you can close reconstructor, add the files to /home/yourusername/reconstructor/root/ (or any folder beneath that).  Then you can open Reconstructor again, go through the motions but leave those three boxes on the third page unchecked to prevent overwriting of your newly constructed liveCD filesystem, and build a new LiveCD with whatever you added.

Sorry I didn't think of this sooner.

---

### Post by castoroil97 on 2007-07-01
how do i get reconstructer?

thanks

---

### Post by amgupt01 on 2007-08-05
castoroil97:
You can get Reconstructor from [http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by starscalling on 2007-10-20
should be able to open iso with file-roller make a dir in there and just drop in files

---

### Post by mudshark30 on 2007-10-27
burn your iso to a dvdrw. Don't finalize the disk.  afterwards you can add files. If you don't specify a location they will be in /cdrom.  This works for me.

---

