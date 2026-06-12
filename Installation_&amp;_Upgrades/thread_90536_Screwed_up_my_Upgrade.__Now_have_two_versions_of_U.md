---
title: "Screwed up my Upgrade.  Now have two versions of Ubuntu"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by Alatar on 2005-11-15
I was attempting to upgrade to Breezy from Warty by using the Breezy installation CD.  I assumed it would just upgrade, but in fact it resized my old partition to make space for a new one and installed into that  (I just took the default options).  Of course, once this had happened I realised my mistake and went back into the installer to remove the partition and resize my old partition back to what it was before.  Once I did this I could no longer boot as Grub was looking for the new partition.  After messing around for a while I decided my best bet was to reinstall again so that I could have access to the Grub config files.  Then I could remove the entries to Breezy, boot back to Warty, delete the Breezy partition and resize the Warty partition.  No such luck.  I can boot into Warty, but there are no entries in the menu.lst for Breezy.  How do I get rid of the Breezy partition and still be able to boot into Warty?

Assuming I manage this, should I upgrade using apt-get dist-upgrade?  How do I point it to use the CD so I don't have to redownload every package online?

Thanks,
Alatar

---

### Post by Alatar on 2005-11-15
Bumping before this falls off the page...

Anyone?

---

### Post by SSTwinrova on 2005-11-15
[QUOTE=Alatar]How do I point it to use the CD so I don't have to redownload every package online?[/QUOTE]

I can provide some knowledge on this part of the question  :)

First off, I've heard that it's not recommended to skip a release with a dist-upgrade (i.e. going from Warty to Breezy). That said, you should be able to put in a cdrom line in sources.list and then an apt-get update would find all the packages there. I've personally never upgraded from a CD, but I would think that the computer would be smart enough to pull packages from the CD as long as there are not newer versions available from any online repos. I know in Hoary there was a GUI method for adding new repos (and I think CDs were one of the choices), but that option may or may not be in Warty. If there isn't, check [here]("http://www.us.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom") for instructions on the command line way to add a CD. Hope this helps.

---

### Post by Alatar on 2005-11-16
Just an update if anyone else sees the same problems.  I resolved this by running the install again, getting as far as the partitioning manager.  I removed the new Breezy partition and resized the Warty partition.  Then I haed to make the Warty partition bootable and mounted as root.  I then had to save these changes and write to disk.  Of course, Ubuntu install now complained that the chosen partition was not emptry so I went back to the menu and skipped ahead straight to installing Grub.  I reinstalled grub, rebooted and was back to my original install.

Not a very user friendly upgrade!

---

### Post by yesplease on 2005-11-16
"Not a very user friendly upgrade!"

I hope you are yoking because you made this mess yourself :)

Anyway, I would do none of this repairing stuff, just back up and reinstall after such a major problem. I think this will save lots of time. Good luck.

If you still want to upgrade there is a howto in the sticky (first post).

---

### Post by missmoondog on 2005-11-18
Yep,
just tried this cd upgrade myself as doing it the other recommended ways screwed everything up anyway. this is the 4th computer i've tried to upgrade this week and not a single one has gone very well. at least this time i could boot to the desktop and get everything updated. seems to be working good, but now i have 3 operating systems on this computer. ubuntu 5.04 & 5.10 plus xp pro. is there a way to smoothly remove hoary? i will probably just wipe that partition because as the original poster said "not a very user friendly upgrade."

---

### Post by yesplease on 2005-11-18
@missmoondog: I saw your posts during this week and you have been working hard to upgrade 5 computers to 5.10.

However, my reply was to Alatar. Dont you agree that he caused the troubles himself if you read the first post in this thread? 

Anyway, instead of just blaming this or that I tried to give Alatar advice too.


Edit: Just saw your post in [http://www.ubuntuforums.org/showthread.php?p=501096#post501096](http://www.ubuntuforums.org/showthread.php?p=501096#post501096)
and that is not a proper way to speak to your dad, missmoondog ;)

Edit: I am not going to read all your posts, but the last ones are a kind of guerilla tactic; drop a complaint or a rant, and run. 

You will get more helpfull replies if you just ask one question at a time, provide info on what you did yourself to solve the problem, and give relevant info on hardware and software. Good luck!

---

### Post by missmoondog on 2005-11-18
unfortunately, my dad saw that post too. wow, did i get cussed out. was just coming back to edit that and apologize.

my edit is this:
after getting things somewhat straightened out and fully updated, i do believe that upgrade from cd worked perfectly!! YAY all to heck!!!!! 

i was going to post asking if i just edited my boot file and removed the 5.04 linux kernel section from that, would it not show up or blow up. i did and it didn't.

