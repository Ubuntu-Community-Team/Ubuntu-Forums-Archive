---
title: "Ghosting a machine ... is this possible?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by asearle on 2010-05-13
Hi Everyone,

I have a laptop running dual boot which I would now like to convert to single boot (Ubuntu only).

I have recently had some very good experiences with VirtualBox (It's fantastic!) and so the idea that I have is to 'migrate' my whole Windows environment from 'dual boot' to VirtualBox.

I know that this can be done with such products as 'Ghost' where you take a snapshot of a whole (Windows) system and then you can recreate this (from DVD).

Here I'd really like to know whether Ubuntu (live CD) offers a similar tool so that I could copy my whole Windows setup, save it to DVD and then simply 're-install' it on a new VirtualBox machine.

That would save me absolutely masses of configuration work!

Any tips would be most gratefully received.

Cheers,
Alan

---

### Post by howefield on 2010-05-13
Clonezilla would take an image of your Windows system in the same manner as Ghost, but I fear using the image in Virtualbox isn't as straight forward as you think.

---

### Post by dino99 on 2010-05-13
clonezilla can make what you need: 
[http://www.clonezilla.org/download/sourceforge/](http://www.clonezilla.org/download/sourceforge/)

but as you still know virtualbox, wine (winehq) is able to directly run the windoz apps with ubuntu: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

here is how to format : 
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by wkulecz on 2010-05-13
Windows throws up a lot of obsticals when replacing motherboards -- which is in effect what moving to VirtualBox would be.  I know how to solve them for W2k, XP is more difficult, Vista & Win7 close to impossible as far as I can tell -- you need to re-install, re-activate, and re-install all your applications -- its why I'm moving to Linux as fast as possible.  

I can backup my Linux systems with rsync and "clone them and all apps by re-installing grub and  editing /etc/fstab and a few other system files to change the hostname (not usually necessary as the clones end up on different subnets for me) on the new drive before the first boot using the live CD.

If you want to try, the Virtualbox.org website has some user tutorials and howtos, one of which addresses this.  Its not easy.

---

### Post by asearle on 2010-05-14
Hi Guys,

Many thanks for the feedback and, yes, I will certainly check out Clonezilla.

I see the reason for the problem with the migration to VirtualBox:  XP will take that as a different PC and all that stupid 'registration' stuff will kick in.  Arrrggghhh!

So I probably won't do that.

But regarding Ubuntu, yes, I have to say that I can do most of what I normally do directly in Linux including quite a lot of Windows stuff using Wine.  That's great and it is all much more stable and easy to set up than it was a couple of years ago.  Bravo.

The one thing (however) which keeps tripping me up is the fact that I often need to work with MS-Access which (as far as I know) won't work under Wine.

I played around with OpenOffice Base but, although I'm a big fan of OpenOffice, Base just hasn't quite got there yet.  That's a big shame.

Anyway, maybe I will soon be able to completely do without Windows.  That would be GREAT !!!

Regards and thanks,
Alan Searle

---

