---
title: "[SOLVED] Trouble with Alternate CD"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by gimmejimmy on 2008-09-24
Hello, I'm trying to install Ubuntu on a PC with only 128MB so I downloaded the 8.4 alternate CD.  I triple checked the hash and it matches.  I've also tested the memory on the target PC and it returned no errors.  However during "Installing the base system" I got various messages about files(?) being corrupt.  Out of curiosity I made an ISO image from the CD to see if it was a bad burn.  The hash check came out ok, so the CD is probably good.  So I tried installing again and now it doesn't complain about any files but the "linux-generic" kernel won't install.  Should I choose another kernel?  The choices are:
linux-generic
linux-image-generic
linux-image-2.6.24-19-generic
none
Is it the download, the CD, the burn?  I've burned bootable CDs before on this burner (UBCD, UBCD4win, BartPE) Thank you.

---

### Post by lisati on 2008-09-24
Did you burn the CD as a disk image?

---

### Post by Sef on 2008-09-24
>  Is it the download, the CD, the burn?  I've burned bootable CDs before on this burner (UBCD, UBCD4win, BartPE) 

1) Did you burn the iso at 4x or less?

2) Have you checked that the disk is ok?  Go down to 'Check disk for errors' instead of installing.

---

### Post by gimmejimmy on 2008-09-24
I chose "Burn CD from image" in Nero Express.  Is that what you meant?
For the kernel I chose "linux-image-generic" and it installed fine.  It's also asked for a username and password and now that's done too.  Now it's stuck at 28% with the status "Scanning the mirror".  The keyboard lights are still responding so it probably hasn't hung.  I'm also downloading the non-alternate ISO, is that why it's taking long?

---

### Post by gimmejimmy on 2008-09-24
I burned it at 48x.  The "Check disk for errors" option tells me the CD is bad.  But I made a new image from the CD and the hash matched the original download, doesn't that mean that the CD is good?

---

### Post by lisati on 2008-09-24
> **gimmejimmy said:**
> I chose "Burn CD from image" in Nero Express.  Is that what you meant?
For the kernel I chose "linux-image-generic" and it installed fine.  It's also asked for a username and password and now that's done too.  Now it's stuck at 28% with the status "Scanning the mirror".  The keyboard lights are still responding so it probably hasn't hung.  I'm also downloading the non-alternate ISO, is that why it's taking long?

1) Some parts of the installation need an internet connection. 
2) If I remember correctly, when I used the alternate CD to install v7.04 on my laptop, it seemed to get stuck at 28% or thereabouts. I went away, had a hot coffee, waited a while. I can't remember exactly how long it took, but it did eventually come right. (afterthought: have a look at your hard disk activity light or your modem lights to see if they're actually doing something.)

---

### Post by gimmejimmy on 2008-09-24
It's past the 28% now.  It's been at "Select and install software" 6% for the past few minutes.  No HD lights but the CD lights are blinking.
I've been trying to follow the instructions here: [https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
Now I realize that I didn't see/select the "Install a command-line system" option.
> To install a base system, boot from any Alternate CD and choose "Install a command-line system." It is exactly the same command-line system on Kubuntu/Xubuntu/Ubuntu Alternate CDs. 
Should I do this over?  Thanks again.

---

### Post by Sef on 2008-09-24
> It's past the 28% now. It's been at "Select and install software" 6% for the past few minutes. No HD lights but the CD lights are blinking.

Since you only have 128 mb ram, it will take a while for that to finish.   Just wait and sit back.  It will take a long time.

---

### Post by robert shearer on 2008-09-24
> **gimmejimmy said:**
> I chose "Burn CD from image" in Nero Express.  Is that what you meant?
For the kernel I chose "linux-image-generic" and it installed fine.  It's also asked for a username and password and now that's done too.  Now it's stuck at 28% with the status "Scanning the mirror".  The keyboard lights are still responding so it probably hasn't hung.  I'm also downloading the non-alternate ISO, is that why it's taking long?

Do you mean that you have two machines connected to a router and on one you are installing ubuntu and at the same time on the other you are downloading an iso???

and someone correct me here but I think you need more than 128Mb of ram to run a gui so presumably you are installing a command line only system??

---

### Post by Sef on 2008-09-24
> and someone correct me here but I think you need more than 128Mb of ram to run a gui so presumably you are installing a command line only system??

To run Ubuntu decently, you need 512 mb ram.  128 mb ram could run Ubuntu, but it will run slow.  People have installed it on systems with less specs, but opening applications was based on minutes instead of seconds.

---

