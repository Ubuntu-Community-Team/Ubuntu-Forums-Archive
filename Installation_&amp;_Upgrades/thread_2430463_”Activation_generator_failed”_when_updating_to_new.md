---
title: "”Activation generator failed” when updating to newest Ubuntu"
date: 2019-11-02
forum: Installation &amp; Upgrades
---

### Post by zaragendon on 2019-11-02
Like the title says. I can’t do anything. Nothing works. I havn’t tried to restart my laptop yet. I’m not good with computers and I don’t understand what this means. It just was updating and then this happened. Help, anyone? Thanks. (Sorry abou gigantic photo)

---

### Post by zaragendon on 2019-11-02
Update: So I restart my laptop and now theres just a black screen and nothing is happening.

---

### Post by zaragendon on 2019-11-03
Anyone can help?

---

### Post by The Cog on 2019-11-03
That looks bad. I'm sorry, I have no idea how to fix that. I found a suggestion (using google) to run an apt reinstall --force command, but of course you can't do that if it wont even boot. 
If it was me, I'd install from scratch and restore my user data from backups.

If no backups, I would be setting about booting the installer USB and using its try-before mode to mount the disks and copy my data off to a backup disk before doing a new install.

---

### Post by zaragendon on 2019-11-12
Sorry for be a noob but how can I restore my user data from backups? If I even have any...

---

### Post by zaragendon on 2019-11-14
> **zaragendon said:**
> Sorry for be a noob but how can I restore my user data from backups? If I even have any...

Anyone can help me on this?

---

### Post by jetsam on 2019-11-14
This is going to be challenging.  Let's see if we can rescue your data, first.

Do you have a means to make either a live CD or a live USB thumb drive?  Also, have you used Linux much before, and do you know how to use the command line?

Finally, do you have access to a USB hard drive or a large USB thumb drive?  You need some place to put your data when and if you can recover it.

---

### Post by zaragendon on 2019-11-17
> **jetsam said:**
> This is going to be challenging.  Let's see if we can rescue your data, first.

Do you have a means to make either a live CD or a live USB thumb drive?  Also, have you used Linux much before, and do you know how to use the command line?

Finally, do you have access to a USB hard drive or a large USB thumb drive?  You need some place to put your data when and if you can recover it.

Thank you for your respond.

I have an 8 Gb USB thumb drive. Also I have another computer with Windows 10 where I can put my data.

Iv used a little bit Linux and the terminal but I can basically say that I don’t know anything about commands anyway. So if you could explain me everything step by step, that would help me alot. Oh also, I’m not a native English speaker so it might be I don’t understand everything.

---

### Post by jetsam on 2019-11-17
> Iv used a little bit Linux and the terminal but I can basically say that I don&#8217;t know anything about commands anyway. So if you could explain me everything step by step, that would help me alot. Oh also, I&#8217;m not a native English speaker so it might be I don&#8217;t understand everything. 

Ok.  We'll do our best.

Go here: 
[Puppy Linux Installation and Usage]("http://puppylinux.com/install.html")
and follow the instructions.  

You need to copy Puppy Linux to your USB stick or to a dvd drive so that we can try to use it to boot into your laptop.  This may not work.  If the laptop is locked down in such a way that it can't be booted from USB or from the optical drive, then we'll have to find another path through.

