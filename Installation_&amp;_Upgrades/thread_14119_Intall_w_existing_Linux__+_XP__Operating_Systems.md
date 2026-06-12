---
title: "Intall w/ existing Linux  + XP  Operating Systems"
date: 2005-02-05
forum: Installation &amp; Upgrades
---

### Post by Adler on 2005-02-05
Hi All,

This is my first post here so go gentle. LOL.

I've a year of experience with SuSE 9.1 + 9.2 Pro and want to install UBUNTU as an alternative experimental OS. I see several advantages -- I just love the Live CD -- but can't seem to save my changes. So I thought that an install would be best. I do have the Install CD.

I'm thinking of doing an install of UBUNTU on my Notebook, but I've already three partitions:

/ SuSE 68% used - 7.06 Gb free
/ Windows C: 47% used - 7.84 Gb free
/ Windows D: 10% used - 11.02 Gb free

Does it look doable to try the install?

From what I've read re-partitioning active partitions can get really flaky. I'd like to put UBUNTU on and use it as my experimental Linux distro. The native (and only) Desktop is GNOME and their seem to be several native GNOME apps that I'd like to keep e.g. Evolution and another that I'd like to install e.g. Beagle -- [http://www.gnome.org/projects/beagle/](http://www.gnome.org/projects/beagle/) -- that's a cool tool! Plus APT / Synaptic is part of the UBUNTU package. I've got RC2 (Red Carpet 2) / YaST / APT, etc. going. But want to add UBUNTU.

Comments welcome!

---

### Post by llamakc on 2005-02-05
Good to hear you want to try Ubuntu, you'll be quite pleased. What is your question though? 
 
 Installing is doable if you want to repartition. Is their valuable data on your Windows D:\ partition? Move what you need to C:\ before proceeding and then install to there. If SuSe is handling bootloading for you, just remember to add a stanza for the new Ubuntu install.
 
 Good luck!

---

### Post by Adler on 2005-02-05
llamakc,

Thanks for the response.

On the D: Drive is nothing of real value -- that I've not already bacled-up to CDs -- and I can move it to the C: Drive. 

How would you proceed with a re-partition? This is where it gets scary for me. I understand that trying this with a Live Partition can get nasty. Will the UBUNYU Install CD do this for me? I've not decided to throw the ROM into my drive and then start a "Run Away Train" if you know what I mean.

SuSE does do the booting for me so what does

> just remember to add a stanza for the new Ubuntu install. 

mean?

Thanks in advance for your response.

---

### Post by Adler on 2005-02-05
Hi All,

I've formated my Windows D: Drive and now have the following set-up:

/Suse 15.77 GB - used, 6.83 Gb free
/Windows C: 8.10 GB used, 6.91 Gb free
/Windows D: 213 Mb used, 12.05 Gb free

So I've got a bit of space to put UBUNTU on. Any sugestions as to proceed?

---

### Post by llamakc on 2005-02-05
Here is my suggestion and it requires you explicitly KNOWING what D:\ really is on the hard drives layout.
 
 IF it is /dev/hda4 (because /dev/hda1 and /dev/hda2 are for SuSE and /dev/hda3 is for your Windows install) then go ahead and start the install. When you get to the partitioner use /dev/hda4 as your linux partition. You would be able to REUSE the /dev/hda? partition that SuSE is using for swap.
 
 Does that make sense? You won't be pushing data around on D:\; you'll be usurping it for Linux instead. FWIW it is easier to have a partition that is already set geometry-wise to install Linux on, which is what you have. Don't worry about resizing--you need to worry about just reformatting that partition to ext3 or reiserfs. 
 
 What I would do in the Ubuntu installer is choose to delete partition /dev/hda4 and then create TWO new partitions: one for SWAP and one for /. If you would like more help, just holler. Or holla. Or ask.

---

### Post by Adler on 2005-02-05
llamakc,

Thanks. I got brave and threw the Install CD in the drive and started the install process. I backed out basically because of the nature of partitioning. And I was a little confused about where to put UBUNTU.

I'm now doing a re-think about having MS XP at all.  I've got enough Linux experience to know what to save and what not, plus run the only thing that I need is Crossover Office to keep me up there with the MS .doc crowd. Everything Linux can be pulled down with the native UBUNTU Apt / Synaptic or I can add RC2 (Red Carpet 2).

The one thing in the install process that I didn't get was there was no option for a Dial-Up connection. I'd the option for Ethernet and Wireless, which is cool, but am stuck every once in a while with Dial-Up.

Thanks for getting back to me. As you can imagine there are a bunch of us out there with multiple OSs going AND all trying to get rid of MS.

Thanks again, for the comeback.

---

### Post by Adler on 2005-02-05
llamakc,

BTW, it seems that some of my buddies over at another SuSE Forum, which has had -- let's say, a few problems are -- watching my conversion.

I look forward to hearing back from you again.

---

### Post by lesleyb on 2005-02-07
[QUOTE=Adler]Hi All,

This is my first post here so go gentle. LOL.

I've a year of experience with SuSE 9.1 + 9.2 Pro and want to install UBUNTU as an alternative experimental OS. I see several advantages -- I just love the Live CD -- but can't seem to save my changes. So I thought that an install would be best. I do have the Install CD.

I'm thinking of doing an install of UBUNTU on my Notebook, but I've already three partitions:

/ SuSE 68% used - 7.06 Gb free
/ Windows C: 47% used - 7.84 Gb free
/ Windows D: 10% used - 11.02 Gb free

Does it look doable to try the install?

From what I've read re-partitioning active partitions can get really flaky. I'd like to put UBUNTU on and use it as my experimental Linux distro. The native (and only) Desktop is GNOME and their seem to be several native GNOME apps that I'd like to keep e.g. Evolution and another that I'd like to install e.g. Beagle -- [http://www.gnome.org/projects/beagle/](http://www.gnome.org/projects/beagle/) -- that's a cool tool! Plus APT / Synaptic is part of the UBUNTU package. I've got RC2 (Red Carpet 2) / YaST / APT, etc. going. But want to add UBUNTU.

Comments welcome![/QUOTE]


Hiya Adler

I'm interested in doing this too and I have XP/Suse 9.2

I read your later post where you'd reduced the D: partition down to about 213 MB.

What I suggest you do is go back into XP and free up a large proportion of that D drive by reducing the partition size.  That should then mark what you have freed up as free space in the partition part of the Ubuntu install.  parted had some bugs a while back and I am wary of relying on it to do this.

You need to decide how much you really need on that D drive for XP; 2% of 11 G is about 2G so give your self some room and go for 2.5G or 3G as the D drive's new size.  You MUST back up your D drive data before you do this.

Once you have that space free from Windows and unassigned to SuSE there are some other things to do.

Back up your SuSE /etc, /home and anything else you might have modified in SuSE.

If you have a spare HDD then rsync everything over to that.

Then start the Ubuntu install. 

When you get to partitioning the disk use the up/down arrows to scroll to the free space and make some logical extensions for the Ubuntu /, /usr, /home, /etc and so on.  Make sure you mark those for formatting and mount the filesystems you want accordingly.  

This is how I allocated space on a 15G drive and that's with a basic install off the CD. 

/dev/hda3             1.8G  111M  1.6G   7% /
tmpfs                 189M     0  189M   0% /dev/shm
/dev/hda1             447M   15M  409M   4% /boot
/dev/hda8             1.4G   17M  1.3G   2% /home
/dev/hda11            1.2G  8.1M  1.2G   1% /srv
/dev/hda10            1.4G  8.1M  1.3G   1% /tmp
/dev/hda5             3.7G  1.3G  2.2G  37% /usr
/dev/hda9             894M   12M  835M   2% /usr/local
/dev/hda6             1.4G   96M  1.2G   8% /var
/dev/hda7             1.4G   13M  1.3G   2% /var/log

So you need a fair bit of space for the /usr partition but obviously you could slim down the /tmp, not need the /srv, /usr/local, /var/log to squeeze in what you want to get out of an Ubuntu system and shoehorn it into the available space.

It's likely that Ubuntu will see the other partitions, the SuSE ones and the Windows ones, check that they are marked 'Do not use' and 'do not mount'.  This *should* avoid them being mounted or overwritten during the install process.  Then continue the install.  

Now as far as I understand GRUB you can tell it where to load what from.  I am no expert on either GRUB or LILO so we need one of those here.  Read around about it.  I intend to before I try exactly the same thing.

What I am not sure about is 'do you have one /boot partition for all Linux distro's on the system?'.  If so you don't need to have another /boot partition.

I also don't know how well Ubuntu's installation of GRUB works.  Will it recognise the existing GRUB and modify that to add the new boot info for Ubuntu?  What about if the kernels made by Ubuntu and SuSE have exactly the same name; how's that handled?   Will Ubuntu crash through and override SuSE's set up?

I don't know how well this part of an Ubuntu install has been tested and verified as safe and working.  And I don't know how well SuSER or any other distro copes in thsi situ either!

I do intend to deal with a mutliple Linux install and I am sure it is possible but I don't plan to try it without some serious reading and planning.

Hope some of this helps and I hope some people will come back with some answers.

Regards

LesleyB

---

### Post by Adler on 2005-02-07
lesleyb,

Nice to have chatted with you on IRC earlier today.

Let me try to digest what you sent along and get back to you.

Thanks for the comments and assistance.

---

### Post by Wok on 2005-02-07
Adler & Leslie, I've been following your discussion with interest, since I'm kind of in the same boat. I have Win98 and Mepis Linux installed already and would like to give Ubuntu a try, but am afraid it will mess up the Mepis bootloader or worse. I guess there would be ways to recover it, but I've spent a lot of time getting Mepis right and really don't want to go through it again. Some time back I tried installing Knoppix on a drive with Libranet and everything got kind of wrecked, so I'm kind of leery now.

I hope you'll let us know what happens if you take the plunge. I'll do the same. I keep hoping somebody who's done the deed will discover this thread and enlighten us all.

---

### Post by Adler on 2005-02-07
Wok,

Thanks for your post!

It seems that there are a lot of us that are looking to settle on different Linux Distros. My favorite to-date has been SuSE 9.1 Pro and then 9.2 Pro. Each has its advantages. But want to keep the MS OS on their systems. That is until we want to go completely Linux.

Right now UBUNTU looks good because of its native GNOME Desktop -- which has been really ignored in SuSE (that prefers KDE), native Evolution on start-up, APT /Synaptic.  And getting Beagle up and running, which seems to be a native GNOME app. Hmmm...

I know Red Carpet 2 (RC2), Yast, APT / Synaptic, etc. So building a Linux Box is pretty familiar stuff.

Out there in the Linux Universe I'm still looking for the ultimate install / boot process.  But above all, l want to get rid of MS.

The whole boot process with two Linux OS systems is still not really clear to me. I've backed everything up, but am still working my way through this. Plus keep MS XP.

Keep asking questions to keep this "bumped up" e.g. to keep it at the head of the Forum here.

Thanks again for your post!

---

### Post by Adler on 2005-02-07
Wok + lesleyb,

I keep coming back to this -

> I hope you'll let us know what happens if you take the plunge. I'll do the same. I keep hoping somebody who's done the deed will discover this thread and enlighten us all. 

Every where that I have searched I come back to the same sentence.

Is it really possible to have two versions of Linux and or  / MS on the same Box?

---

### Post by Xian on 2005-02-07
[QUOTE=Wok]I have Win98 and Mepis Linux installed already and would like to give Ubuntu a try, but am afraid it will mess up the Mepis bootloader or worse. I guess there would be ways to recover it, but I've spent a lot of time getting Mepis right and really don't want to go through it again. [/QUOTE]
The only thing you need is to make a spare partition, run the Ubuntu installer, and DO NOT install grub to the MBR or your Mepis partition. That's honestly all there is to it. Go through the Ubuntu installation and select a new partition for root, or "/". And then just share the swap file partition that Mepis uses with Ubuntu. When it comes time, simply install the bootloader to the Ubuntu "/" partition and you're done.

The installer will say something like, "Do you want to install grub to the MBR?"
And you will select no. 
Then it will ask where you want to place it.
You will say something like: /dev/hdax ("x" being the Ubuntu root partition #, i.e., hda4)

Then if Mepis uses grub go to your current /boot/grub/menu.lst and add Ubuntu to the list of options to be presented during the system boot. If it uses lilo then do likewise with the /etc/lilo.conf file and then run /sbin/lilo as root to add Ubuntu to the menu options.

All this is assuming that Ubuntu will be your fourth (after Win, Mepis, Swap) partition on your disk. If there will be more than four you will need to create an extended partition and then work from that by making further divisions.

---

### Post by Adler on 2005-02-07
Xian,

Let's pretend we want to do the same thing, but with XP and Suse. Go up through my original post.

BTW, don't I know you from somewhere else?

---

### Post by Xian on 2005-02-07
[QUOTE=Adler]Let's pretend we want to do the same thing, but with XP and Suse.[/QUOTE]
Makes no difference, save that I know SuSE uses grub and I'm only guessing at Mepis. SuSE will boot XP or Win98 in the same fashion. It all goes through the /boot/grub/menu.lst config. So again, as long as you have a separate partition for Ubuntu, share the swap file, don't have more than four partitions, and remember to install Ubuntu's bootloader to it's OWN root, then it is simply a matter of adding the Ubuntu entry to your present (SuSE) system.

Acutally, it's not even necessary to install Ubuntu's bootloader anywhere since you will be using another method to access its kernel, but this way it will make the installer happy and not throw a bunch of bright red text at you.

---

### Post by Adler on 2005-02-07
Xian,

Thanks.

We are stll looking...

---

### Post by Wok on 2005-02-08
[QUOTE=Adler]Xian,

Thanks.

We are stll looking...[/QUOTE]
 Xian, thanks for the excellently clear explanations. I think we're almost there. I'm feeling a lot more confident that a third OS install won't blow up what's already there.

Just one more thing, if your patience holds out:

The /boot/grub/menu.lst appears a little more complicated than just adding an entry. Here's the listing in mine of one of the Mepis versions and Win98:

> title MEPIS at hda2, kernel 2.6.7
kernel (hd0,1)/boot/vmlinuz-2.6.7 root=/dev/hda2 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,1)/boot/initrd.mepis 
savedefault

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1
savedefault

From your posts, I assume the Ubuntu bootloader won't write any of this? If not, which parameters have to be there? I'm wondering especially what the "chainloader" bit means.

---

### Post by Wok on 2005-02-08
Xian, thanks for the excellently clear explanations. I think we're almost there. I'm feeling a lot more confident that a third OS install won't blow up what's already there.

Just one more thing, if your patience holds out:

The /boot/grub/menu.lst appears a little more complicated than just adding an entry. Here's the listing in mine of one of the Mepis versions and Win98:

> title MEPIS at hda2, kernel 2.6.7
kernel (hd0,1)/boot/vmlinuz-2.6.7 root=/dev/hda2 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,1)/boot/initrd.mepis 
savedefault

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1
savedefault

From your posts, I assume the Ubuntu bootloader won't write any of this? If not, which parameters have to be there? I'm wondering especially what the "chainloader" bit means.

---

### Post by Xian on 2005-02-08
[QUOTE=Wok]The /boot/grub/menu.lst appears a little more complicated than just adding an entry. From your posts, I assume the Ubuntu bootloader won't write any of this? If not, which parameters have to be there? I'm wondering especially what the "chainloader" bit means.[/QUOTE]
You can ignore the entry with that chainloader line. We would only need to create something like that in linux if we were attempting to use lilo. I can see from the info you provided that Mepis uses grub and that is fine. As we will be working from your Mepis system we actually won't even be using the bootloader that Ubuntu installed to its own root partition. All we want is to get Mepis to provide Ubuntu as a boot option and then actually access the Ubuntu kernel. 

Okay, here's the only thing we need to know: What are the kernel and initrd.img file names that Ubuntu is using to load that system? The easiest way to find that out is to just look at the menu.lst file in your Ubuntu boot directory. So please access that partition in Ubuntu and navigate to:

/boot/grub/menu.lst

It's the same path as in your Mepis partition but obviously the information will be somewhat different. Let's use my own menu.lst file in Ubuntu as an example. We only need the relevant information so scroll down until you see something like this:

```
title		Ubuntu, kernel 2.6.8.1-4-686 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.8.1-4-686 root=/dev/hda6 ro vga=791 quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-686
```

Now we just need to transfer that info to your Mepis system in a format that it will recognize. This is really easy as all we do is just change around the sequence of what is already there. Doing that will result in the following:

```
title Ubuntu, kernel 2.6.8.1-4-686
kernel (hd0,5)/boot/vmlinuz-2.6.8.1-4-686 root=/dev/hda6 ro vga=791 quiet splash 
initrd (hd0,5)/boot/initrd.img-2.6.8.1-4-686
```

Just a quick note on the terminology: (hd0,5) is the same thing as saying /dev/hda6, (hd0,1) equals /dev/hda2, (hd0,0) equals /dev/hda1, and so forth. You just add one digit to the last numeral in the brackets to match your actual partition number. So after adding this entry to your /boot/grub/menu.lst file in Mepis, the entire relevant portion will look similar to this:

```
title MEPIS at hda2, kernel 2.6.7
kernel (hd0,1)/boot/vmlinuz-2.6.7 root=/dev/hda2 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,1)/boot/initrd.mepis 
savedefault

title Ubuntu, kernel 2.6.8.1-4-686
kernel (hd0,5)/boot/vmlinuz-2.6.8.1-4-686 root=/dev/hda6 ro vga=791 quiet splash 
initrd (hd0,5)/boot/initrd.img-2.6.8.1-4-686

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1
savedefault
```

You are done. Reboot and now Ubuntu will be listed as a boot option along with Mepis and Windows. Select it to boot into your Ubuntu system. Don't forget to change my partition numbers to what is on your disk and to use your own kernel and initrd.img files names. All of that is provided in Ubuntu's menu.lst file. 

Also remember that if you update your kernel in Ubuntu that you will need to make similar edits like this again in Mepis. Ubuntu will update its own grub configuration, but you need to transfer that over to Mepis so that the newer kernel will be used. Of course if you forget you can still boot Ubuntu since it will keep the old kernel as a back-up. But you won't be able to use the new kernel and initrd.img file until you paste their new file names to Mepis in the format you see outlined.

---

### Post by Wok on 2005-02-17
Well, I went ahead and did it. Close but no cigar. The good news is, the install didn't mess up any existing installations. The bad news is, no Ubuntu. Ubuntu shows up as an option in the Mepis bootscreen, but when I try to open it, I get a few lines of text scrolling too fast to read and then a black screen. I have to reboot by shutting off the power.

Tried to follow Xian's directions, but it looks like there's some little detail that went wrong somewhere.

Here's part of the menu.lst in the Mepis boot/grub file:

> title MEPIS at hda2, kernel 2.4.26
kernel (hd0,1)/boot/vmlinuz-2.4.26 root=/dev/hda2 nomce quiet splash=verbose vga=791 hdc=ide-scsi hdd=ide-scsi 
initrd (hd0,1)/boot/initrd.mepis 
savedefault

title Ubuntu, kernel 2.6.8.1-3-386 
kernel (hd0,4)/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda5 ro quiet splash
initrd (hd0,4)/boot/initrd.img-2.6.8.1-3-386

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1
savedefault

I'm pretty sure I told the installer to put the Ubuntu MBR into dev/hda5, which is the partition formatted to ext3 for Ubuntu. Hmm-- I see the Ubuntu entry is the only one that doesn't have a "save default" line. Could that be the problem?

I have to say, the installer is kind of a disappointment in an OS that aims at being easy. I have no problem with text-based, but the partitioning and boot options are really confusing, even to a somewhat experienced Linux user like me who has not learned much about the boot/partition aspects. Mepis installed flawlessly, Windows came up as an option in the bootscreen and worked fine. Maybe having 3 systems instead of 2 creates much more complexity, and I'd have the same problem with any third install attempt -- don't know. Anyway I trust the developers are looking at this as an area for improvement. Most Linux users are apparently using multiboot installations, so making it easy will affect a lot of us.

Seems like Linus is mature enough that it would be possible to make adding Ubuntu to preexisting OSs could go something like this: "Ubuntu has detected two existing installed OSs, Mepis and Windows. There is space available to add Ubuntu. Install Ubuntu at {partition} [yes/no]. You are currently booting using Mepis. Add Ubuntu to the Mepis bootscreen? [yes/no]" And so on, maybe allowing the user to make Ubuntu the bootscreen if "no" is the previous answer. In any case, the options now for where to put the MBR are confusing and no help is available during the install. At the very least, I hope that's fixed in the upcoming release.

But that's all in the future. For now, Xian or somebody, any idea of what went wrong? Should I just delete Ubuntu and start over? In which case what do I say when it asks where to install the MBR?

---

### Post by Xian on 2005-02-17
[QUOTE=Wok]Hmm-- I see the Ubuntu entry is the only one that doesn't have a "save default" line. Could that be the problem? For now, Xian or somebody, any idea of what went wrong? Should I just delete Ubuntu and start over? In which case what do I say when it asks where to install the MBR?[/QUOTE]
The "savedefault" line is just a method so that grub can boot the previously selected option.
I don't use it but there is no harm in adding that entry.

It actually doesn't even matter whether or not you installed Ubuntu's bootloader at all, since you are using grub on another partition, and therefore that is the only loader which will be used. You should just be able to point it to the correct kernel and initrd file in Ubuntu and boot your system in that manner. I always make a point to mention that the bootloader in Ubuntu just should not be installed to the MBR or any other partition besides the one that /boot resides under. Past that step it really makes no difference.

Your entry in Mepis for Ubuntu in the menu.lst looks perfectly appropriate, as long as the correct partition is being referenced and the proper kernel & initrd files are notated. You say that the Ubuntu /boot and root directories are on hda5, and so unless you have some reason to doubt that, I think it is safe to conclude that the entries for (hd0,4) and root=/dev/hda5 are correct.

Can you mount the Ubuntu partition in Mepis and get a look at what is in the Ubuntu /boot directory? It won't hurt to verify the file names in there as these can often get misplaced in the grub menu.lst. Do something like:

$ cd /<ubuntu mount folder>/boot
$ ls

Oh, and just to have a look-see, post the output of this ofter you su to root:

$ fdisk -l

---

### Post by Wok on 2005-02-17
Xian, thanks for staying with this.

Here's what I get in the Ubuntu /boot file:
    >  ptya4      rfcomm128  sdh9        ttyv9
admmidi1       hdj20       ptya5      rfcomm129  sequencer   ttyva
admmidi2       hdj3        pty

And this is the output from fdisk:

>   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10507     5295496+   c  W95 FAT32 (LBA)
/dev/hda2           10508      116031    53184096   83  Linux
/dev/hda3          116032      119048     1520568   83  Linux
/dev/hda4          119049      155061    18150552    f  W95 Ext'd (LBA)
/dev/hda5          119049      155061    18150520+  83  Linux


I don't get why it thinks hda4 is a Windows partition. It's an extended partition that hda five is on. Anyway is this the info you were wanting?

---

### Post by Xian on 2005-02-17
[QUOTE=Wok]Here's what I get in the Ubuntu /boot file:
    
ptya4 rfcomm128 sdh9 ttyv9
admmidi1 hdj20 ptya5 rfcomm129 sequencer ttyva
admmidi2 hdj3 pty

And this is the output from fdisk:

Device Boot Start End Blocks Id System
/dev/hda1 * 1 10507 5295496+ c W95 FAT32 (LBA)
/dev/hda2 10508 116031 53184096 83 Linux
/dev/hda3 116032 119048 1520568 83 Linux
/dev/hda4 119049 155061 18150552 f W95 Ext'd (LBA)
/dev/hda5 119049 155061 18150520+ 83 Linux

I don't get why it thinks hda4 is a Windows partition. It's an extended partition that hda five is on. Anyway is this the info you were wanting?[/QUOTE]
It doesn't think that hda4 is a Win partition. That is just the terminology method. My extended partition looks just the same. If it really thought it was a Windows system you'd see a different notation in the ID column.

Okay, as for the contents of your Ubuntu /boot folder we have a definite problem. That is where all your kernel, initrd, and config files should be located. That is why when Mepis goes there to load Ubuntu it is supposed to be able to grab the files it needs to run that system. The problem is that none of the required contents are listed.

Here is my /boot contents just for you to reference:
```
$ cd /boot
$ ls
config-2.6.8.1-5-686  initrd.img-2.6.8.1-5-686  System.map-2.6.8.1-5-686
grub                  memtest86+.bin            vmlinuz-2.6.8.1-5-686
```

Are you certain you looked in the right folder? You Ubuntu /boot folder?

---

### Post by Xian on 2005-02-17
Oh, and I don't know if you intended this or not but you see here:

/dev/hda4 119049 155061 18150552 f W95 Ext'd (LBA)
/dev/hda5 119049 155061 18150520+ 83 Linux

You've used basically your entire Ext partition for just Ubuntu. Meaning only that if you ever wanted to create another partition for storage or whatever you'd be unable to do so.

---

### Post by Wok on 2005-02-18
Xian, 

Ack. That was some kind of sloppy thing I did. Sorry. Here's the real thing:

> config-2.6.8.1-3-386  initrd.img-2.6.8.1-3-386  System.map-2.6.8.1-3-386
grub                  memtest86+.bin            vmlinuz-2.6.8.1-3-386

---

### Post by Xian on 2005-02-18
[QUOTE=Wok]Ack. That was some kind of sloppy thing I did. Sorry. Here's the real thing:[/QUOTE]
No big deal. LOL. I've looked over your /boot contents and the menu.lst file, and I can not see anything that looks to be in error. Basically, it should be working but it's not. I will continue to think upon this, but as of now I have no further suggestions. Your set-up is identical to mine, save the partition numbers and file names, and yet for some reason you are not able to boot the second Linux installation.

---

### Post by dheerajmk on 2005-02-19
[QUOTE=llamakc]Here is my suggestion and it requires you explicitly KNOWING what D:\ really is on the hard drives layout.
 
 IF it is /dev/hda4 (because /dev/hda1 and /dev/hda2 are for SuSE and /dev/hda3 is for your Windows install) then go ahead and start the install. When you get to the partitioner use /dev/hda4 as your linux partition. You would be able to REUSE the /dev/hda? partition that SuSE is using for swap.
 
 Does that make sense? You won't be pushing data around on D:\; you'll be usurping it for Linux instead. FWIW it is easier to have a partition that is already set geometry-wise to install Linux on, which is what you have. Don't worry about resizing--you need to worry about just reformatting that partition to ext3 or reiserfs. 
 
 What I would do in the Ubuntu installer is choose to delete partition /dev/hda4 and then create TWO new partitions: one for SWAP and one for /. If you would like more help, just holler. Or holla. Or ask.[/QUOTE]
 Hi please help me i have four partitions already 
c:
d:
e:
f:
i want to install ubuntu on E: without losing any data on any of these partitions 
also i already habe xp installed on D: and 98 installed on C:
please help i dont mind getting rid of 98

---

### Post by dheerajmk on 2005-02-19
Hi please help me i have four partitions already
c:
d:
e:
f:
i want to install ubuntu on E: without losing any data on any of these partitions
also i already habe xp installed on D: and 98 installed on C:
please help i dont mind getting rid of 98

---

### Post by Wok on 2005-02-20
> I will continue to think upon this, but as of now I have no further suggestions. Your set-up is identical to mine, save the partition numbers and file names, and yet for some reason you are not able to boot the second Linux installation.

Xian, thanks for trying. I suppose the problem could be something other than the boot setup, like video or something. Anyway, I think I'll try installing again and see if anything changes. I don't remember there being an option to make a boot floppy, but if I can find one I'll do that and see if it works. If not, I'll just wait for the next release and see if the problem goes away. In the meantime I'll probably check out Kanotix or  PCLinuxOS, which also sound pretty interesting.

Luckily Mepis suits all my real computing needs, so this is no emergency. I just liked Ubuntu's ideas and community, and wanted to spend some time checking out a Gnome-based distro with a great reputation. Maybe the next release will work out better.

---

### Post by pigpen on 2005-03-05
For what its worth, I have been able to get triple booting with the same setup as yours. I previously had Win98 and Mepis dual booting and just installed Ubuntu today and got it triple booting fairly easily. And used a similiar method as Xian described.

Since I already had GRUB in the MBR from the Mepis installation, I didn't want Ubuntu to overwrite my previous GRUB installation. So when installing Ubuntu, I had the Ubuntu installer install GRUB into my Ubuntu partition instead of the MBR.  After installation and rebooting, I booted into Mepis (or you can use any linux Live CD like Knoppix) and with a text editor, opened up the /boot/grub/menu.lst from the Ubuntu partition. Copied the Ubuntu menu text, then opened up my /boot/grub/menu.lst from my Mepis partition and pasted the text into it.  Saved the menu.lst and rebooted and that was it. I got the Ubuntu menu options in GRUB and was able to boot into Ubuntu.

One little problem I had was that I mistakenly saved my new menu.lst file with the wrong file name extension. I saved it as 'menu.1st' instead of 'menu.lst'. I had used '1' instead of 'l' in the 'lst' extension.

Also the Ubuntu version I installed was the just released Array 6 "Hoary" beta release, which came out a couple days ago (Mar.03.2005). Don't know if that makes a difference. Anyway this method should work with whatever distro you install, regardless if its Ubuntu.

---

### Post by dheerajmk on 2005-11-09
No dude the reason also for not replying for so long is because 
My comp crashed as the win xp booter got corrupted and I only had Ubuntu
which was not very helpful as I was not and am not very experienced with Linux
But I still want to learn and so please give me a solution to this
I want to install Ubuntu on a partition specially created for ubuntu without disturbing win xp or 98!!
Any solution ?
anyways pleaz cooperate as I am still learning
Thank you

---

