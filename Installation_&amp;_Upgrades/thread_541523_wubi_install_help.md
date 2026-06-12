---
title: "wubi install help"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by badapple on 2007-09-02
I,ve been searching for a week to find info/program to install linux/ubuntu from harddrive. Most were beyond my skill level at this time. I came across wubi finaly and it started to install nicely until this error came up" error informing the kernel about modifications to partition /dev/sdb5 --device or resource busy"

"the ext file system creation in partition #1 of scs1i (0,1,0) (sdb failed)
Its probably obvious to you that I run xp on c drive and am installing ubuntu on 2nd hard drive. At the installation for partitioning I selected guided partitioning (auto I guess). I really want this to work out for me so I can boot xp out the door, but I am wondering if its still too early to switch to linux as it being a bit too manually driven for my novice computer skills.   thanks in advance ,,,,,badapple mike
PS xp NTFS, d HD 32bit   :(

---

### Post by logos34 on 2007-09-02
Can you give us a little more info?

Are you trying wubi because you don't have a cdrom drive/can't boot from cdrom?  Do you have broadband internet connection?  System specs?  How big is sdb (D: )?

I think you're exaggerating the difficulty level of linux.  Ubuntu is universally regarded as the most user-friendly for newcomers.  You can do it!

If you don't have a cdrom or just can't boot from it, I'd try this howto:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

('Netboot approach' using XP and GRUB  or the 'CD Image approach').

---

### Post by badapple on 2007-09-03
Hello and thanks for your swift reply. I'm trying wubi because the new burner bought for my linux install copied the iso but it wasn't decompiled. 3 disks later i gave up and tried wubi. I do have broadband and my new combo dvd/cdrw was given to my girlfriend. 
my 2nd HD is 15gig , 2.6dual core intel cpu 1gig ram, ati video 256 on board card. more than enough to easily run any linux I'd need.
I was booting my computer and having a choice of windoze or ubuntu, but this mornings boot I had no option. 
I looked at grub but it all seemed a little to difficult for my liking.
hope this is enough info for you if not, ask specifics please. I do immensely thanks for the help.
I'm on my way to check out the link you gave me now.

---

### Post by badapple on 2007-09-03
tried wubi to no avail.... my ip addy isn't static. my server company (eastlink) told me if auto internet detection doesn't work then you're out o luck......seems they are right...........any other suggestions?

---

### Post by badapple on 2007-09-03
I've had enough of loading at least a dozen different programs to get this ubuntu to work.now my computer is acting up and just rebooting for no reason....going to give  "pclinuxos" a try. if too much trouble I'll try again in 10yrs like I tried about 10yrs ago for linux....way to much time and trouble. I hate windoze but at least its easy to install and run, thats why its soooo popular....goodbye, seeya in 10yrs or so...

---

### Post by logos34 on 2007-09-03
> I was booting my computer and having a choice of windoze or ubuntu, but this mornings boot I had no option.
I looked at grub but it all seemed a little to difficult for my liking.

oh, so you already had ubuntu installed (dual boot) and it was working until this morning?  But you no longer get the grub menu screen, is that right?  Do you have a cdrom to boot from the ubuntu live cd, or was the one you gave your girlfriend? Because if you can boot the live cd you could try reinstalling grub.  

Since you have two drives the only other thing I can think of for it not booting all of a suddem is the drive boot order got switched somehow.  Or maybe it's a hardware issue.

---

