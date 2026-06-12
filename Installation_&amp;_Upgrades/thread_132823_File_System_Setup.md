---
title: "File System Setup"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2006-02-19
Hi. I just reinstalled my system on a brand new 300 GB HD (Serial ATA - just $80 at Fry's this weekend :D ). I'm not used to having this much room on my Linux drive. Normally, I store all my media files (music, images, etc.) on a vfat drive that I keep around for testing out programs on Windows. But now I want to store such files on my Linux filesystem. 

So... where do I put them? I know that there's no "right" way to do this, but which directory is sort of the default for this kind of stuff? 

Thanks. :KS

---

### Post by amoser on 2006-02-19
I think that you should just keep the music files on your vfat drive.  That way you can use your music files in both windows and linux.  And there is not defalult directory for Music files in Linux

~Alan

---

### Post by Ocxic on 2006-02-19
I have my compsetup like this

15GB- root partition
20GB- /home partition
the rest is storage the you could split up anyway if you like, there are drivers for windows that will allow you to read a linux drive but i reccommend not trying to write anything to the drive, as it can cause file corruption. really your can set it up anyway you like.

---

### Post by jjf on 2006-02-19
I was going to start a new thread asking some of the same questions, so I'll just post them here.  I'm not trying to hijack the thread, but my questions seem pretty close to the original posters, so it seemed better to keep them both in one place.

My drive is much smaller (40 gb), but I plan to have 4 partitions: root, swap, home, win (a FAT32 partition that networked Windows boxes will be able to write to).  

First question -- What are the benefits of the ext file system?  Why not just do the entire home partition as FAT32?

Second question -- When I install a new program (say, the Scribus desktop publishing software), are its program files are installed on the root partition?  So I need to be sure to leave enough headspace for any programs I might want.

Third question -- How big should my swap partition be?  As large as my RAM?  Twice as large as RAM?  I've also read something suggestion I will get better performance by having swap in between root and home, so that a drive seek head usually has less distance to travel shuttling back and forth.  Did I correctly understand what the guy was saying?

Thanks.

---

### Post by quonsar on 2006-02-19
[QUOTE=jjf]What are the benefits of the ext file system?  Why not just do the entire home partition as FAT32?[/QUOTE]

fat32 does not support the file ownership and permissions linux requires. linux stores all user-specific program settings and user preference info in the users home directory, the /home directory cannot reside on a fat32 partition. simply won't work.

---

### Post by WelterPelter on 2006-02-20
My original question still stands. Clearly, some directories were not intended to store such files (even though, of course, you *could* do such a thing). For example /bin, /boot, /dev, and so on.

Or, put differently, in which directory would *you* put a jillion gigs of jpegs? I'm thinking of creating subdirectories in the /opt folder...

---

### Post by Herman on 2006-02-20
Hello, WelterPelter, it is  normal to feel a little bit disoriented at first when you are new to Linux and Ubuntu. Most people expect to find the old familiar 'My Documents', 'My Pictures', 'My Music' or the like already made for them somewhere.

Linux is a little bit different, it's more for the 'do-it-yourselfer's' types. It is normal (for most of us) to keep everything like that in our '/home/username' folder. That's the one we get to when we click 'Places', 'Home Folder' on our top panel. Inside that you can make your own folders and name them anything you like. If it makes you feel more 'at home', you can name them 'my_e_books', 'my_pictures', 'my_music', like you were used to. If you are tired of the same old boring folder names you can think up something new and different, any names you like will be fine.
You can even do a little decorating by clicking 'edit', 'backgrounds and emblems', and choosing a background color or even a background pattern for your home folder (and any others) if you like. 

Is this what you wanted to know? :-D (Herman)

---

### Post by WelterPelter on 2006-02-20
Thanks, Herman. I was thinking of putting them in the home folder, but that is usually the first to get nuked in any kind of re-install. I've been working with Linux for a few years now, so I'm a little bit used to the filesystem, but haven't really dug into this end of it. Getting the big drive and devoting it solely to ubuntu Linux shows the direction I'm going in... 


Probably I'll end up putting them in the /opt folder... or creating something like /music. 


I think it might be interesting to have some kind of "directories" sticky in this forum. Coming from Windows does make it all seem rather complex...

---

### Post by Herman on 2006-02-20
That gives me an idea!
 If I want to be able to 'nuke' my system and I have a nice big hard drive where space is not a problem I can make lots and lots of logical partitions; one for each different type of data I want to store.

I could mount each partition in seperate directories in my /home/herman folder to keep the desktop tidy.
Then I can 'nuke' my installation as often as I like without losing any data! 

(I don't understand what you mean by putting things in /opt. Usually when I nuke my system the /opt goes at the same time as everything else, unless there is something more here I need to learn). 

I already use the trick of having a spare copy of the whole installation (complete with added software and tweaks and customizations but without any data), waiting up at the other end of the drive. Every time I 'nuke' it I just copy back the spare one in a few minutes with GParted and away I go again, 'good as new'.

From now on I'll be able to 'nuke' my system and replace it again in a few minutes without even losing data!

Brilliant! Thank you, WelterPelter, you are the teacher, not the student!

---

### Post by WelterPelter on 2006-02-20
The main thing saving my files so far is that they've been on a separate drive, so when I reinstall linux, they're safe and sound... Your partitioning idea is cool. It could save the day.

---

### Post by WelterPelter on 2006-02-28
BTW - Does any person who actually knows what their talking about think this is a good idea? 

(that is, partitioning a huge hard drive so that when having to re-install Linux it doesn't erase the entire drive)

---

### Post by John.Michael.Kane on 2006-02-28
WelterPelter if you worried about a re-install of Linux keep your root/ from your home
run it like this will allow you to format just the root and reinstall just the root folder.
/=root
/home
swap 

!f you want to keep your music even more safe that is if your distro junky switching many times. you could put those files on usb harddrive.

---

### Post by WelterPelter on 2006-02-28
Are you saying put the /home on its own partition? And then keep music, photos, etc, in the home folder?

Sorry for the density here. I've just made so many mistakes with Linux over the years that I like to get things spelled out 12 different ways to make sure I've got it right before I go ahead and destroy my system again.

---

### Post by John.Michael.Kane on 2006-02-28
Yes you can keep you music in your "home folder". or on a usb harddrive. the main thing is to keep you root folder on it's on partition. that will allow you to rebuild should you have to install again.

---

### Post by WelterPelter on 2006-02-28
Assuming I've got the vitals backed up, how tricky would it be to create a separate partition more or less *right now*?

Also, what about all the other directories (such as /etc, /dev, and so on)? - Oh, right, they're all under the /.

Downloading the live CD as we speak...

---

