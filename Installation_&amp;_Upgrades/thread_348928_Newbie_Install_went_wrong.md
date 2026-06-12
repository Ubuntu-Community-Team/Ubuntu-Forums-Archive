---
title: "Newbie Install went wrong :/"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by Ipnobatis on 2007-01-29
First of all, hi to everyone!
I decided to move to linux.. so many reasons (blue,green,colorfull etc) that i don't want to waste time explaining...
I have some knowledge over pc's (you know the clasical one with the Ms sing on them... :( ) but now i'm getting to a hole new enviroment..
To get to the problem, i d/l the ubuntu 6.06.1 desktop i386, burn it to a cd, found the oldest pc around and tried to install it... but i get some "wierd" error that i can not translate :) 
The pc is an old amd k7 550mhz, 250somthing memory, tnt2 32mb(?), msi motherboard and a maxtor 12gigs hard drive.
I wipe every little thing of windows from the hard drive, i didnt formated in any format, and put the cd to start up, tried to install ubuntu, getting some graphics saying "that the linux kernel is starting up" and then two-three screens of numbers and letters...
I quote the last 2 lines of the hole "error"

"[    89.993708] <0> Kernel panic - not syncing : Attempted to kill init!
 [    89.993823] 
                         "
everything stuck there, reset button, tried couple of times still the same.. 
Because i'm just starting to learn about linux... i'm open to all sugestions :D 

Regards

Update:
I have tried all menus from the installation procedure, even the "start ubuntu in safe graphics mode" ends up in an error
the application comes to an end in the second file that is trying to be copied the "initrd.gz"......

---

### Post by l951b951 on 2007-01-29
Is there a chance of an error on the download or burn of the iso?  
You might want to re-download the iso image and burn it at the lowest speed possible to ensure there are no errors.  My first linux install had a problem that was caused by a data error.  I used bittorrent to download and verify integrity of file, and then burned it on slowest possible setting.  Worked for me.

---

### Post by Ipnobatis on 2007-01-30
I thought that, so i d/l it again..
I tried the alternate iso, did a parity check, wrote it 4x speed 
but stil i get the same message whatever i do...
Any more ideas? anyone?

---

### Post by Ipnobatis on 2007-02-02
Update...
After some intensive search and study i tried to solve the problem with ubuntu boot...
I haven't come to any solutions just to more questions....

I have copied the error mesage just a few lines before the error crash, it is obvius that one specific file that is trying to load makes all the damage but i don't know how to get rid of it...

I quote some of the last lines or the "error code"
where # = numbers
{bla bla bla

[####.#######] [c#####] sys_write+0x38/0x80
[####.#######] [c#####] populate_rootfs*0x91/0xd0
[####.#######] [c#####] init+0x0/0x150
[####.#######] [c#####] init+0x18/0x150
[####.#######] [c#####] kernel_thread helper+0x5/0x10
[####.#######] Code: 85 db 75 9d 8b 46 10 8b .... and so on for about 2 more lines....

[####.#######] [c#####] <0> kernel panic_not syncing! Attempted to kill init!
}
Some people told me about live cd, which to be honest I don't know the difference between the normal the alternate and the live cd...
Any more sugestions or ideas are more than welcome :KS

/edit: Where exacly should i d/l the live cd?

---

