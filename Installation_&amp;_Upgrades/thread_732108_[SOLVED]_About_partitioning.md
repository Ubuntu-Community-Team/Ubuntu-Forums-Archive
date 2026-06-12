---
title: "[SOLVED] About partitioning"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Uzi304 on 2008-03-22
Well I have WinXP and now I would like Ubuntu on my PC also. The thing is, I need WinXP for my gaming needs and I have a 75 GB hard drive with about 25 GB freespace. Now I started the Ubuntu installer from the Live CD and I stopped when the partitioning part came up. If I want to keep WinXP which option should I choose and when it does partition what does it delete from the WinXP?

---

### Post by keratos on 2008-03-22
> **Uzi304 said:**
> Well I have WinXP and now I would like Ubuntu on my PC also. The thing is, I need WinXP for my gaming needs and I have a 75 GB hard drive with about 25 GB freespace. Now I started the Ubuntu installer from the Live CD and I stopped when the partitioning part came up. If I want to keep WinXP which option should I choose and when it does partition what does it delete from the WinXP?

When the menu comes up in ubuntu install, the bit about partitioning, you need to select MANUAL then an empty partition.

but FIRST, you need to run the partitioning tool, its called gparted from the menus. Or you can run it from a terminal window (accessories->terminal) and [as root user] enter: gparted.

You need to then partition your drive accordingly AND THEN install ubuntu.

This is no different than running partition magic in Windows, et.al.

If all that is over your head, then I would with no disrespect intended, suggest you stick with Windowze !t

You could always read the installation guide in ubuntu wiki that very kind developers took considerable time in creating, for users like yourself.

---

### Post by forestpixie on 2008-03-22
The install will not remove any of the win installation unless you explicitly tell it to do so.

What I would do is partition before you start the installer - as you have some freespace it should be fairly easy to do. In the system >admin menu is partition editor open that.

Once it's loaded you should have a representation of you're hdd, if you only have the 1 win partition it will be on the left and to the right will be the unallocated space. In that unallocated space right click and create an extended partition, click apply and let it do that.

Use the 1.5xRAM to work out swap size - now in the extended partition create 2 logical partitions - 1 needs to be formatted as ext3 and is as big as 25Gb - swap size, the second needs to be formatted as swap, click apply again and it will create them for you, they will be given names such as sda5 or hda5 make a note of that.

Now start the install again - pick manual and you will be able to use the partitions you have created, you will need to edit the biggest partition - when you get the second screen you need to give it a mountpoint of /. The installer will recognise the swap as such so you can forget that for the moment.

If during the partitioning you choose the win partition you will lose the information on it and there is every likelihood it will not be recoverable easily, make sure you have good backups before you start.

Sounds  a lot - but it's not really - I've assumed you know little about partitioning.

In future you might be better served using the absolute beginners forum.

---

### Post by Uzi304 on 2008-03-22
Ok thanks guys, I'll try that.

---

### Post by keratos on 2008-03-22
> **forestpixie said:**
> The install will not remove any of the win installation unless you explicitly tell it to do so.

What I would do is partition before you start the installer - as you have some freespace it should be fairly easy to do. In the system >admin menu is partition editor open that.

Once it's loaded you should have a representation of you're hdd, if you only have the 1 win partition it will be on the left and to the right will be the unallocated space. In that unallocated space right click and create an extended partition, click apply and let it do that.

Use the 1.5xRAM to work out swap size - now in the extended partition create 2 logical partitions - 1 needs to be formatted as ext3 and is as big as 25Gb - swap size, the second needs to be formatted as swap, click apply again and it will create them for you, they will be given names such as sda5 or hda5 make a note of that.

Now start the install again - pick manual and you will be able to use the partitions you have created, you will need to edit the biggest partition - when you get the second screen you need to give it a mountpoint of /. The installer will recognise the swap as such so you can forget that for the moment.

If during the partitioning you choose the win partition you will lose the information on it and there is every likelihood it will not be recoverable easily, make sure you have good backups before you start.

Sounds  a lot - but it's not really - I've assumed you know little about partitioning.

In future you might be better served using the absolute beginners forum.

TICK and ditto

your ever so diplomatic :-)

---

### Post by Uzi304 on 2008-03-22
[IMG]http://i198.photobucket.com/albums/aa307/Blazin_Uzi/Screenshot.png[/IMG]
I've gotten this far. I'm sorry I'm a newb but I'd really like to learn. So what do I do after this? And am I doing it right?

---

### Post by forestpixie on 2008-03-22
You have absolutely no free space whatsoever left in your win install - it will freeze up. 

Cancel all operations - at the moment you haven't committed - you need to leave room for the win partition then close the partitioner - boot win and defrag a couple of times. 

Reboot with the livecd - go back into the partitioner and resume from where you are - except you need to leave enough room within the extended partition for swap and lewave enough room for win.

If that doesn't make sense post now - before it's too late. Then come back I will keep an eye on this for an hour or two,

@Keratos : > your ever so diplomatic  - do my best :)

---

