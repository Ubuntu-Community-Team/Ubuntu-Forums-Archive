---
title: "Can GRUB be repaired/installed from the 'grub rescue&gt;' prompt?"
date: 2014-07-09
forum: Installation &amp; Upgrades
---

### Post by betlog-hax on 2014-07-09
From time to time I use partition manager to copy a partition to another drive, sometimes it's a linux root system.
Typically I'm cloning a structure like this, so I need to edit the new GUIDs into /etc/fstab too:
/sda1 - swap
/sda2 - / - the active OS
/sda3 - / - space for OS backup/testing/partition expansion - usually left unformatted 
/sda4 - /home

After I boot the new drive it invariably finishes up on the prompt:
grub rescue>

**Is there a simple way - from this prompt - to reinstall GRUB and get it booting again?**
No, I do not mean downloading a rescue ISO and the application to burn it to USB, and then booting USB to fix it... I mean rectifying GRUB from the rescue grub prompt directly.

Also: why on earth does the kubuntu live bootable image not include one of the GUI based repair tools accessible from it's menus? That would seem to be an obvious inclusion for what is so often used as a recovery tool.

---

### Post by Bashing-om on 2014-07-09
betlog-hax; Hey, - and a Welcome to the forum.

Yeah, doable !
You may have to do some seeking from the grub > prompt [ ls -la (hd0,mdsos2 )or further ls -la (hd0,msdos2)/], and so on to find the proper parameters.
Do something like this:
Boot to that grub > prompt; press 'c' key for a command line, and enter:
```

linux (hd0,msdos2)/vmlinuz root=UUID=7dd23297-30ea-417a-8f69-3e2df76f3192 ro
initrd (hd0,msdos2)initrd.img
boot

```Where the UUID matches that of the partition that the OS is installed onto.
Once booted into the operating system maybe all that will be required further is to update grub.
```

sudo update-grub

```
To set all to a good state. - may also require editing /etc/grub.d/10_linux with the correct UUID for the 'root' partition (??).

[INDENT][INDENT]just tell it what ya want it to do, it's 'buntu
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-07-09
What seems to you to be obvious would mean a lot of work and cost to those who actually have to do the work. Do you know how long it takes to package every item of software that goes into a Ubuntu image. Do you know how long it takes to build those packages into an ISO image and at the same time test the builds?

Canonical has a server farm just for building and testing packages.

[http://ci.ubuntu.com/smokeng/utopic/](http://ci.ubuntu.com/smokeng/utopic/)

[http://ci.ubuntu.com/merger/](http://ci.ubuntu.com/merger/)

The answer to Is there a simple way? is NO.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Actually I have tested many Ubuntu ISO images. I have installed Ubuntu many time for testing. I do not often use the Live Session DVD as a recovery tool. But I do have a copy of Linux Secure Remix. And with USB memory sticks and "persistence" it is possible to create our very own recovery tool .

---

### Post by betlog-hax on 2014-07-09
> **Bashing-om said:**
> ```
linux (hd0,msdos2)/vmlinuz root=UUID=7dd23297-30ea-417a-8f69-3e2df76f3192 ro
initrd (hd0,msdos2)initrd.img
boot
sudo update-grub
```
Thanks :smile: I was hoping for something simpler and more elegant, but this looks like the easiest and most direct way to do what I asked.
However I'm a little surprised that GRUB isn't self-repairing to some degree. 
A script that intelligently handles all the variables in what you suggest above, executed from the grub rescue prompt, would make much more sense, for most users looking to 'just fix GRUB', than needing to record or remember a bunch of relatively arcane and infrequently used syntax.

I appreciate your accurate and useful post.

---

### Post by Bashing-om on 2014-07-10
betlog-hax; Hey,

How are you looking ? Is this sufficient to boot, or do we have to go a step deeper ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by betlog-hax on 2014-07-17
I suspect it does answer the question as nicely as is currently possible.
It's not as trivial as it should be, so ideally somebody should script that and include it in grub. IMO a bootloader - by definition - should be trivially self-repairing.

In this case I got sidetracked and opted for a clean install instead of screwing around with grub, so I didn't test your suggestion, but I know it is the right method. I will be implementing it eventually.

---

### Post by Bashing-om on 2014-07-17
betlog-hax; Hey;

Yeah, a (RE-)install is always the final solution; It always works.
As to Grub .. it is a boot manager and is very versatile. However, there is a learning curve in dealing with it.

I personally would have it no different, and even now I keep learning more about it.

As this situation is now concluded;
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

it is amazing indeed
[INDENT][INDENT][INDENT]what it takes to boot up[/INDENT][/INDENT][/INDENT]

---

