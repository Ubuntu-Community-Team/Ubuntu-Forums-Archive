---
title: "Can't Install Packages in Maverick (10.10)"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2011-02-04
I decided to give a new download of Ubuntu 10.10 a chance.  It went on fine,
I even installed VirtualBox with noi problem, But I am light on assessories,
particularly gimp.  I tried the Ubuntu Software Center, then I tried the Synaptic Package Manager for this and other packages, and guess what?  I kept getting errors like this:

[B]dpkg: failed to read on buffer copy for copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/B]
I even found a link that showed how to include gimp on 10.04 or 10.10 with a few command line statement, and I thought that would fly, but I got the same error again.  Another problem is that my monitor keeps fading to a **sort of blue-gray color indicating the processor is having trouble keeping up**, but I have only FireFox running, and the [B]keyboard locks up after after just a a smaill handful of charactrers are typed, then after about 10 seconds or so, the keyboard buffer flushes to the screen.
[/B]
This certainly is not typical of earlier Ubuntu versions, and I wonder if anybody else has similar problems or knows the cause and cure.

I am down to the point of asking myself, what is so urgent with the Ubuntu developers that we are having more and more conflicts between hardware and software to resolve with each new release?  And that they are pulling more and more packages out of the LiveCD in order to make room for something that is bulking up in some other manner?  What are you people up to, make Ubuntu more like Windows with coming releases?  If I wanted Windows, I would stick with or get a newer version of Windows.  Linux is suppose to be a swift greyhound compared to the panda that Windows is

---

### Post by labinnsw on 2011-02-05
[See if this works]("http://ubuntuforums.org/archive/index.php/t-389997.html")

---

### Post by oldefoxx on 2011-02-10
Okay, This is what I have so far:

I didn't just wait for a reply, I kept trying things.  I finally decided to see what would happen if I just reinstalled 10.10, but I wanted to keep my account settings.  No trouble if you pick manual partitioning and elect not to format the drive.  But because I have two other installs on two other partitions, I felt I had to protect the /home folder and contents on these as well.  I won't explain all this again, these are the steps I followed:

$ sudo -s
$ Password:
# mkdir /media/a1
# mkdir /media/a2
# mount -t ext3 /dev/sda1 /media/a1
# mount -t ext3 /dev/sda2 /media/a2
# mkdir /media/a1/rhome
# mkdir /media/a2/rhome
# mv /media/a1/home/* /media/a1/rhome/
# mv /media/a2/home/* /media/a2/rhome/
# dir /media/a1/home           'just to be sure
# dir /media/a1/home                ditto

if the two /home folders are not empty, check your work.  You can also check the /rhome folders and make sure they have the contents moved.

If the /home directories are there but empty, you need to delete them,
which you can do like this:

rm -r /media/a1/home
rm -r /media/a2/home

Now you have no hindering /home folders to worry about for the moment.
Unfortunately, this elaboration is because Linux, like Unix, has no rename feature.  There are also difficulties without the /* and / at the end,
which from a syntax standpoint, makes to sense.  But what is shown works.

So after you install to a different partition, in my case /dev/sda3, you have to set the home directories back for the other two.  Like this:

# mkdir /media/a1/home
# mkdir /media/a2/home
# mv /media/a1/rhome/* /media/a1/home/
# mv /media/a2/rhome/* /media/a2/home/

You can delete the two /rhome folders when finished. but make sure the contents did move back to the /home folders first.

So anyway, I got through the install okay, and decided to do the Update Manager first before messing with VirtualBox install.  And I got reports from the Update Manager of possibly a defective hard drive.  So I ran fsck -f to see what got reported, and I learned that an inode came up with a short link, which could be ignored or not.  I chose not to ignore it and fsck died with a bad status.  Somehow the inode and the earlier reported problem of a buffer segment in an input/output buffer seemed collected.  But an inode is likely to be a software glitch rather than hardware, so how would I get around this?  Now as primitive as some thinking that the MSDOS/Windows program of CHKDSK is, they stick to it because it is about the best thing they have.  Only it won't work with non-MS file systems.

What I was pretty much left with was trying to do a full format over again. Nobody has a tool for doing a partial format, and quick format is nothing like the same thing.  But I wanted to keep my accounts that I had on /dev/sda3 as well, expecially since I had some important VDI files on it.  So I used this method:
# mkdir /media/a3
# mount -t ext3 /dev/sda3 /media/a3
# mount -t ext3 /dev/sda2 /media/a2
# mkdir /media/a2/home3
# cp -r /media/a3/home/* /media/a2/home3/

I slept while that long process went on.  Then I started the 10.10 install to /dev/sda3 manually again, but this time I indicated that format needed to be included.  A royal pain in the neck, but it got me passed that inode
defect with no problems.  Then to put matters back to norm, I copied two ways:
# cp -r /home/* /media/a2/home3/
# cp -r /media/a2/home3/* /home/

The first copy is to take the consequences of that latest install and make them part of what was retained, then copy the whole cabootle back to my present accounts.

Now that took care of doing my updates and being current for the moment, but something is really messed up with FireFox.  I have interconnect connectivity as I can manually ping and get replies, my wired or wireless connections show up right, but FireFox tries to launch, but keeps failing.  I put the install disk back in, and it either gives me a checkmark if I have a network connection or an X if I don't.  I was getting Xed, but I played with the router connections for a bit and that got taken care of.  In fact, I'm booted back up under 9.10 on sda1 to connect and write this, meaning I have a network connection, but 10.10 plus that upgraded for FireFox seemed to be messed up somehow.

Unfortunately, I looks like the LiveCD disk requires a wired connection (it ignored the wireless one), There is only one provided web browser that I know of, otherwise I could try a different path, and there is no simple way I know of to back up one package with FireFox and see what happens.

Suggestions and fixes would be welcomed.

---

