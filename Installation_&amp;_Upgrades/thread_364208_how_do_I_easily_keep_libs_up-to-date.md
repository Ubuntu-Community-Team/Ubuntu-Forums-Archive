---
title: "how do I easily keep libs up-to-date?"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by tashazo on 2007-02-17
Recently I haven't been able to install programs because my libs are not up to date, and so the sources wont configure.  I get error messages such as(below is what I get when I try to get latest stable version of epiphany browser):
Package requirements (
                  glib-2.0 >= 2.12.0
                  gmodule-2.0
                  gtk+-2.0 >= 2.10.0
                  gtk+-unix-print-2.0 >= 2.10.0
                  libxml-2.0 >= 2.6.12
                  libxslt >= 1.1.7
                  libgnome-2.0 >= 2.14.0
                  libgnomeui-2.0 >= 2.14.0
                  libglade-2.0 >= 2.3.1                   gnome-vfs-2.0 >= 2.9.2                  gnome-vfs-module-2.0
                  gconf-2.0
                  gnome-desktop-2.0 >= 2.9.91
                  libstartup-notification-1.0 >= 0.5
                  ) were not met:

Some of these I've seen before.  
I've tried distro-upgrade, etc, but these dont do anything.  Is there an easy way to get my entire system truly up-to-date, so that I don't constantly have to go hunting for stuff just to install a new program? 
Thanks...

---

### Post by nyinge on 2007-02-18
AFAIK, when you download sources to compile from the program's website, they're quite bleeding edge.  In other words, they have not been thoroughly tested enough to include in Ubuntu's released versions.

I think it is OK to stay with Ubuntu's released versions, unless of course, you must have a certain feature which is not part of the released version.  Then, unfortunately, you will have to grab all those required sources of libraries from their respective sites and compile them yourself.

Actually, if you want bleeding edge stuff, you should try out Feisty.  :)

---

### Post by tashazo on 2007-02-18
nyinge, thanks for the tip on Feisty.  I will definitely be upgrading in April.
But in the meantime, since each of those 'required' libs/packages are available (& stable?), why is it so hard to update? 
I don't think I know enough code to go and install each one separately - there's too much room for (my) user error, and I'm afraid to mess up my system, as well as spend hours on trying to get it right.
So I guess if there's no 'easy' way, then I'll just wait for Feisty.
Thanks!

---

### Post by lazork on 2007-02-18
If you're trying to compile the programs yourself you might be indeed missing these libraries. Even though you've already got the listed libs, keep in mind that you'll need the "dev" ones as well (e.g. you need both libxml2 and libxml2-dev). You can easily find them in the repositories.
By the way, I've checked some of the libraries listed in your post and the version available in the repositories seems to be recent enough, so I guess you're just missing the "-dev" version of the libs.

Another thing: usually ubuntu keeps all the packages (libraries included) up to date automatically. Unless you're really new to ubuntu you'll have certainly seen the "Updates available" message pop up from the system tray: that's when ubuntu lets you know there is a newer version of some of the packages installed; you can update them by clicking on the orange icon that has appeared.
But I think you already knew this.

---

### Post by tashazo on 2007-02-18
yeah I did...
thanks tho.

---

### Post by nyinge on 2007-02-18
You're welcome Tashazo.  Yes, I forgot to mention that you need some "devel" packages, as Lazork pointed out.  Well, if those won't satisfy the dependencies, I don't see any easier way at the moment.

However, the good news is that there is [Feisty Herd 4]("http://cdimage.ubuntu.com/releases/feisty/herd-4/") available now.  Be warned that Feisty Herd 4 is not at all a stable release.  As usual,  I highly recommend that you only install it on a spare machine / partition.  You'll find most of them at updated versions.

---

### Post by tashazo on 2007-02-18
hmmmm I'm itching to try it...
I want to start fresh.....

But I don't have a spare partition. It would have to go over my Dapper.
My important files are on a fat32 partition, while email & config files (for firefox, etc), I could easily backup as well.
So should I wait?  
Does it wipe out everything from before?  Or can you consider it a simple "upgrade"?

---

### Post by nyinge on 2007-02-22
Sorry for the late reply.  If you're still reading...

It will wipe out the system if you do a fresh install and choose to format the partition.  You can choose not to format it and just install Feisty on top of Edgy, I believe that may cause disasters as there are many incompatibilities between the two.

Well, there is one really cool thing you can try next time.  Forgive me if you've already known about this though.  :P

Have your "/home" directory on a separate partition.

So, every time you do a fresh reinstall, you will retain all the information (personal files, configuration files, etc.) inside your home directory.  This will save you time for reconfiguring your GUI and lots of other stuff.  