### Post by snowpine on 2008-09-24
> **gimmejimmy said:**
> Hello, I'm trying to install Ubuntu on a PC with only 128MB so I downloaded the 8.4 alternate CD.  I triple checked the hash and it matches.  I've also tested the memory on the target PC and it returned no errors.  However during "Installing the base system" I got various messages about files(?) being corrupt.  Out of curiosity I made an ISO image from the CD to see if it was a bad burn.  The hash check came out ok, so the CD is probably good.  So I tried installing again and now it doesn't complain about any files but the "linux-generic" kernel won't install.  Should I choose another kernel?  The choices are:
linux-generic
linux-image-generic
linux-image-2.6.24-19-generic
none
Is it the download, the CD, the burn?  I've burned bootable CDs before on this burner (UBCD, UBCD4win, BartPE) Thank you.

Hi Jimmy, you need 256mb to install Ubuntu using the Alternate CD.

---

### Post by gimmejimmy on 2008-09-24
Hello again, I stepped out for a few hours.  When I left it was at around 40% of "Select and Install Software" and when I came back it had failed.
1.  Can I just install manually since I've already installed the base system?
2.  Several people have pointed out that I don't have enough RAM, even for the alternate CD.  Do I need to get a different distribution?  This is my first try with Linux.  The target PC previously had Windows ME.
Thanks for all the replies.

---

### Post by snowpine on 2008-09-24
> **gimmejimmy said:**
> Hello again, I stepped out for a few hours.  When I left it was at around 40% of "Select and Install Software" and when I came back it had failed.
1.  Can I just install manually since I've already installed the base system?
2.  Several people have pointed out that I don't have enough RAM, even for the alternate CD.  Do I need to get a different distribution?  This is my first try with Linux.  The target PC previously had Windows ME.
Thanks for all the replies.

Hi Jimmy, the only distro I am aware of in the Ubuntu family that will install comfortably on 128mb of ram is Fluxbuntu. It's a little outdated and buggy, but I like it a lot. :)

For best performance, you want something designed specifically for old computers: DSL, Puppy, SliTaz, etc. 

My #1 recommendation though is more ram. 128mb is borderline for any modern OS (Windows ME is 8 years old).

---

### Post by gimmejimmy on 2008-09-24
I chose Ubuntu because I read it's good for newbies, but I think I can manage with something else.  I've heard good things about Puppy too.  Thing is I live with people who are VERY used to Windows and do not like (computer-related) change very much.  Would Puppy be a good choice?
Update:  The Ubuntu install is failing at the Software installation, but I ran the CD check again and this time it passed!  I think it's either my memory (memtest can't find anything though) or my optical drive messing up.

---

### Post by enthusiastic.sady on 2008-09-24
If you are new to Linux, Just a suggestion.
I have 128mb RAM. The setup cant even load in my system, dont ever think of the "live CD", It's great headache. Please increase you RAM to atleast 512 and try. I am also a sufferer. I have tried DSL, puppy Linux, Knoppix, Berry. But I cant even install Xubuntu (Alternate) or Fluxbuntu.

---

### Post by enthusiastic.sady on 2008-09-24
> **snowpine said:**
> Hi Jimmy, the only distro I am aware of in the Ubuntu family that will install comfortably on 128mb of ram is Fluxbuntu. It's a little outdated and buggy, but I like it a lot. :)

For best performance, you want something designed specifically for old computers: DSL, Puppy, SliTaz, etc. 

My #1 recommendation though is more ram. 128mb is borderline for any modern OS (Windows ME is 8 years old).
> My #1 recommendation though is more ram. 128mb is borderline for any modern OS (Windows ME is 8 years old).

Hey not "ANY", I have already used and run Windows XP, 2006 - smoooothly on my computer with just 128 mb of RAM !

---

### Post by gimmejimmy on 2008-09-24
@enthusiastic

Did you try the alternate CD, any luck there?  How was your experience with Puppy?

---

### Post by snowpine on 2008-09-24
> **gimmejimmy said:**
> I chose Ubuntu because I read it's good for newbies, but I think I can manage with something else.  I've heard good things about Puppy too.  Thing is I live with people who are VERY used to Windows and do not like (computer-related) change very much.  Would Puppy be a good choice?
Update:  The Ubuntu install is failing at the Software installation, but I ran the CD check again and this time it passed!  I think it's either my memory (memtest can't find anything though) or my optical drive messing up.

Hi Jimmy, I've only used Puppy a couple of times to test it out (my laptop has 256mb so I use Crunchbang instead). I think it is popular because most of the functions you need are right in front of you as icons on the desktop. So it is an intuitive "point and click" interface. 

