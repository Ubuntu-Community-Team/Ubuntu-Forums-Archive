---
title: "Creating a personal boot disk."
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by mikpatton-photography on 2015-01-19
Here is one for you:  I'm currently volunteering for the Goodwill, and we see an unusual amount of desktops come through, donated for whatever reason.  Usually, they send them out to be recycled (whatever THAT means)  So here is what I want to do:

Create a boot-disc/usb drive that has the following:

1.  An LTS Ubuntu (So they dont have to worry about copyrights, etc...)
2.  And because of some weird "personal information" BS (you know, because people are weird) some sort of a Boot and Nuke.
3.  All pretty much automated.  Boot to CD, walk away.

Any ideas?  Surely I'm not the only person to want to do this...  I assume that I'd have to put all the software together, but I lack the knowledge to dtring it all together and make it work the way I need it to.  A few hints or a tutorial on writing the script?  Or point me towards a previous post?  

Thank ya kindly!

Mik

---

### Post by yancek on 2015-01-19
I'm not really sure what you want.  You can do an actual install of Ubuntu to a flash drive.  It will probably need to have an 8GB or larger flash drive.
You can use software such as unetbootin (which has different versions for windows, Linux and mac) or pendrivelinux (windows only) to create a bootable Live CD of Ubuntu or other Linux systems on a flash drive.  This would include software that can overwrite partitions/drives.  I'm not sure why you want that?  If you used it as a Live CD on a flash drive, nothing would be saved on reboot.

Are you wanting some medium to use to install Ubuntu or just something that can be booted and used?

Are you wanting to install Ubuntu on these various computers?

---

### Post by grahammechanical on 2015-01-19
Shall we start at the beginning? Have you ever installed Ubuntu? Your post is not clear on what you want to do. So, I may be completely misunderstanding you but this statement causes me to wonder if you have any experience in installing and using Ubuntu.

> [COLOR=#000000]I assume that I'd have to put all the software together, but I lack the knowledge to dtring it all together[/COLOR]

You see, it is all done for us. This is why Ubuntu is not an operating system but a Linux distribution. If it is your intention to recycle these machines by installing Ubuntu on them, then read the installation guides.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Take the tour and see what we get with Ubuntu

[http://www.ubuntu.com/desktop/take-the-tour](http://www.ubuntu.com/desktop/take-the-tour)

But consider this. These machine will be old hardware. Some machines may still be usable and may be powerful enough to run Ubuntu. Some may be broken and some may lack the necessary hardware to run Ubuntu. In which case you can try one of the other members of the Ubuntu family such as Xubuntu and Lubuntu.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

[http://lubuntu.net/](http://lubuntu.net/)

[http://xubuntu.org/](http://xubuntu.org/)

What do the managers of this organisation think about your idea? If they are recycling these machines for scrap value it could be because they do not have the human resources to test each of these machines to see if they still work. They may have decided that they do not have people who are qualified to re-condition these machines. And do not forget that even if you intended to give these machines away you still have a legal duty of care to make sure these machines are electrically safe to use.

You understand that people are weird and I agree with you. You may find people coming back with broken machines and demanding a replacement and demanding that someone retrieves all their data that they have put on it.

And another thing, who is going to explain how to use the operating system? Will you stay around long enough to take responsibility for what you have started?

Regards.

---

### Post by mikpatton-photography on 2015-01-20
The idea would be to make sure that no personal data wouild be left recoverable.  The boot and nuke, just to write zeros to the drive.  Basically, to set anyones mind at ease that their peronal info couldnt be retrieved.  (Short of forensics, etc) I realise that most reformats basically get rid of everything, but I just wanted to nail it down.  I guess I want to know how to ADD that bit of software to the basic install of Ubuntu.  And make it painless and hands off.

---

### Post by mikpatton-photography on 2015-01-20
To answer a few questions:  I'm just trying to figure out if its possible to do so, while making all levels happy with "safety"  

I am very familiar with installation of Linux, (Currently using it on the laptop)  

As far as the goodwill is concerned, everything is sold "as-is", so we wouldnt be on the hook for repairs, etc.  

As far as the rest...  Im qualified enough to strip parts and rebuild.  Basically, I'd be volunteering my time to do this, at no cost, etc.  I'm not really worried about long term support, as most of these would be sold to people who would be striping them down for parts, etc.  (Id install windows, but obviously, thats a whole OTHER problem)

---

### Post by yancek on 2015-01-20
If you were to use software such as unetbootin or pendrivelinux to create a bootable Live CD of Ubuntu on a flash drive, you would not have to worry about data as it is a read-only filesystem.  Any software installed, anything downloaded, any folders/files created when booted to it will be gone on reboot.  Nothing is saved on reboot.

You could do what is referred to as a "frugal install" with unetbootin, putting Ubuntu on the hard drive but still as a Live CD and a read-only filesystem so that nothing is saved on reboot.

I'm not sure whose personal data you are concerned about.  The people who are giving you the computers?  The people who are buying them or having them given?  Seems to me that would be their responsibility.

Overwriting a partition or drive can be done with the dd command or with 'shred' both of which should be on the Ubuntu medium.

---

### Post by sudodus on 2015-01-20
> **mikpatton-photography said:**
> ...
Create a boot-disc/usb drive that has the following:

1.  An LTS Ubuntu (So they dont have to worry about copyrights, etc...)
2.  And because of some weird "personal information" BS (you know, because people are weird) some sort of a Boot and Nuke.
3.  All pretty much automated.  Boot to CD, walk away.

...

And thank for explaining with more details :-)

1. No problems with Ubuntu, it is free software - but will you install it to these second-hand computers, or only run it live to test if the computers work?

                          [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")                 


The community flavours of Ubuntu are better for old computers but contain some proprietary software, so the computers cannot be sold with such installed systems in certain countries, for example the United States. But you can make it easy for the users to install by supplying CD disks for Lubuntu or DVD disks for Xubuntu.

2. You can use ***DBAN***, which can wipe the drive in a more efficient way than overwriting with zeros. But it will be in a second CD or USB drive. Don't make things complicated by trying to put everything in one drive.

3. Well, at least two stages - wiping and testing.

But installation of an Ubuntu flavour in many different computers will not be very automatic, if that is what you hope. After a while you will know more about tweaking Ubuntu flavours and versions in old computers than most of us, and you will be very welcome to help people here at the Ubuntu Forums, which is also a volunteer task ;-)

Many old computers but not all are worth spending time on: see this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

