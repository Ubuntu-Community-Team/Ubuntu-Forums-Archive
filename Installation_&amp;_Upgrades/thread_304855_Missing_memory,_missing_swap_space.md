---
title: "Missing memory, missing swap space"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2006-11-22
I recently moved from Fedora core 1 to ubuntu 6.06.
On boot up I got messages (not exact):

DosSegMgr: Warning: 
using an alternate geometry (cylinders, heads, sectors) for drive hda

The kernal reported drive geometry is: C=4865 H=16 S=63

The partition records report a geometry of C=4865 H=255 S=63

Using the alternate geometry reported by the partition records

No volume groups found
alert   does not exist

Dropping to a shell

/bin/sh:  can't access tty.  job control turned off

I didn't know what to do at this point so I just rebooted again
and got the same messages.

On my third (I think) try, ubuntu 6.06 came up successfully
and everything seemed ok as far as I can tell.  (I am no linux expert
though.)

Among the things I did was run the command:

    squeak -memory 150m  squeakImage

which runs squeak (a version of Smalltalk) with an initial allocation
of 150 megabytes of memory.

This worked for a few day until I upgraded to unbutu 6.10.

Then, when I ran the above command ubuntu reported that not enough
memory was available.  However the command:

     squeak -memory 110m squeakImage 

worked fine.

My first question is what is it about ubuntu 6.10 that is using the
extra memory since (AT LEAST) 40 megabytes of memory is no longer
available to applications that I run.  Is there anything that
I can (and should) do to free up this memory.

I then ran a df command.
I noticed that no swap space was reported by df. 
(on Fedora core1 the df command reports the size 
of my swap space which was set to 512m on my 256m machine)
machine.

My second question is what happened to my swap space.
I am assuming that I need to repartition so that I have a swap space.
If so, where do I go to find the documentation on how to do this.
I don't want to lose the data currently on the disk drive of course.

Thanks, and sorry for the long post.

Ralph Boland

---

