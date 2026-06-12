---
title: "Grub stage 1.5 gives Error 15"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by NomadOfNorad on 2005-09-26
I am attempting to do a clean install of Ubuntu 5.04 "Hoary Hedgehog" Release i386 on an old Micron Millenia Celeron, using the instructions at...

[http://www.howtoforge.com/perfect_setup_ubuntu_5.04]("http://www.howtoforge.com/perfect_setup_ubuntu_5.04")

...entitled [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=3]**ISP-Server         Setup -         Ubuntu 5.0.4 "The Hoary Hedgehog"** and I get as far as completing the second page of instructions before I get:

[B]GRUB Loading Stage 1.5

GRUB loading, please wait....

Error 15

_
[/B]
Where the **_** is the flashing underscore on the screen.

I've tried reinstalling several times, wiping and remaking the partitions each time, and get the same result. I've tried running the live-CD in rescue mode, following some of the instructions I've seen elsewhere, but it doesn't seem to help. I know that *Error 15* means that the GRUB install is not complete...

The above tutorial tells me to create four partitions on the machine with the following specs:

  50mb   /boot   Ext3
  1GB     swap   swap
  10GB   /         Ext3
  10GB   /var     EXt3
[/SIZE][/FONT]
I don't have as big an HD as he has in the example, so I've had to make the second and third partitions 4.6 GM each instead.

The first time I installed, upon reboot from the second page, the machine complained it could not find any active partitions, so I went back and checked and discovered I hadn't marked any of the partitians as bootable, so I redid things setting the first one as bootable.

Long story short, now I'm getting *Error 15* and cannot figure out which place to go to in my install via rescue mode to run grub-install or whatever the command was again...

I really need to get this system up and running *yesterday*, so I can set up a local IMAP server for myself.  (Long story...)

---

### Post by greenstar on 2005-09-26
This is something of a wild guess, but try setting the root partition to bootable. I've never had much luck with separate /boot partitions, they always fail to boot for me.:(  So I boot from / . Maybe just my luck or error. 

Also see my post about [checksumming]("http://ubuntuforums.org/showpost.php?p=372540&postcount=2"), this is what usually causes Grub errors for me.

greenstar

---

### Post by greenstar on 2005-09-27
Just noticed you're from Jax, my hometown. I grew up mostly at the beaches, graduated from Fletcher. Are you local?

---

### Post by NomadOfNorad on 2005-09-27
I did, actually, set the root partitian to bootable, all but the first time I created the install.  (On first install, the machine complained about not finding an active partitian and so couldn't boot...)  Haven't tried setting the other ones to bootable, though.

As per your second message here... Yeah, I've lived here in Jaguarville since I was probably 4 or 5 years old, which was around 1969 or 1970.  I'm actually over in the so-called Westside of town.

---

### Post by greenstar on 2005-09-27
Flashback: Cue Robbie Rose - "The Westsaaaahd is the Bestsaaaaahd":lol: 

Haaaahahahahahaha!!!!:D Sorry, couldn't resist.

greenstar

---

