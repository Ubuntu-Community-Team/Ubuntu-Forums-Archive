---
title: "No grub bootloader on install"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by thearne on 2005-02-03
Hi,

I am trying ubuntu 4.1 on an additional partition in my hard drive and sharing swap and home partitions with another Linux dist (Mepis).  I was not allowed to install the Grub bootloader where I wanted (in the /root), so I opted to finish without one.  

What is the easiest way to now install grub?  I currently have a working copy in the MBR that lists WinXp and my Mepis install.

Is there a way to get Grub installed in the /root of ubuntu?  (then I can just reference it from my existing Grub installation)

Thanks in advance!
Tom

---

### Post by thestarman on 2005-02-04
Tom,

   First, there's absolutely no reason to put it there!  The GRUB binary files are already installed here:  "**/boot/grub/**"  and if you have Mepis and yet another copy of Ubuntu, then you should have versions (not necessarily the same) of GRUB binary files in the same location of those as well.  Please keep reading past my rant here....
   I didn't like what Ubuntu did to my drive, because it literally lied to me :mad: during the install when it said it would install to (assume just) the MBR... the MBR is a single 512-byte sector at the very beginning of any drive, but instead, Ubuntu's install program placed ALL of the first and second stages of GRUB in my drive's first TRACK (erasing some valuable data I had stored there!) using about 16 more sectors to do so!  Neither RedHat nor SuSE nor any other install program have ever done that without first making it clear what they were about to do!!!  From now on, I will always 'back up' my whole first track before *playing* with new Linux installs!  OK, back to your problem:

   All you really need to do is correctly edit the GRUB menu you are presently using! :D   For example, I've been using GRUB on my own box for a long time, and after installing Ubuntu's GRUB to a floppy diskette (from which you can retrieve its entries from 8-) ), I then modified my present GRUB menu.  That file might be "**menu.lst**" or "**grub.conf**" but should always be in that folder I listed above: "**/boot/grub/**"  (it would rarely be anything but those two).  Here's where my new Ubuntu install is (logical drive on my Primary Slave -- 2nd drive):
[FONT=Fixedsys][B]
title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd1,6)
kernel          /vmlinuz-2.6.8.1-3-386 root=/dev/hdb9 ro quiet splash
initrd          /initrd.img-2.6.8.1-3-386
boot[/B][/FONT]

Your own Ubuntu location details will vary of course!  And maybe you're using the newer kernel too.

The Starman.

---

### Post by thearne on 2005-02-04
Thanks Starman,

I actually ended up reinstalling and was able to install the Grub file in the /root directory.  Then I edited the Grub file in the MEPIS  /root to include ubuntu as an option:

title <ubuntu 4.1>
rootnoverify (hd0,5) <example here assumes hda7 partition>
chainloader +1
boot


Works great!  Never have to mess with MBR on any new test. 

Now I have a new problem:  ubuntu does not accept my root password.  This seems insane to me:  I NEVER use different root passwords.  My quess is that I will be reinstalling - again.

Any alternatives?

Tom

---

### Post by Buffalo Soldier on 2005-02-04
[QUOTE=thearne]Works great!  Never have to mess with MBR on any new test. 

Now I have a new problem:  ubuntu does not accept my root password.  This seems insane to me:  I NEVER use different root passwords.  My quess is that I will be reinstalling - again.

Any alternatives?

Tom[/QUOTE]

Glad to hear you manage to solve the first problem.

About the root password, Ubuntu does not setup any root user on default. Whevener Ubuntu ask for a password, just enter the password for the user that you created during install. 

Ubuntu uses **sudo**. For more info you can refer to [http://www.courtesan.com/sudo/man/sudo.html](http://www.courtesan.com/sudo/man/sudo.html)

---

