---
title: "Trying to learn linux"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Aim9b on 2008-04-11
Hi All,
I'm trying to set up a box to learn linix/perl. I installed Ubuntu Server & thought all was well, but then I didn't have a gui desktop. Also I was told Xubuntu was a better fit for my "antique" box. So I tried installing it, but I can't seem to "see" the cdrom.  Being a complete newbie.. here's what I know....cat, ls -a |more  & thats about it.  The only book I have pretty much assumes a gui interface.

I have a line in etc/fstab the refers to a dev/hdb  /media/cdrom0 
I assume ths mounts the cd-rom drive, but I can't do a dir or ls on it.
The best I can get is a "Total 0" line.  Can someone educate me so I can move on. Thanks, -Sidewinder.

---

### Post by David Robertson on 2008-04-11
What's your box like? In particular how much memory?

---

### Post by Pumalite on 2008-04-11
This might help:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)
And here are some tutorials for Linux in general:
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by Aim9b on 2008-04-11
My box is an old Compaq Proliant Server, 333mhz, 192mb RAM, 8gb Raid disk, Floppy, CD Rom, not sure what video card.  It's old & slow, but should work for teaching my "old & Slow" brain.  ;-)

---

### Post by Pumalite on 2008-04-11
You can probably get 6.06 in there.

---

### Post by Aim9b on 2008-04-11
I had 7.1 ubuntu server on & running, it's just that when I tried to overlay Xubuntu I can't seem to see the cdrom. Every thing I find to "help" assumes a gui desktop, so I was trying to get to one.
Plus, I've been told xubuntu is a smaller "lighter" linux. thanks.

---

### Post by Aim9b on 2008-04-11
I think my problem is in the mount command.  Thanks for the tutorial links they offered some great help.  I can't try them till I get home, but then all I'll have is dialup which makes conversing here, a real pain.  ;-)

---

### Post by Pumalite on 2008-04-11
Xubuntu is a great light Desktop, but I thought you wanted a Server and learn to use one.

---

### Post by Aim9b on 2008-04-11
Sorry about the confusion...I thought I NEEDED -server because of the raid box I was putting it on.  Actually all I need is something to run linux & perl.  I'm hoping this will teach me enough to know if I need server at some future point.  I'm a total ?nix newbie & really hate windows. This seemed like the path to take.  My employer is getting more & more involved in linux (albiet under the covers) so I want to be ready when the light dawns on the brass.  ;-)

---

### Post by Aim9b on 2008-04-11
Also, I posted an earlier question the went a week with no replys. I was about to give up onthis site when I decided to re-post based on the progress I'd made so far.  Thanks for the help...I think I'll stick around ro a while.

---

### Post by Pumalite on 2008-04-11
This is it then:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
(Alternate)

---

### Post by Aim9b on 2008-04-11
That's the one I downloaded & burned (Both the Live & the Alt), & I can't seem to get it to run.  When I run "sudo apt-get install xubuntu" or any one of 7 million syntax derivatives I get a not found message.  I'm assuming it's due to my cd mount problem.  My only book assumes a gui. Can you offer the correct command-line syntax for the mount & install.  Thanks.

---

### Post by Pumalite on 2008-04-11
You have to burn the iso, as an 'image', at 4x or less to a CD-R, check CD integrity after burn and before install when booting from it.

---

### Post by Irony on 2008-04-11
Ubuntu Server doesn't have a gui, you need the desktop cd for that - I suppose you could install a gui on it by doing apt-get install somegui

---

### Post by Aim9b on 2008-04-11
I'll check the CD integrity, but I used the same process to dwnld/burn the server cd.  Also, after installing server, I tried to install a desktop on top of it, but again, it couldn't find anything.  I tried the following...
sudo apt-get install ubuntu-desktop
sudo apt-get install desktop
sudo apt-get xubuntu-desktop
and several xorg things that I can't remember.
 how do I know if the apt-get is looking ON-LINE, or at the CD?  
On-line is not an option for this box just yet.
I tried mount /media/cdrom0 but it said something about not in fstab or mtab, when it actually IS in the fstab as dev/hdb    /media/cdrom0  noauto,user,.....

That first install was soooo easy, I guess I'm making up for it now.  ;-)

---

### Post by Pumalite on 2008-04-11
If you don't have Internet, you can't install a Desktop or download the iso.

---

### Post by Aim9b on 2008-04-11
I download & burn it on my laptop here at work.  That's how I'm talking to you now. When I get home, I attempt to install from the CD. It worked fine for ubuntu-server. However, I seem to have lost my access to the cdrom drive.  The only thing I can think of is that under the original SCO Unix, the cd was already mounted & the ubuntu-server cd just took off & installed when I asked it to. I can run server now, I'm just not smart enough (yet) to mount the cd & install xubuntu or a desk top.

---

### Post by Aim9b on 2008-04-14
**[SOLVED..Well Maybe postponed] ** OK, thanks to everyone for the help. You can close this thread or whatever it is you do, since in my attempt to determine the memory slots available, the position of the CD-ROM (primary/secondary, master/slave, etc.) I discovered a hole poked into the ribbon (data) cable for the CD-ROM or floppy, etc.  And since parts for this old box are rare, it'll be a while before I can resume my linux/perl education.   Ihave a backup, I'm going to see if it's usable.
Thanks again...I'll be back in a few days with more opportunities.   ;-)
Aim.

---

