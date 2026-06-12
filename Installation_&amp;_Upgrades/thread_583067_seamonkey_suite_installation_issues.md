---
title: "seamonkey suite installation issues"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2007-10-20
friends,
i feel lost sometime.

downloaded seamonkey tar.gz file. created .deb file using alien. then clicked on .deb file - it said that the installation has been successful. however, i can not locate where to run the software from.

in other words, the icon is not on desktop, nor in any menu nor i can locate it anywhere else.
any one ??

Sandeep

---

### Post by repawn on 2007-10-20
This is probably not the answer you are looking for but Seamonkey is in the repositories - it is known as iceape - take a look under add/remove programs. When you created the DEB it probably placed the file in your home directory somewhere - you will need to create a menu item for it. A search of the forum will provide answers on doing that.

---

### Post by MSchenker on 2007-10-22
> **repawn said:**
> ...Seamonkey is in the repositories - it is known as iceape - take a look under add/remove programs.

I wish I had known this before!!  I checked the repository and did not see SeaMonkey in there, so I went and downloaded the suite from the Mozilla site and ran into the same trouble that mosaic2s reports in his post.

Two questions:

1. Is IceApe the very same thing as SeaMonkey?

2. Is there a way to edit the repository so it mentions SeaMonkey in the IceApe description?  This would avoid future users from having the same trouble.

Thanks,
Matt

---

### Post by MSchenker on 2007-10-22
Actually, I just checked in add/remove programs and I cannot find Iceape listed there.  I also ran the Adept package manager and still could not find it.

Does it go by a different name in 7.04?

Can someone please help me find this application?

Thanks,
Matt

---

### Post by mosaic2s on 2007-10-22
same situation. i could not locate it either as iceape.

---

### Post by MSchenker on 2007-10-22
OK, this seems like a simple matter...
Does anyone know how to locate the IceApe application?

---

### Post by MSchenker on 2007-10-24
I just found out that IceApe is in the repository of the latest version (7.10).  It's not in 7.04, which is the one I am running.  That explains the problem!

I do wish that when people post information they could be more informative, or at least follow up with simple data.  Remember, there are a lot of new users here in the Ubuntu forums, and they need more than just a "go here..." comment.

Thanks,
Matthew

---

### Post by jviscosi on 2007-10-25
I may be wrong but I don't think you can use alien to turn a tar.gz into an installable DEB.  As far as I know it's for converting things like RPMs into DEBs.  (That's all I've ever used it for, anyway.  But like I said I could be wrong)

The way I used to install Seamonkey before I upgraded to 7.10 and got IceApe out of the repositories was to unzip the tar.gz, then go to the seamonkey-installer directory and run the seamonkey-installer as root from a terminal.  On my machine it wants to install to /usr/local/bin/seamonkey by default, but I would put it in a subdirectory according to the version number instead.  I would then put a link to the seamonkey executable directly in /usr/local/bin.  So if I downloaded Seamonkey to /download/Mozilla/Seamonkey, I would do something like this in the terminal:

```

cd /download/Mozilla/Seamonkey
tar zxvf seamonkey.tar.gz
cd seamonkey-installer
sudo ./seamonkey-installer

```**<GRAPHICAL INSTALLER RUNS>**

I tell it to put Seamonkey in /usr/local/bin/seamonkey1.1.5 or whatever.  Then, when it's finished, I would do:

```

sudo ln -s /usr/local/bin/seamonkey1.1.5/seamonkey /usr/local/bin/seamonkey

```You could also put the seamonkey installation folder into your path, but a symbolic link is simpler in my opinion.  Then you just have to add Seamonkey to the menu in your preferred window manager or desktop environment.

---

### Post by mosaic2s on 2007-10-26
alien seems to do the job of converting tar.gz. to .deb

anyhow, your advise on setting up a tar.gz file is great. will use it next time. for now, my 7.04 is waiting for the CD to upgrade to 7.10.

---

### Post by jviscosi on 2007-10-26
> **mosaic2s said:**
> for now, my 7.04 is waiting for the CD to upgrade to 7.10.

That's good, I think you'll find it more convenient to have the packagers pushing out updates to Seamonk -- errr, IceApe.  I know I do.  But I do so hate that name!  ;-)

---

### Post by MSchenker on 2007-10-26
I just installed the newest alpha Wubi 7.10, mainly in order to install IceApe (SeaMonkey).  But when I go into Adept > Internet, the IceApe applications are all ghosted out.

Can someone help me get them un-ghosted!

Thanks,
Matt

---

### Post by jviscosi on 2007-10-27
Try opening a terminal and running **sudo apt-get install iceape**. A lot of times the output from that is more informative than synaptic. (For instance it told me why synaptic wasn't able to update gnome-themes-extras and some other packages -- there were conflicts with existing packages.  With apt-get I was able to tell it to resolve the conflict.)

---

### Post by MSchenker on 2007-10-31
Success!  I got IceApe installed on Kubuntu 7.10.

Now, just one more thing.  Does anyone know how to install the profile manager?  My wife and I have been using SeaMonkey, which lete each of us sign into our own e-mail and browser settings.  Is there a way to get this in IceApe as well?

Thanks,
Matt

---

### Post by mosaic2s on 2008-01-24
thanks. buddies. i am learning to say thanks. :)
btw, now using gutsy. and trying vbox. it is great.

---

### Post by ADH on 2008-02-13
I have Seamonkey 1.16 installed (don't remember how I did it - I know nothing about Linux yet.)  How do I get it to upgrade to the latest version?

Thanks,

---