You need to pick a particular Puppy Linux first.  If your laptop is 64 bit (any relatively newish one will be), then I'd go for Xenial 64 Bit.  Here is a direct download link:
[http://distro.ibiblio.org/puppylinux/puppy-xenial/64/xenialpup64-7.5-uefi.iso]("http://distro.ibiblio.org/puppylinux/puppy-xenial/64/xenialpup64-7.5-uefi.iso")

That's from this this ftp site, Puppy's official distribution channel for Xenial:
[http://distro.ibiblio.org/puppylinux/puppy-xenial/64/]("http://distro.ibiblio.org/puppylinux/puppy-xenial/64/")

If you need a different spin of Puppy because you need 32 bit or would prefer something else, you can select from the list here and follow the links for downloading instructions:
[Puppy Linux Downloads]("http://puppylinux.com/download.html")

Once you've downloaded the iso, you need to go here:
[Blue Pup Google Drive For Disk Imager]("https://drive.google.com/drive/folders/0B_iVVJCd9q09VGZsZE5keU1vR0E")

From that page, download "win32diskimager-v0.7-binary."  Right click on the file name at the bottom, then select 'download' from the menu to download it.

Then, unzip win32diskimager somewhere on your Windows PC.  Run the setup file in the extracted directory.  Finally, run the tool, and use it to burn the Puppy version you downloaded above to your USB stick.

Many steps!  Take them slowly, and ask questions if you need to.  This may be a process, so I expect it will take some time.  It helps a lot you have a working computer with you, though.

Cheers,
jetsam

---

### Post by ajgreeny on 2019-11-17
It looks from your image in post #1 that you installed with LVM partitioning, which is not the best way, particularly if you're not used to Linux.

Is this a new install or an update from a previous ubuntu version to a newer version?
If you do have much data on this ubuntu system you can certainly copy it to an external drive, though as jetsam is saying you will need a live OS to do it.
As you presumably installed Ubuntu at some time in the past you may already have either a live USB or DVD version you can use simply for this purpose.

It may be even easier to simply reinstall the Ubuntu from a live system after copying your data elsewhere as installing is quickly done.  If you do reinstall I recommend that you **do not use LVM** but choose the default installation to disk.

More detail about your hardware would be helpful; is it UEFI or MBR/BIOS?

---

### Post by zaragendon on 2019-11-18
> **jetsam said:**
> Ok.  We'll do our best.

Go here: 
[Puppy Linux Installation and Usage]("http://puppylinux.com/install.html")
and follow the instructions.  

You need to copy Puppy Linux to your USB stick or to a dvd drive so that we can try to use it to boot into your laptop.  This may not work.  If the laptop is locked down in such a way that it can't be booted from USB or from the optical drive, then we'll have to find another path through.

You need to pick a particular Puppy Linux first.  If your laptop is 64 bit (any relatively newish one will be), then I'd go for Xenial 64 Bit.  Here is a direct download link:
[http://distro.ibiblio.org/puppylinux/puppy-xenial/64/xenialpup64-7.5-uefi.iso](http://distro.ibiblio.org/puppylinux/puppy-xenial/64/xenialpup64-7.5-uefi.iso)

That's from this this ftp site, Puppy's official distribution channel for Xenial:
[http://distro.ibiblio.org/puppylinux/puppy-xenial/64/](http://distro.ibiblio.org/puppylinux/puppy-xenial/64/)

If you need a different spin of Puppy because you need 32 bit or would prefer something else, you can select from the list here and follow the links for downloading instructions:
[Puppy Linux Downloads]("http://puppylinux.com/download.html")

Once you've downloaded the iso, you need to go here:
[Blue Pup Google Drive For Disk Imager]("https://drive.google.com/drive/folders/0B_iVVJCd9q09VGZsZE5keU1vR0E")

From that page, download "win32diskimager-v0.7-binary."  Right click on the file name at the bottom, then select 'download' from the menu to download it.

Then, unzip win32diskimager somewhere on your Windows PC.  Run the setup file in the extracted directory.  Finally, run the tool, and use it to burn the Puppy version you downloaded above to your USB stick.

Many steps!  Take them slowly, and ask questions if you need to.  This may be a process, so I expect it will take some time.  It helps a lot you have a working computer with you, though.

Cheers,
jetsam

Thank you for the answer. I will try this on next weekend when I have more time, then I’ll come back.

---

### Post by zaragendon on 2019-11-18
> **ajgreeny said:**
> It looks from your image in post #1 that you installed with LVM partitioning, which is not the best way, particularly if you're not used to Linux.

Is this a new install or an update from a previous ubuntu version to a newer version?
If you do have much data on this ubuntu system you can certainly copy it to an external drive, though as jetsam is saying you will need a live OS to do it.
As you presumably installed Ubuntu at some time in the past you may already have either a live USB or DVD version you can use simply for this purpose.

It may be even easier to simply reinstall the Ubuntu from a live system after copying your data elsewhere as installing is quickly done.  If you do reinstall I recommend that you **do not use LVM** but choose the default installation to disk.

More detail about your hardware would be helpful; is it UEFI or MBR/BIOS?

Is LVM partitioning something about hard disk partition? If so, if I remember correct, I did that long time ago.

I tried to updated the old version of Ubuntu to the newest.

About the hardware, Im not sure what do you mean about UEFI and MBR/BIOS. I know what is BIOS (pressing F10 or something while the pc is booting?) and and Im pretty sure my pc have that.

---

### Post by jetsam on 2019-11-18
> **zaragendon said:**
> ...I will try this on next weekend when I have more time, then I&#8217;ll come back.

Sounds good.  If you can get Puppy running on your computer, you just need to copy off the files you want to keep.  Definitely copy the entire home directory of each user.  Other than that, there could be save games or other data files you need to look for.  Google can help if you need to find, say, the default save game location for a particular game.  The Steam forums for a game are also a good place to look for this information.

If you run a database for a website or anything, you'll want to follow the database's procedure for backing up...  Again, Google is your friend here.

Firefox/browser bookmarks are good to save.  They take a long time to acquire, and copying them to a new system makes it feel like home.

There are some automated scripts available for backing up a system quickly and without much interaction on your part, but I've never used them so I can't vouch for them personally.

Good luck with it.  Ask questions if you want to or if you get stuck.

---

### Post by zaragendon on 2019-11-25
> **jetsam said:**
> Sounds good.  If you can get Puppy running on your computer, you just need to copy off the files you want to keep.  Definitely copy the entire home directory of each user.  Other than that, there could be save games or other data files you need to look for.  Google can help if you need to find, say, the default save game location for a particular game.  The Steam forums for a game are also a good place to look for this information.

If you run a database for a website or anything, you'll want to follow the database's procedure for backing up...  Again, Google is your friend here.

Firefox/browser bookmarks are good to save.  They take a long time to acquire, and copying them to a new system makes it feel like home.

There are some automated scripts available for backing up a system quickly and without much interaction on your part, but I've never used them so I can't vouch for them personally.

Good luck with it.  Ask questions if you want to or if you get stuck.

Ok it worked. I managed to do all the steps. And copying all the important stuff. Now, what do I have to do now?

I tried to google how to format the current hard drive but ai couldnt find good answers. I found out that you can format the disk from terminal but the instructions were too confusing for me.

---

### Post by zaragendon on 2019-11-30
Any help?

---

### Post by zaragendon on 2019-12-04
I really need help with this one. How can I format my computer to install Ubuntu again? Its been long time I havent been able to use my laptop. Thanks.

---

### Post by zaragendon on 2019-12-08
Nvm I found help from other place.

---

### Post by wildmanne39 on 2019-12-08
Will you please post your solution here so it can benefit the whole community?

Thanks

---