now, what i'm wondering about is all those items (14) i have in the installed (local or obsolete) section of synaptic? it was up to 37, bit i removed the other 23. a partial list of what is showing up in there is clam, firestarter, ffmpeg, gstreamer 0.8 and a few others. what exactly is that section for? not worried about removing clam or firestarter, but not messing with anything that has to do with audio/video!!

p.s.
in my dad's own words, "you're (me) going to learn this even if it kills your (my) brain cells!" 
i get my own brand new computer for christmas if i can get a grasp of this stuff!!

---

### Post by yesplease on 2005-11-18
Just a quick answer for now (from Windows), dont worry about local. 

**Edit**: You may want to read this, it is a summary of the directory structure: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html) and an informative site too.


Some dads would never notice that you have a brain too, so you could be worse off :)

---

### Post by missmoondog on 2005-11-18
that local/obsolete part is listed as one in the same. the exact wording of that section is:

installed (local or obsolete)

now it has graveman in that list also and i just installed that. actually burned a cd on this computer correctly too! i'm getting better.

---

### Post by yesplease on 2005-11-19
You may want to read this, it is a summary of the directory structure: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html) and an informative site too.

[http://www.tuxfiles.org/](http://www.tuxfiles.org/)  is excellent, it is well written and easy to read.

---

### Post by missmoondog on 2005-11-19
thanks.
had that in the bookmarks already. glanced through that chapter in the linux for dummies book i borrowed too. that is what we call tmi around here. tmi=to much information....LOL

---

### Post by yesplease on 2005-11-19
Well, I have that problemm too and I also notice that I am just scanning paging quickly instead of reading them properly (must be all that searching on the net),

I was curious why you need 5 computers, I have 2 an old one and a newish one. If I am too nosey you can just ignore this question :)

---

### Post by missmoondog on 2005-11-19
5 computers just seemed to have happened. work on other people's stuff, they junk them, come across deals on parts and what not. 3 of them are thrown together machines that i rebuilt with almost all new parts myself. now, my dad is making me learn linux (so i can really know how a computer operates)

besides, i just love computers. i want work in the field somewhere, someday

---

### Post by yesplease on 2005-11-20
I build my 2nd computer from parts too, and found that that isnt too hard when you are carefull. 

Years ago I tried Debian, but then you had to fill in rows of numbers in config files just to get your mouse working. Problem was that I didnt know that those config files existed, which numbers to put there, and found it too hard to find information. I could buy a new mouse but not a new videocard or monitor when I would break things.

Thats why it is a pity that some people have a hard time to install Ubuntu. Ubuntu is made to make install very easy so that you have a working system right away and can learn new things when you want to. Though I had a minor problem with grub, it worked for me.

---

### Post by Alatar on 2005-11-21
[QUOTE=yesplease]"Not a very user friendly upgrade!"

I hope you are yoking because you made this mess yourself :)

[/QUOTE]

I won't deny that I made my own mistakes, but I'll still stand by my comment that the upgrade path is not user friendly.  User friendly would be something along the lines of:

"There appears to be a prior installation of Ubuntu on this system.  Would you like to upgrade?"


Since most other OS's and distros provide thsi option I don't think its unreasonable.  In fact I took it so much for granted that I assumed the install was doing this as this has ben my experience on previous upgrades.

For full disclosure, while I am far from being a Linux Guru I am not a newbie either.  I've been installing and upgrading Linux distros for about 7 years now. Ubuntu is an excellent distro and the initial install is very user friendly.  The upgrade path is not.

Just to clarify.  You put a new version of the OS into your CDRom.  It does not offer you an upgrade path, but instead offers to either create a dual boot system or blow away your old system.  There is not even a recognition thet and existing version of the OS is present and a simple text file saying "Please use apt-get dist-upgrade instead".

Like I said, not user friendly.   I'm a proficient and technically competent user and I lost two days work over this.  In this scenario do you see me recommending this to a neophyte?  Let's not blind ourselves to the faults that exist.  If Ubuntu is to challenge Windows in the marketplace, these are the issues it needs to face.

Criticism can be constructive.

Alatar

---

### Post by yesplease on 2005-11-21
[QUOTE=Alatar]  Criticism can be constructive.

Alatar[/QUOTE]

@Alatar: It was not my intention to be cynical or to doubt your abilities. My reaction was triggered by the difference in your first post (where you seem to be saying something like 'I made a mess of this upgrade') and the post where you say that the Ubuntu dist-upgrade is not user-friendly. That is all. 

I agree that critisism can be constructive. However, in this case you may be wrong. There is, for instance the sticky thread that gives directions for first-time upgraders. Users that wait with the dist-upgrade will be notified of this option via the update-notifier. In my opinion that is user-friendly. An installation disk wont overwrite your existing installation, it will stop the installation. However, the installation can proceed when you do it on a new partition, and that is what you seem to have done.

Off-topic remark: unsupported customizations made by users can be the cause that upgrades will be problematic or will be incomplete, but this does not seem apply to your case.

---

