---
title: "help with dual-booting and frequent installations"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by VCSkier on 2007-10-16
I always dual boot two linux distributions.  Either the stable Ubuntu and the testing branch, or Ubuntu and another distro altogether (openSuse at the moment), and the only thing that is constant is that I reformat and install new distributions often.  It seems though, that I have more problems than I should, when reformatting and installing...

Generally, my partition table looks like this.
/dev/sda1 - /home (shared)
/dev/sda2 - / for distro 1
/dev/sda3 - / for distro 2
/dev/sda4 - swap (shared)

This is where my problem is though.  I had Ubuntu 7.04 installed on sda2, and I reformatted sda3 to install openSUSE.  My Ubuntu installation then wouldn't mount my partition table, because my UUID's had changed.  So rather than manually fixing the fstab from console (I had done that in the past), I just reformatted sda3 and installed Gutsy on it (I had been wanting to anyway).  So everything was going fine, until I got a kernel update in openSUSE.  But because I had installed Gutsy last, it owned my grub and MBR, and so I couldn't boot to the new openSUSE kernel without fixing Gutsy's grub manually.  There must be an easier way to do this!  What is the best setup for someone who likes to test distributions?

Would it help if I ditched all this UUID garbage?  If so, what's the best way to do that?
*AND/OR*
Would it help if I had a separate /boot partition?  I had tried doing that in the past, and it just seemed to make things more complicated; maybe I did it wrong.

Is there anything else I could do?

---

### Post by Herman on 2007-10-17
Hello VCSkier,
It is much simpler to use the 'configfile' command rather than doing a direct kernel boot when you are booting other Linux distros from one GRUB menu, providing the other Linux also boots with GRUB.