### Post by forestpixie on 2008-03-22
In the scrnshot attached I've ringed three buttons on the Post Reply screen - it makes life easier for everyone if you use them -

rather than have an image in a post - use attach 

if you want to quote someone use quote

If you have to give a lot of information - use code it  only goes to a certain size within a thread then and it scrolls - also it will be as wise as it needs to be - important if you have a long command string to get across

---

### Post by Uzi304 on 2008-03-22
How much room should I leave for the Windows partition?
This is how it originally looked. I've defragged and now I'm rebooting with Live CD.

---

### Post by forestpixie on 2008-03-22
Ok tell me how much ram you have and I'll give you some figures to work with.

---

### Post by Uzi304 on 2008-03-22
I have 2 gigs of RAM.

---

### Post by Pumalite on 2008-03-22
You can run anything you want then.

---

### Post by forestpixie on 2008-03-22
I'd make an extended of 20Gb, with a swap partition of 1 unless you hibernate then 2 give the rest of the room to / that will leave win with 5Gb to ruin.

---

### Post by Pumalite on 2008-03-22
I'd get an external hard drive to keep all your photos, music and movies. That way you free space in your internal drive. Your docs are safer too.

---

### Post by Uzi304 on 2008-03-22
Ok after I make the first logical partiition, I cannot make another one. What am I doing wrong?

---

### Post by forestpixie on 2008-03-22
> I'd get an external hard drive to keep all your photos, music and movies. That way you free space in your internal drive. Your docs are safer too. +1 or at least another internal.

> What am I doing wrong? no idea I can't see - what are you doing - post a scrn shot :)

---

### Post by Uzi304 on 2008-03-22
Ok I think I've got it but I want to make sure it's right.

---

### Post by Pumalite on 2008-03-22
He got it!

---

### Post by Uzi304 on 2008-03-22
Yay! Thank you all so very much. The Ubuntu community is definitely my favorite now. Alright so I'm going to go ahead and install now, I'll tell you how it turns out.

---

### Post by forestpixie on 2008-03-22
That looks fine as long as you're not hibernating. Once you've applied the changes and let it do it's stuff. Go back into the install - when you get to partitioning go manual.

It's probable that the partition 'new partition 5' will be sda5 afterwards. Choose that partition - edit it during installation  - pick the mountpoint as / , close that window and tick the format box for it. Then ok that - when it's nearly ready to install you will get a window telling you what it's going to do - it should say something similar to 

installing/formatting to sda5
swap on sda6

if it says it's touching sda1 you've done something wrong so go back and check.

Good luck - see you on the other side :)

---

### Post by forestpixie on 2008-03-22
> **Pumalite said:**
> He got it!

Almost like teaching - you can nearly see the light going on :D

---

### Post by Uzi304 on 2008-03-22
Actually the application process is taking a while so I can't install just yet. 
> Choose that partition - edit it during installation - pick the mountpoint as / , close that window and tick the format box for it.
Meanwhile, could you explain this a bit further please?

---

### Post by forestpixie on 2008-03-22
Yea it can take a while to do that - do not be tempted to turn it off half way through.

You pick manual partioning - and will gewt a list of your partitions it is likely to be
sda1 - ntfs - win install 
sda5 - linux
sda6 - linux swap

highlight the sda5 (if that is it's number) - at the bottom of the partitioner - some buttons - one is edit partition - click it

new window - details of the partition - bottom right there is a mountpoint button - click it and pick / , close or save can't remember

you will be back at partition list - tick the format box for that partition - at this point the list will change to say that sda5 has a mount point of / - there will be ticks in only that format box - it'll make sense when you see it

then carry on - eventually you'll get a window that tells you what it is going to be doing partition wise - check it - it'll say it's dealing with sda5 and 6

---

### Post by Uzi304 on 2008-03-22
Thanks for the help guys. Proud user of Ubantu posting.

---

### Post by forestpixie on 2008-03-22
Excellent - well done and welcome.

---

### Post by keratos on 2008-03-23
> **Pumalite said:**
> You can run anything you want then.

Yeah - Besides windowZe

:lolflag:

---

### Post by keratos on 2008-03-23
> **forestpixie said:**
> Yea it can take a while to do that - do not be tempted to turn it off half way through.

You pick manual partioning - and will gewt a list of your partitions it is likely to be
sda1 - ntfs - win install 
sda5 - linux
sda6 - linux swap

highlight the sda5 (if that is it's number) - at the bottom of the partitioner - some buttons - one is edit partition - click it

new window - details of the partition - bottom right there is a mountpoint button - click it and pick / , close or save can't remember

you will be back at partition list - tick the format box for that partition - at this point the list will change to say that sda5 has a mount point of / - there will be ticks in only that format box - it'll make sense when you see it

then carry on - eventually you'll get a window that tells you what it is going to be doing partition wise - check it - it'll say it's dealing with sda5 and 6

...and when you get to the bit about installing the boot loader into /dev/sda or /dev/sda5 MAKE SURE you select /dev/sda (no number after it). This will install the boot loader into the MBR of the disk. You then need o make sure that same disk is the first bootable disk in your BIOS.

---

