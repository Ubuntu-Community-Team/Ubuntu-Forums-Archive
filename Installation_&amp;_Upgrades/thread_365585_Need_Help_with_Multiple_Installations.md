---
title: "Need Help with Multiple Installations"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by kringle on 2007-02-19
First off, I made the switch to leave Windows, except for games, since summer of 06.  I love Ubuntu!  While there was a small learning curve, I actually feel I know my system better.  That being said, here is my dilemma:

I have a dual boot system right now.  Windows XP on a serial ATA for my games, although I haven't booted into it for over a month, and an upgraded Dapper to Edgy install on a separate regular ATA drive.  I like having my Windows on a separate drive from my Ubuntu.  Now, I only have 5 gigs left on my ATA drive.  I went and bought another ATA drive, 250 gigs, to replace my old, not much space left 120 gig ATA drive.  All of my important stuff is on this 120 gig Edgy drive.  Here's what I was thinking to do:
1: Install my new 250 gig ATA drive on my secondary IDEE slot--set to master like my 120 gig on the primary IDEE slot
2:  Install Edgy, via a live Edgy CD, on this new drive, fresh install,not an upgraded version like on my 120 gig
3:  Move my home files over from the 120 gig to the 250 gig inside the new Edgy install
4:  Once I know I have all my important files on the new 250 gig, upgrade the Edgy to Feisty on the old 120 gig to experiment--being I'll have all my files on a safe Edgy install on a new drive

Questions:
1.  When I install the Edgy on the new drive, will GRUB have a problem, I'll overwrite the GRUB on SATA, with two Edgy installs?  Will I be able to tell the difference between the 120 gig install compared to the Edgy on the 250 gig drive?  Will it state Edgy hda and Edgy hdb or hdc on GRUB boot?  I really don't want to hose my XP install either, not because there is anything important in there, but I don't want to have to go through the reinstall, update, reboot, update, reboot Windows hell again...
2.  Is this possible?
3.  Am I stupid for going about it this way?
4.  I really want to put all my important documents on this new 250 gig and experiment on my old 120 gig--I might even remove the 120 later and try to build a home server using Ubuntu and LAMP stuff with an older computer I have laying around...

I hope I don't sound like a complete n00b here...thanks for the response...

---

### Post by tgalati4 on 2007-02-22
For day-to-day reliability you want to stick with Dapper Drake 6.06.  It will receive long term support and you will have less frustration when things don't work the way they are supposed to.  

You will probably have to edit your /boot/grub/menu.lst file to capture all of your operating systems.  Make a backup of menu.lst and keep it in your home directory.  That way when grub installs you will always have menu.lst to work from and compare to the new one.

I would do it the other way around:  Set up Dapper on the 120 GB drive, make a bullet-proof system on the older hardware (you can use it as a media server, Lamp server, just about anything).

Use the newer hardware to experiment with Edgy or Feisty.  Put your data files as a second disk in the Dapper machine.  Get another cheap drive to put in your newer desktop machine and make several partitions so that you can install Edgy Eft, Feisty  Fawn and Garish Goose. Don't forget a generous swap partition (4GB).  Then you will be styling.

---

### Post by kringle on 2007-02-22
Thank you for the response.  I've been using Edgy for over four months now and would never want to switch back to Dapper; however, I must be one of the few that has never had a problem with Edgy.  I just wanted to try Feisty.  What I did was install the new hard drive and made it a home disk.  This way I have a dedicated drive for all of my home documents.  I followed the directions at [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
, ignoring using the LiveCD part as I didn't have to unmount the drive since it was a separate drive and not a new partition.  In addition, I made the Ext3 partition on the new drive a primary and not a Logical as suggested in psychocats' tutorial.  Viola, I now have a 250 gig drive dedicated to my home items.  Now, I will probably create some partitions on my old 120 gig, so I can experiment with Feisty.

Thanks again for the response :)

---

