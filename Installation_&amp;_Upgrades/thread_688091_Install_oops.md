---
title: "Install oops"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by mistweaver4 on 2008-02-05
Hey All!

Im new to this so please be patient with me.

I have recently installed ubuntu on my laptop as a dual boot with windows XP. when i installed it i wanted to partition the HDD 70%/30% with ubuntu on the 70% side. Sadly, it ended up on the 30% side.

my question is how can i undo the install and the partition so i can re-install it the way i want without messing up windows?

thanks for any assistance!!

---

### Post by roachk71 on 2008-02-05
Oops, Indeed... :(

If Windows was already installed in the 30% partition, that Windows installation is already gone for good, unless you have either the Windows installation CD or recovery discs (and hopefully have backed up your files.)

If you have the Ubuntu Live CD, boot into that and try using its partition editor to find out your disk layout, then post that here. I'm hoping as you are that you haven't wiped out the other OS.

Perhaps you've simply resized your NTFS partition to 70%, instead of 30%; in that case, you could try to reinstall Ubuntu and resize the XP partition again. Windows XP is much more forgiving than Vista regarding these issues...

Oh, and don't forget to resize the other partition to match, allocating about 2GB for swap.

---

### Post by forestpixie on 2008-02-05
2 ways to deal with this either resize the partitions without uninstalling or delete partitions and start again

boot up with the livecd - there is a partition tool include - can't remember wher it is exactly - either in system tools or admin >system.

Once it's booted you'll have a graphic representation of your drive

resize the windows partition to suit, then you'll need to move the ubuntu partition to the left to the edge of the win partition, then you can resize the ubunut one to take up the slack.

OR - resize the win partition, delete the partitions ubunut made during install and then reinstall to the empty area

Make sure you have defragged win and that you've still got the backups you had before you started the install :)

I'd go for the first option myself.

When you're using the partition tool - do each step seperately and apply changes before you do next

Good luck

---

### Post by mistweaver4 on 2008-02-05
windows is still there

i just messed up with where i put the partition. i slid the graphical slider the wrong way when i chose where to set it.

right now everything runs fine. 

i guess basically i just want to move the partition to give more room to the ubuntu side.

---

### Post by forestpixie on 2008-02-05
that's what I thought wa sthe problem - glad it was :)

---

### Post by mistweaver4 on 2008-02-05
so im making progress.

ive shrunk the size of the area with windows but the partition editor wont let me increase the size where ubuntu is.

---

### Post by forestpixie on 2008-02-05
you have to move the ubunut partition first to the left (oops I said right before) before you can resize it

---

### Post by mistweaver4 on 2008-02-05
woo hoo! i think its working!

i wont know for sure for another 37mins apparently, but it seems to be going swimmingly! 

Thank you for your help forestpixie!

---

### Post by forestpixie on 2008-02-05
excellent - when you've done and you know you can boot to both can you make sure thread gets marked as solved

---

### Post by mistweaver4 on 2008-02-05
will do, thanks again

---