I can't really recall in details of the process, but in general...
- Choose to manually partition your drive (when you're presented with an option to do so during the installation process)
- Manually create "/", "swap" and "/home" partitions (at least)
- Continue installation as normal

Now, when you want to reinstall Edgy (maybe because there are too many problems with Feisty Herd 4), during the installation process, just point your "/home" directory to the old "/home" directory, but do NOT choose to format it (the "/" partition can be reformatted, and it is recommended).  Also be sure to use the same login name/password.

I havn't had any problems this way in jumping around releases.  But I've heard that some people run into problems if it is a distribution.  Good luck!

---

### Post by tashazo on 2007-02-23
I have Dapper, not Edgy.  I assume it's the same situation though?
Interesting trick with the home partition - no, I hadn't heard of it.  I would do that but I'm running out of space.  I still have a Windows partition for a couple programs I need to use (Adobe).  I think I split up my hard drive wrong - right now I have the hpfs/ntfs windows (hda2, 14gb), fat 32 (hda3, 4gb), linux (hda5, 19gb) & its swap (hda6, 1gb) under an extended partition (hda4, 20gb).  hda1 is a 48mb dell utility thing.
I don't know much about partitioning, but I remember I wasn't allowed to add anything else, and I had to do this extended thing in order to get my linux + swap in there.
Is the trick still doable for me?  How much space would you give to the home partition?

---

### Post by nyinge on 2007-02-24
Yes, the trick is doable.  Well, I call that a trick because I just found out about it a couple of months ago... hehe...  not exactly one though.  Anyway...  You're still using Dapper.  You can still enjoy lots of newer version of packages in Edgy, but of course, not as recent as packages in Feisty.  But I'd rather choose stability over dependacy nightmares.

That being said...  Let's say you're installing a fresh copy of Edgy using the desktop/live CD or DVD.  Once the desktop loads, you'll proceed the install by clicking on the "Install" icon on the desktop.  After answering a few pages of questions, you'll arrive at a page where you'll be able to choose where to install to.  Choose to "Manually edit partition table."

According to your partition table, it seems that the 4 gigs of fat32 partition is for sharing between windows and linux, right?  You can actually choose the fat32 partition as your /home mount-point.  Of course, do NOT choose to format it.  (hda5, 19G) will be used for " / " mount-point (format it).  And the hda6 for swap.  Just make sure other partitions are not marked for formatting.

Should everything go smooth, you'll have a /home partition accessible by both Windows and Linux.  You'll also see a mixture of files created by Ubuntu and your personal files which may have been there on the fat32 partition from before.

---

### Post by tashazo on 2007-02-25
I like the idea.  I am going to do it.  My fat32 partition is basically a copy of stuff in my home partition I wanted to share with windows anyway, so this makes sense for me.  I hope 4gb is enough. I checked and it looks like I'm using about 1gb in my home right now.  But I haven't been downloading a lot of multimedia since I started with Dapper - I've kept it pretty clean...  I wonder if I should increase the shared partition making my windows about 10gb, linux around 15, and fat32 around 10gb.  Are there any security risks by putting home on a shared drive that windows viruses could ruin?  
But I think I'll wait to see if Feisty is stable by April, and then install Feisty if all's good.
2 more questions:
-how do I move my home directory to my fat32 partition now, without ruining any system stuff/dependencies/paths?
-after installing a new distro, like you said, how to I "point" home to my new fat32 'home' dir.?  (well, this would apply to now too)

---

### Post by nyinge on 2007-02-25
I keep the linux partition only at 10 gig on my laptop, and it seems to be doing fine, but I like to keep my home partition as large as possible.

Window viruses...  hmm...  AFAIK, since they're not targeted for Linux related files, I think you're on the safe side.  However, viruses, that deliberately alter/delete any files they could access, would impose some risks I suppose.

For moving your current home directory to a different partition, Psychocat has a [tutorial]("http://www.psychocats.net/ubuntu/separatehome"), though, I've yet to try it out.

For a fresh install, follow [this tutorial]("http://users.bigpond.net.au/hermanzone/p14.htm").  It's actually for a text install, but you could also apply the idea to a graphical install.[URL="http://users.bigpond.net.au/hermanzone/p14.htm"]
[/URL]

---

### Post by tashazo on 2007-02-26
Thank you.
I will check those out.  I've read psychocats stuff before - very well laid out guides...
Hopefully I'll be able to update my partitions/home dir without too much trouble.
I see that it is not recommended to use fat32 for the home drive, and psycocats offer another alternative with a prgrm that allows windows to read/write to ext2 linux...  I'll have to check all that out..
Thanks again. \\:D/

---