Personally, I would choose Fluxbuntu over Puppy because it has access to the full Ubuntu software repositories. However the system requirements for Fluxbuntu are probably higher than Puppy, so it may be a trade-off in performance.

---

### Post by snowpine on 2008-09-24
> **enthusiastic.sady said:**
> Hey not "ANY", I have already used and run Windows XP, 2006 - smoooothly on my computer with just 128 mb of RAM !

Windows XP is not "modern"; it is 7 years old and Microsoft stopped selling it earlier this year (except for netbooks). Vista is the current version and good luck running it with 128mb of ram. :)

---

### Post by gimmejimmy on 2008-09-24
Ok, by my sheer stubbornness the installation has finally completed.  However, it wasn't the light version I was hoping for.  I wasn't able to do anything listed here:
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
Is there any way to get the install "lighter" without doing another install?

Edit:  Err, I don't know why that thumbs down icon is there.

---

### Post by robert shearer on 2008-09-24
> **gimmejimmy said:**
> Ok, by my sheer stubbornness the installation has finally completed.  However, it wasn't the light version I was hoping for.  I wasn't able to do anything listed here:
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
Is there any way to get the install "lighter" without doing another install?

Edit:  Err, I don't know why that thumbs down icon is there.

Your memory is too light to be able to run Ubuntu with the full Gnome desktop that comes with a standard install.
Other posters have suggested ubuntus with lighter desktops such as Fluxbuntu and other o/s like Puppy which run snappily on a system such as yours. 
I have Puppy on a laptop.. Pentium 1/233Mhz/96Mb Ram/3Gb h/d .. and find it quick and responsive.
On another older machine I use a Puppy version called macPup which has a Mac like dock . Worth a look ...
[http://www.puppylinux.org/downloads/puplets/macpup-dingo](http://www.puppylinux.org/downloads/puplets/macpup-dingo)

---

### Post by snowpine on 2008-09-24
> **gimmejimmy said:**
> Ok, by my sheer stubbornness the installation has finally completed.  However, it wasn't the light version I was hoping for.  I wasn't able to do anything listed here:
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
Is there any way to get the install "lighter" without doing another install?

Edit:  Err, I don't know why that thumbs down icon is there.

You should have chosen "install a command line system only." I think you can get back to a command line install by removing the ubuntu-desktop metapackage and all its dependencies; never actually tried it though.

Be aware that that page you linked to is a bit outdated and does not necessarily still apply to Hardy. Here's a more up to date tutorial: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

I repeat my recommendation to install something lighter than Ubuntu. :)

---

### Post by gimmejimmy on 2008-09-25
> You should have chosen "install a command line system only."
I didn't see that option, I was actually waiting for the installer to ask me about that but I guess I missed the part where I should have put it in.
Thank you for the up-to-date link!  When I work up enough courage I'm going to try that, Puppy, and the other recommendations.  The difficulty I had just installing Ubuntu makes me want to keep it for just another day.
If I got my RAM up to 384MB or 256MB would that be good enough to keep Ubuntu?
Edit:  More questions, I need to share files with a WinXP PC, do I need a FAT32 partition?  Do I make that during or after install?  The XP PC has NTFS, not a problem right?

---

### Post by robert shearer on 2008-09-25
> **gimmejimmy said:**
> I didn't see that option, I was actually waiting for the installer to ask me about that but I guess I missed the part where I should have put it in.
Thank you for the up-to-date link!  When I work up enough courage I'm going to try that, Puppy, and the other recommendations.  The difficulty I had just installing Ubuntu makes me want to keep it for just another day.
If I got my RAM up to 384MB or 256MB would that be good enough to keep Ubuntu?
Edit:  More questions, I need to share files with a WinXP PC, do I need a FAT32 partition?  Do I make that during or after install?  The XP PC has NTFS, not a problem right?

384Mb is a recognised minimum to run Ubuntu with a full desktop manager such as Gnome (default) 512 is better. So try it in steps. If 384 doesn't do it for you then try some more. RAM is a cost effective upgrade.

Puppy will run ,on your current 128Mb, as fast as Ubuntu with 512Mb so is a no cost option.Now that you know you can install Ubuntu and reinstall then why not try puppy and if it is not right for you add some ram and reinstall Ubuntu?

Ubuntu now handles NTFS well so should share files with WinXP fine.If you are concerned and want to be doubly triply sure then go ahead and use a Fat32 shared partition it won't hurt anything so why not.

---

