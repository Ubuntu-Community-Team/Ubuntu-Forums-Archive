---
title: "Frustrated with installation…"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by shaynaynay on 2005-04-19
Well, that is what happen, when you tell a newbie to install Linux.  ](*,) 

Hi everybody.
My name is Guy, and I'm from Israel.
I want to install Ubuntu, so I read a little in this forum, saw you are excellent in solving peoples problems (computer wise)…

Let me describe you my problems:
I have 2 physical Hard Drives:
Master: 2 partitions, C and D (C has win xp pro). Both NTFS.
Slavew: 2 partitions, "I" and H. Both NTFS. H is empty, I want to install Ubuntu to it.
You can see it all in [.:: HERE ::.](http://img256.echo.cx/img256/4979/disks3zp.jpg)

I'm running to rescue disc, and then QTPARTED.
Then I go the H, and formatting it to ext3.
It all seems to go well.

Then I run the Ubuntu installation.
In the partitioning part, I need to select the drive to install to, right?
Well, I got H shown as ext3 (#1 in the following screenshot)…
And I got a weird "free space" on hda1 (master, #2 at the screenshot).

[.:: Screenshot ::.](http://img256.echo.cx/img256/1743/disksqtparted6nq.jpg)

Then I got stack. No matter what I try, I can't install.
He yells that he doesn't find root drive, or something like that?...
Plus, what is this Free Space? I know according to [.:: THIS ::.](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html) guide that I shall have this Free Space, but I can't manage to create it. (Only when resizing H drive, but that's something I don't want to do, 'cause H is dedicated to Linux. And I read in this forum that it's good to format H to ext3, right?).

Anyway- I'm sorry for my English, and from the length of this doc.
I will be thankful to the one that will be able to solve my problem.

Thank you very much,
Guy.

---

### Post by bored2k on 2005-04-19
[QUOTE=shaynaynay]Then I got stack. No matter what I try, I can't install.
He yells that he doesn't find root drive, or something like that?...
Plus, what is this Free Space? I know according to [.:: THIS ::.](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html) guide that I shall have this Free Space, but I can't manage to create it. (Only when resizing H drive, but that's something I don't want to do, 'cause H is dedicated to Linux. And I read in this forum that it's good to format H to ext3, right?).

Guy.[/QUOTE]

Well, you already have your ext3 space, but you need to assign a / [root] mount point. So on the partitioning step, select your ext3 partition, and there should be an option refering to its mount point, once you find it, select "/" as a mount point [its in the menu, you don't have to write it]. Once that is done, select finish partitioning and I think you'd be good to go.  If it doesn't work let us know.

And by the way, Ubuntu Warty is getting old, you might consider upgrading to hoary;)/

---

### Post by shaynaynay on 2005-04-19
If you could only see the smile on my face  :) 

The installation process was quick and good...

but suddenly:

> 
[COLOR=Red]Fatal ERROR!![/COLOR]
[COLOR=Blue]Unable to install Grub in (hd0)[/COLOR]
Executing 'grub-install (hd0)' failed
This is a fatal error


 :neutral:   ](*,)  

Why?? Why is that?
Than I tried to install LILO, but I noticed that I choose to install it to **hdb**  which is not bootable. LILO installation went well.
It told me to remove the disk and it will reboot.
I did so, and it rebooted to Windows (because hdb is not bootable).

Now what? all from the top? erase all? what with the LILO?

---

