---
title: "Help!  Broke Libc6 now Synaptic is broken!! Help me !!!"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by FRuMMaGe on 2007-05-15
I tried to install an earlier version of libc6.  BIG MISTAKE.

Now when I try to use apt-get, i get a "Floating point exception".

And synaptic will not open!

HELP!!!

---

### Post by FRuMMaGe on 2007-05-15
Please help!  Im afraid to turn off my computer in case it doesnt start up again!

---

### Post by FRuMMaGe on 2007-05-15
bump :(

---

### Post by FRuMMaGe on 2007-05-15
Sorry to whine, but im so screwed if i cant sort this out.

Is there a way to reinstall libc6 from the liveCD?

---

### Post by jrusso2 on 2007-05-15
Dude to downgrade libc is major no no.  Everything is dependent on the version.

Best to reinstall that mess.

---

### Post by FRuMMaGe on 2007-05-15
yeah I realize that now.  Isn't there anything less drastic I could do?

Is their a "repair" function for major stuff like libc6?

I have the LiveCD and I can still access the terminal from ubuntu.

Or is there a way to manually fix it (without the use of deb files or synaptic)?

---

### Post by FRuMMaGe on 2007-05-16
anyone? :(

---

### Post by FRuMMaGe on 2007-05-16
bump

---

### Post by FXWGBill on 2007-05-23
I just came across your post and I am in a similar boat, but havn't downgraded libc6 yet.  It appears it's been a week since your last post and I am curious if you got it straightened out yet?  What mine is doing, is the same thing as when you started, the upgrading of libc6 and a conflict with txdata...  I've tried all kinds of combinations of doing 'things' and can't seem to come across anything that is acceptable to me, or works, (preferably I will find both (simultaneously!!)).  (As far as downgrading one to fix the other, etc).  The developers have to know by now this is an issue for a lot of folks...   I have about 200 packages that are ready to be upgraded and won't because of this silly tzdata problem.  Wondering how I could 'undo' that dependency at this point.  I feel like if I can get it past the tzdata problem I can fix the rest...  

If ya figured out anything, please let us know...  This seems to be an issue for a bunch of peeps, as I said...

EDIT:

If you are still having problems, I just figured out all my problems, or at least how to get around them, anyway.

I'm not sure what all is missing as far as Synaptic goes, but your best bet is to try and install the updated libc6 back.

To do that go to your   /var/cache/apt/archives  folder and see what versions you have in there, and then reinstall the newer version with:  dpkg -i newerversion.deb

The try running synaptic again and see what it says.  If it names package dependencies that you have unloaded, you can use that list to dpkg -i the things you need
to get Synaptic back going.

Just some thoughts...  Like I say, I just found the post when looking for a cure for my problem with libc6 and tzdata....

---

### Post by FRuMMaGe on 2007-05-23
> **FXWGBill said:**
> I just came across your post and I am in a similar boat, but havn't downgraded libc6 yet.  It appears it's been a week since your last post and I am curious if you got it straightened out yet?  What mine is doing, is the same thing as when you started, the upgrading of libc6 and a conflict with txdata...  I've tried all kinds of combinations of doing 'things' and can't seem to come across anything that is acceptable to me, or works, (preferably I will find both (simultaneously!!)).  (As far as downgrading one to fix the other, etc).  The developers have to know by now this is an issue for a lot of folks...   I have about 200 packages that are ready to be upgraded and won't because of this silly tzdata problem.  Wondering how I could 'undo' that dependency at this point.  I feel like if I can get it past the tzdata problem I can fix the rest...  

If ya figured out anything, please let us know...  This seems to be an issue for a bunch of peeps, as I said...

I'm sorry to say that I took the only advice I was given and just reinstalled.  However, it only took me about an hour to get back to the stage I was at, because I backed up all my games and home folder and used a program to burn all my downloaded packages to a cd.

If you have set a restore point or ghost image then just restore to it.  Sorry i can't be of more help.  It was my own fault anyway for downgrading libc6 :p

---

### Post by FXWGBill on 2007-05-23
I have posted this in a different thread, but I'll put it here too, just in case.

My notes from the same problem:

Figured out that had to back up to the previous version of tzdata and lock it
did this by going to: /var/cache/apt/archives and invoking:
sudo dpkg -i tzdata_2007e-6ubuntu1_all.deb

NOTE!!!: THE f version of tzdata is the bad one!!!

(says if need to 'adjust the time' use: dpkg-reconfigure tzdata )

Once that was done, then loaded up synaptic and locked down tzdata

Next... starting running the updates again, and NOW we seem to have an
issue with:

/var/cache/apt/archives/remote-tty_4.0-10_i386.deb going to see if I can unmark it and that fix it for now!!

It did unmark and now we can just go back and finish the upgrade...

everything is running great again...

---

