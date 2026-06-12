---
title: "Upgrade from Karmic, Grub symbol 'the puts'  not found"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by alienprdkt on 2010-05-12
Please help 

Just updated from Karmic and wont boot... 
why did it ask me to keep all these local files but grub configuration? 

anyways got an error need help with please.

Got error on boot:

Grub error: the symbol 'the_puts_' not found
grub rescue>

what is the_puts_ anyways?

my boot directory should be found on /dev/sda1 (if that helps)

What do I do now?

Please help.

Please be specific for I don't understand Grub 2 at all.

Any help will be greatly appreciated, I have put over 200 hours into customizing my desktop. And have over 20 databases on it. I really need it back up ASAP, since this is a production machine... Well definitely teaches me about backing up or reading about some boot problems before the next ubuntu update.

---

### Post by alienprdkt on 2010-05-13
60 Views no reply's

Am I the only one that has received this error when upgrading from Karmic to Lynx?

I did not think that upgrading one version would kill grub. The last time I had upgraded it had promted me to keep my local grub configuration.

Anyone know how to possibly re-install grub2 from the grub rescue prompt?

Or how to re-install grub and have it work, or even just fix grub.

Again my boot directory is located /dev/sda1

Anyone, Anything?

---

### Post by alienprdkt on 2010-05-13
Well thanks to aumshantih asking the same question as I did in [http://ubuntuforums.org/showthread.php?t=1467102 ]("http://ubuntuforums.org/showthread.php?t=1467102")

Someone had suggested a fix that had worked!

found here : [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)

well thanks for everyone viewing this thread!

would have been nice if someone would've replied to me, but atleast the problem is now fixed! 

and I can finally enjoy Ubuntu Lynx.

---

### Post by sallymc on 2010-05-14
> **alienprdkt said:**
> Please help 

Just updated from Karmic and wont boot... 
why did it ask me to keep all these local files but grub configuration? 

anyways got an error need help with please.

Got error on boot:

Grub error: the symbol 'the_puts_' not found
grub rescue>

what is the_puts_ anyways?

my boot directory should be found on /dev/sda1 (if that helps)

What do I do now?

Please help.

Please be specific for I don't understand Grub 2 at all.

Any help will be greatly appreciated, I have put over 200 hours into customizing my desktop. And have over 20 databases on it. I really need it back up ASAP, since this is a production machine... Well definitely teaches me about backing up or reading about some boot problems before the next ubuntu update.

I CAN HELP!  Have just had the exact problem, and fixed it.  Go to :

 ['alexandre ***jelly kernel***' french karmic]("http://www.google.com/search?hl=en&ei=Dg3tS8XnEqHYmwPSzq2qDg&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBEQBSgA&q=%27alexandre+jelly+kernel%27+french+karmic&spell=1")

 on Google.  The first article is : 
**[Fix Symbol 'grub_puts'  Not Found When Migrating From Ubuntu *Karmic*]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")**

Follow his instructions and you will be delighted.  By the way, you will need a second working computer in order to access these instuctions, and a live Ubuntu CD to boot from.
Note that his first instruction :  
sudo fdisk-l

has a space after fdisk, before the dash.

Good luck and keep smiling.  I LOVE UBUNTU.

:) Sallymc

---