If your other distro boots with LiLo, you can use the 'chainloader' command instead, (confgifile won't work, it will only work between GRUB and another GRUB). You will need to install LiLo to the first sector of the partition that LiLo belongs to for chainloading to work.
You can also chainload another GRUB if it is installed to the first sector.

By using either of those two commands, GRUB will bring up the other operating system's own GRUB menu, which will be automatically updated with it's own kernel updates. That avoids the need to manually update the kernel details each time another system receives a new kernel.

Here is a link for more info about that, [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

You could make a dedicated GRUB partition, but I would steer away from having any separate /boot partitions unless you have a very old computer with hard disk size limitations in your BIOS or something like that. 
Here's a link about making a dedicated GRUB partition, [         How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

As for the UUID problem, I would just hash out or delete lines for other operating systems in my /etc/fstab and make an mounting script like this instead, [COLOR=#666666][COLOR=#000000][Making a script for mounting your other filesystems instantly]("http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script").

Or just update your /etc/fstab, here's how, [/COLOR][/COLOR]
         [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

Regards, Herman :)

---

### Post by VCSkier on 2007-10-17
Very cool Herman.  Thank you very much.  I think I will use the configfile boot entry, and I will edit out the UUID's on my /etc/fstab (because the change so often).  I'll probably reinstall both of my distributions this weekend (with the brand new Ubuntu 7.10!) and set everything up as you've suggested.  The only restriction of this setup will be that the booting of my second distribution will be dependent on my first distro's grub; when I reinstall distro 1, I will have to add the configfile boot entry back to it's grub menu.lst *before* I can boot to distro 2 again.  Is this correct?

Thanks again for the help!  And by the way, your website is excellent.  There's alot of great help there, and I will certainly be recommending it to friends.

---

### Post by Herman on 2007-10-17
> The only restriction of this setup will be that the booting of my second distribution will be dependent on my first distro's grub; when I reinstall distro 1, I will have to add the configfile boot entry back to it's grub menu.lst *before* I can boot to distro 2 again.  Is this correct? Yes, that's right.
You should get yourself one of adrian15's [Super Grub Disks]("http://supergrub.forjamari.linex.org/") so you will have an emergency means to be able to boot any operating systems.

Configfile or chainloader boot commands are as all you need.

But if you make a dedicated GRUB partition, that will mean GRUB will be operating system independant. You could just make configfile or chainloader boot entries in your GRUB there, to boot your operating systems' GRUBs.
The difference between a 'dedicated GRUB partition' and a 'separate /boot partition' is the dedicated GRUB partition just has GRUB in it and doesn't belong to any particular operating system.
A 'separate /boot partition' contains GRUB and a Linux kernel and inirtd.img belonging to one of your operating systems, and is listed as /boot in one of your operating systems' /etc/fstab files.
It is possible to get more than one operating system to share the same separate /boot partition, but it wouldn't be an ideal way to set things up.
A dedicated GRUB partition though, would be a great idea.

If you will be changing operating systems often and you want something simple and quick to re-configure, you should try the GAG Boot Manager. GAG is 'operating system independent', because it installs to the first track of the hard disk instead of to an operating system. GAG is a 'Graphical boot manager', so it is easy to set up every time you add or remove an operating system. GAG also works from a floppy disc, or a CD. Here's a link to more info, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

> Thanks again for the help! And by the way, your website is excellent. There's alot of great help there, and I will certainly be recommending it to friends.
 Thank you. :)
There is an even better website that you should also tell your freinds about, called 'Ubuntu Linux Resources', and here is the link, [http://www.psychocats.net/ubuntu/index.php.]("http://www.psychocats.net/ubuntu/index.php")
aysiu has a lot of great help and information in there and includes a wealth of information. 
Ubuntu Linux Resources includes installation help for the Ubuntu Live CD installers, where mine is about the 'Alternate CD' installer, and where mine concentrates more on boot loaders and trouble shooting, aysiu's site has more information on getting started with Ubuntu, some of the things you can do when Ubuntu is up and running.

There are lots of other excellent websites about Ubuntu that will keep you fascinated, [Ubuntu Geek]("http://www.ubuntugeek.com/tag/ubuntu-hacks/") is another great one, so is [Ubuntu Starter Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") (almost compulsory).
Don't forget the [Ubuntu Wiki Official documentation]("http://help.ubuntu.com/")', 
 Also be sure to look through [Community documentation]("https://help.ubuntu.com/community/")
 And those are only a few of the great sites that keep us all interested in Ubuntu and having fun,
 Regards, Herman[B] :)
[/B]

---

### Post by VCSkier on 2007-10-29
FWIW, I ended up using GAG to dual boot, and its been great thus far.  Setup is really simple,and its completely independent of either of my distribution installations.  I wish I could figure out how to easily change the icons it uses, but other than that, I have no complaints and would recommend it to anyone who wants to dual boot but plans on reformatting any of their partitions periodically.

---

### Post by Herman on 2007-10-29
Yeah, I agree with you about the icons. It isn't easy to change the icons, but it is possible.
What icons would you like in GAG?
Debian and all the various Ubuntu icons and Suse?

Regards, Herman :)

---

### Post by VCSkier on 2007-11-12
Yeah, I would love to see Ubuntu and openSUSE included as icons that are available by default.  I would think that it would make sense to include other common distribution icons, like Debian, Fedora, Mandriva, and Gentoo...

I do have a new question though.  I have both of my installations share a /home partition, so when I reinstall a particular distribution, I can retain all of my files, and so I can more easily share files between distributions, but what is the ideal way to handle *users* in this type of situation.  I am the only person who uses my computer, so I have been keeping a singular user account that I use in both of my installed distributions, but I'm becoming unsure if this is ideal...

I often receive warnings prior to logging-in regarding non-existent session types (Gnome complains about KDE, and visa-versa), and it seems that openSUSE (KDE) and Ubuntu (Gnome) are conflicting over what should be displayed on the Desktop, as well as some other rather minor settings and defaults.  Would it be more ideal if I created separate user accounts for each distribution?  If I were to do this, would I be able to share documents and files as easily?  If not, is there a more ideal solution?

Thanks.

---

### Post by Herman on 2007-11-13
> Yeah, I would love to see Ubuntu and openSUSE included as icons that are available by default. I would think that it would make sense to include other common distribution icons, like Debian, Fedora, Mandriva, and Gentoo... I can make you a gag.com file with those icons and send it to you or help you make your own if you want. The instructions are already inside GAG's documentation, but there are a few little things about the instructions that make them hard to follow.

> I do have a new question though. I have both of my installations share a /home partition, so when I reinstall a particular distribution, I can retain all of my files, and so I can more easily share files between distributions, but what is the ideal way to handle *users* in this type of situation. I am the only person who uses my computer, so I have been keeping a singular user account that I use in both of my installed distributions, but I'm becoming unsure if this is ideal...

I often receive warnings prior to logging-in regarding non-existent session types (Gnome complains about KDE, and visa-versa), and it seems that openSUSE (KDE) and Ubuntu (Gnome) are conflicting over what should be displayed on the Desktop, as well as some other rather minor settings and defaults. Would it be more ideal if I created separate user accounts for each distribution? If I were to do this, would I be able to share documents and files as easily? If not, is there a more ideal solution? Well you could try out [Unison]("http://www.cis.upenn.edu/%7Ebcpierce/unison/"), as referred to in this thread: [http://ubuntuforums.org/showthread.php?t=603463](http://ubuntuforums.org/showthread.php?t=603463)
I haven't tried that out myself yet, but it looks interesting.

 I like to keep things simple. I like to multiboot too, but I always install in a single / partition, I usually just have one operating system which is my main operating system where I keep almost all of my files. Any other distros I might decide to try our usually don't have any files stored in them. I can always mount another file system if I want to access files in another partition.
To make that quicker you can use a mounting script, [COLOR=#666666][/COLOR][Making a script for mounting your other filesystems instantly]("http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script")

I hope something there helps,
Regards, Herman :)

---

### Post by VCSkier on 2007-11-13
> **Herman said:**
> I can make you a gag.com file with those icons and send it to you or help you make your own if you want. The instructions are already inside GAG's documentation, but there are a few little things about the instructions that make them hard to follow.
That would be great.  Either if you could give me some simpler instructions, or make me a new GAG package, if it wouldn't be too time consuming for you.  I tried looking at the instructions provided, but they were a bit complicated for me.  I'm slightly embarrassed by the fact, but I don't know anything about how to use Gimp.

I've been thinking about the /home partition issue some more, and I've decided it might be easier just to link the folders in my secondary distribution's home folder that I want shared to my primary distribution user's home folders.  For instance, /home/suse/Documents would simply link to /home/ubuntu/Documents, where the files would actually be stored.  Is this possible?  I think I've heard of this being done.  My only question then, is would I run into problems with the file ownerships and permissions?  Thanks again!

---

### Post by Herman on 2007-11-16
:) Hello again VCSkier,  
Please find the attached 'ENGLISH.COM.tar.bz2 file which you can use to overwrite the existing ENGLISH.COM file you have in gag_4.9/linux, and re-install gag with it.

Regards, Herman :)

Here is a screenshot for you,
 [IMG]http://users.bigpond.net.au/hermanzone/ScreenshotGAG.png[/IMG]
[IMG]http://users.bigpond.net.au/hermanzone/Screenshot_DOSBox_GAG.png[/IMG]

---

### Post by Herman on 2007-11-16
> I've been thinking about the /home partition issue some more, and I've decided it might be easier just to link the folders in my secondary distribution's home folder that I want shared to my primary distribution user's home folders. For instance, /home/suse/Documents would simply link to /home/ubuntu/Documents, where the files would actually be stored. Is this possible? I think I've heard of this being done. My only question then, is would I run into problems with the file ownerships and permissions? Thanks again! Hmmm, well I'll tell you what I tried once, I made several small partitions and had each one auto mounted (by listing in /etc/fstab), in my /home/herman/Documents directory and my Music directory and my Pictures directory and so on.  
The main problem with  having lots of separate partitions is, one will get full while another is empty. Although it is always possible to resize partitions with GParted, it's inconvenient to need to do that too often and it takes time.
Maybe a better idea would be to make just one data partition that all your operating systems can share. 
Just because everyone else mounts everything in either /mnt or /media doesn't mean it's compulsory.
For convenience you can make a mount point (directory) for it in your /home/username folder in each distro. 
Then edit /etc/fstab in each distro to have it mounted automatically on each boot-up. 
That should be a nice simple way to do it.

If you do have any file ownership issues then just use chown and chmod commands to adjust your file ownerships and permissions the way you want them, here are the best chown and chmod tutorials I am aware of so far, 
   Tuxfiles: how to use the chmod command, [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")
   Tuxfiles: how to use the chown command, [How to change a file's owner and group in Linux - 1.0]("http://www.tuxfiles.org/linuxhelp/fileowner.html")

Regards, Herman :)

---

### Post by VCSkier on 2007-11-24
Thanks so much for the new icons for GAG, Herman.  I'm now much happier with it.

I had some time to play with my setup yesterday, and so I created a new user for openSUSE (my secondary distribution), and assigned it to the same user id as my Ubuntu user (1000).  I then put symlinks in it's home folder pointing to the folders in my Ubuntu user's home folder that I want to access from both distributions.  I haven't had much time to test everything out, but I haven't run into any problems yet.  I think this will turn out to be quite simple, and will prevent the duplication of some files, which would result in the waste of some disk space (my disk space is rather limited).

Thanks for all the help!

---

### Post by Herman on 2007-11-25
:) Hello VCSkier,
I'm glad you like the different selection of icons.  :)

I already had Ubuntu Feisty and Gutsy installed in my first hard disk.
I decided to try our Open SuSe too, thanks to your reminding me about it.  I also installed Debian, so now I have four installs in my first hard disk.

My second hard disk has all my data in it now, I moved it from all over the place and got it all together in one big partition. (160 GB).

In each of my installations I have made a folder in my /home/username directory called DATA, and mounted my data disk in that. It's quite convenient having it right there in my /home/username folder.

Your idea sounds like it would work better than mine maybe, but mine's probably a little simpler to apply. I just wanted to try this idea out again to see how well it works. I guess there are lots of ways to do things. I have lots of disk space and not so much data. It's working well for me so far the way I'm doing it. :)

I found the mv -u command very handy for getting my files sorted out. The -u option to the mv (move) command makes it only copy the file to the destination if the file is more up to date than the file it will overwrite or if there's no file with the same name in the destination directory.
Sometimes files  still need to be checked by opening them too though, just to make sure. I wouldn't like to delete the wrong one.

That's one of the worst things about multiple booting, having files everywhere and not being sure which is the most up to date copy of the same file. :)
I certainly cleared a lot of junk and duplicate files out of my system at the same time! :lolflag:
It's almost all tidied up now.

Good luck with it and happy computering!
Bye for now, Regards, Herman :)

---

