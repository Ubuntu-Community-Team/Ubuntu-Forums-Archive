---
title: "dual booting?"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by slade on 2005-11-16
my computer has been having problems for a little while, progressively worse, and just yesterday it completely died on me.  i cant even get to the bios.  its 4+ years old, so thats understandable.  luckily just a few days ago i got an even older computer (5+ years, pentium III) and installed ubuntu on it, which is how im online right now.  anyway, i think its time for a new computer.  for a little while ive been wanting to try linux, and i figure now would be a good opportunity to set up a dual boot system from scratch...  it would have more CPU speed, memory, and hard drive space than this computer, plus i wouldnt have to switch the monitor, keyboard, mouse, and other cables every time i wanted to switch computers.  i probably wont have the new computer for a little while, but i decided its a good idea to start looking into what id have to do.

in case it matters, id probably get something along the lines of:

CPU:  2-3 ghz
ram:  512mb-1gig
hard drive:  single, 100-200gigs
sound and video cards:  any suggestions?

i would be installing everything from scratch, and from what ive seen i take it windows would need to be installed first.  i would be installing windows 2000 and linux, probably ubuntu but maybe debian or red hat.

a dual boot system at first didnt sound like it would be too hard, but ive been looking at tutorials and im fairly confused.  im a linux newbie, ive been using linux since, well, i joined this forum.  can anyone tell me what would be the best way to install both windows 2k and linux on a computer at once?  the tutorials all seem to vary.

also, what is GRUB and LILO?  which do you think i would be better off using?  where do i get them?

the partitions are confusing me.  what partitions do i need/would it be a good idea to have?  how do you even set up partitions/at what stage do you do so?  (before you install anything?  during windows installation/during linux installation?)  what would be a good size/order for the partitions?  (considering the HD size)  A tutorial i saw mentioned a BIOS 1024 cylinder limit.  on my windows computer i had 2 partitions, C:  for programs and D: for data, and C:  was probably over 8gigs.  If i did the same thing again, that would mean that the linux boot partition would be past the 8gig line.  could i have the /boot partition before the windows partition?  or would there be a way to reflash the BIOS so that this wouldnt matter?  (if so, how, and what would i flash it to?)  would i be able to set up seperate partitions for each system booting and the programs for each system, and then a shared partition for all my data?  also, what file types are compatable, is there any way to open a .doc file in linux?

once i have everything set up, how do i specify what OS i want to run?  on startup, would it wait for me to select one or the other, or would it automatically boot under one OS unless i did something to specify the other?

thats all the questions i can remember for now, lol...

sorry for so many newb questions, everyone, but im really new to this and it seems like linux has a harsh learning curve.  maybe things are simpler than i think, though.  any help would be appreciated.  if any of you want to know about paintball, i promise ill pay you back ;) 

thanks in advance.

---

### Post by aysiu on 2005-11-16
[Hardware compatibility list](https://wiki.ubuntu.com//HardwareSupport)

[Ultimate dual-boot setup guide for Ubuntu](http://users.bigpond.net.au/hermanzone/)

Ask if you have any questions after you check out those links.

---

### Post by darth_vector on 2005-11-16
hi :)

as for your choice of hardware, that really depends on what you will be using the thing for. are you a gamer, do you do multimedia work, office work only??

as for double booting, its not very difficult to set up. install windows first because it will over-write the master boot record if you install it second. if you want a setup similar to before then you will need two windows partitions. you will create these when installing windows. make sure you leave enough room for the other operating system(s) you are installing.

once you have installed windows, put in the ubuntu install cd and boot from it. you want at least two partitions: / and /home, and possibly a /boot (i like having this for troubleshooting). you will also have to set up swap space - this is an area of the harddisk used by the operating system as additional memory. the size of the swap space should be about twice the size of your RAM.

LILO and GRUB are bootloaders. they load the operating system code into memory. i would use GRUB since it can chainload windows (which lilo cant do without help).

---

### Post by slade on 2005-11-16
[QUOTE=darth_vector]hi :)

as for your choice of hardware, that really depends on what you will be using the thing for. are you a gamer, do you do multimedia work, office work only??

as for double booting, its not very difficult to set up. install windows first because it will over-write the master boot record if you install it second. if you want a setup similar to before then you will need two windows partitions. you will create these when installing windows. make sure you leave enough room for the other operating system(s) you are installing.

once you have installed windows, put in the ubuntu install cd and boot from it. you want at least two partitions: / and /home, and possibly a /boot (i like having this for troubleshooting). you will also have to set up swap space - this is an area of the harddisk used by the operating system as additional memory. the size of the swap space should be about twice the size of your RAM.

LILO and GRUB are bootloaders. they load the operating system code into memory. i would use GRUB since it can chainload windows (which lilo cant do without help).[/QUOTE]
thanks aysiu and darth_vector.  that link makes it look a lot easier...  i think the problem was i kept finding tutorials for other linux distributions or other versions of microsoft, a lot of them were written years ago.  im pretty sure Win 2k uses FAT32, right?  it looks like there isnt too much more with a dual boot than what ive already done.  just to make sure, i do want to install GRUB over the microsoft MBR, right?  I thought a few other tutorials said to not do that, although i think they were older.

I dont do too much gaming.  mostly halo, maybe a few other games.  the computer i had before lagged even while playing offline, but im not sure if that was the CPU or videocard or what...  id like to get that resolved.  my friend is trying to get me addicted to WoW but i dont think i have the time for that.  I use photoshop on occasion but not all the time.  besides that, its basically just officework and going online.  id like something that works well but not top of the line.  and of course, something compatible with ubuntu...  thanks for the link.

im still not clear on the partitions.  i know about swap, but why /, /home, and /boot?  those would be in addition to C: and D:, right?  would the partition(s) for windows be accessable under ubuntu, and vice versa?  (say i save all my music, videos, pictures, etc. under D:  on windows, will i be able to access and edit that data under ubuntu?)

what do you mean chainload windows?

thank you for your help.

---

### Post by aysiu on 2005-11-16
[QUOTE=slade]im pretty sure Win 2k uses FAT32, right?[/quote] Actually, Windows 2000 is usually NTFS > just to make sure, i do want to install GRUB over the microsoft MBR, right? Yes. Ubuntu's boot loader will recognize Windows and add it to the Grub menu. Windows' boot loader will completely ignore Ubuntu.

> im still not clear on the partitions.  i know about swap, but why /, /home, and /boot?  those would be in addition to C: and D:, right? Yes, they're totally different from the Windows drives. Swap is like extra memory (sort of). You don't need a separate /boot partition, but it may help to have a separate /home partition. That way, in case you ever reinstall (or install a newer version of Ubuntu from scratch), you can easily keep your settings intact.

> would the partition(s) for windows be accessable under ubuntu, and vice versa?  (say i save all my music, videos, pictures, etc. under D:  on windows, will i be able to access and edit that data under ubuntu?) [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

NTFS - read-only
FAT32 - read/write

I'd also highly suggest you read [this](http://www.psychocats.net/essays/linuxguide.php)

---

