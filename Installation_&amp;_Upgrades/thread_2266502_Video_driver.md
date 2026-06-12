---
title: "Video driver"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by akel3 on 2015-02-23
I want to install xubuntu [on my computer]("http://pastebin.com/1dQVW7AV"), [but seeing this as soon as the computer starts to boot from the dvd kinda discourages me]("http://www.youtube.com/watch?v=qbk_RKi1fY8"). It reminds me far too much of my first busted video card. After that it seemed to work just fine from the livedvd.
Well, I said, maybe the guys at ubuntu forums know what to do! So I went to the application manu, opened fire-
[IMG]http://i.imgur.com/4BiUyTi.jpg[/IMG]
Oh.
I know my computer isn't exactly top notch, but money is tight here and I quite frankly don't need a new one. This one works just fine to read, write, and play old games. The newest thing I've ever bothered to play is oblivion I think[SIZE=1] and morrowind is much better anyway[/SIZE].
Jokes aside the boot screen thing also happens when I try to go to a tty, which is annoying since my first reflex when everything ****s up is going to a tty and solve it from there.
Lastly, I tried to resize my windows partition to make space (My current instalation is old as sin so I will reinstall, and I want to have a data partition besides the windows and xubuntu ones) but I can't. GParted told me that I needed either ntfsprog or ntfs-3g, but I already had ntfs3g and ntfsprog didn't bring up anything on synaptic.

---

### Post by Mark Phelps on 2015-02-23
What version of Windows are you using? If it's Vista or newer, do NOT, repeat NOT, use Linux utilities to resize the Window OS partition.  Doing so risks corrupting the Windows filesystem and rendering it unbootable -- making it really hard to repair without specialized Windows repair tools.

IF it is Vista or newer, use the Disk Management utility to resize the OS partition.

---

### Post by ajgreeny on 2015-02-23
What graphic card do you have?

If it's **nvidia** you may need to boot using the nomodeset option. Boot to grub menu and hit E to edit; using cursor keys scroll to the line that ends with words including "quiet splash" and replace those two words with "nomodeset" (omit the quotation marks); usr Ctrl+X to boot.

Hopefully that will work and get you to a desktop from which you can install any Additional Drivers available to you.  After that the nomodeset option will not be needed

---

### Post by akel3 on 2015-02-23
> **Mark Phelps said:**
> What version of Windows are you using? If it's Vista or newer, do NOT, repeat NOT, use Linux utilities to resize the Window OS partition.  Doing so risks corrupting the Windows filesystem and rendering it unbootable -- making it really hard to repair without specialized Windows repair tools.

IF it is Vista or newer, use the Disk Management utility to resize the OS partition.
Windows XP. half because of my hardware and half because it's the better for old games.


> **ajgreeny said:**
> What graphic card do you have?

If it's **nvidia** you may need to boot using the nomodeset option. Boot to grub menu and hit E to edit; using cursor keys scroll to the line that ends with words including "quiet splash" and replace those two words with "nomodeset" (omit the quotation marks); usr Ctrl+X to boot.

Hopefully that will work and get you to a desktop from which you can install any Additional Drivers available to you.  After that the nomodeset option will not be needed

Yeah, I have a nvidia chipset ( [http://pastebin.com/1dQVW7AV](http://pastebin.com/1dQVW7AV) ).

---

### Post by akel3 on 2015-02-23
I used the boot options to boot with nomodeset and the loading screen still makes that, but I haven't had the monitor go loco again. Maybe it was a one time thing.

EDIT:Wait, I expected this message to join the last one autimatically, and now I can't delete it, could some admin to the honors?

---

