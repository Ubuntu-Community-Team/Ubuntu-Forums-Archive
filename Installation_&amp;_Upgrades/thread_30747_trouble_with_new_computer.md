---
title: "trouble with new computer"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by dueY on 2005-04-30
Just when I was getting used to Ubuntu being my main OS on my other computer...

I just set up my new computer today.  After getting Windows all patched and setup I created a new 20GB partition and made it ext3.  I change the boot order to CD first, pop in my hoary504-386 iso, and watch the text fly down the screen.  Then it stops.  There was some kind of timeout. [-X   So I try it again, same result.

Thinking it may be a corrupted disc or something, I put in my trusty old 4.10 CD that I ordered from Ubuntu and used to install Ubuntu on my last PC.  It looks like it's working up until the detecting the CDROM part.

It claims it can't detect my CDROM.  I don't understand how this can be since it's obviously reading it since it booted into it and is running the install program from it. :---) 

Any help here would be much appreciated.  I was hoping to get my Ubuntu up and running tonight  ](*,) 

I'm going to bed now, I can post specs or give any other information when I wake up,  if needed.  Thanks for any help possible  :?

---

### Post by DJ_Max on 2005-04-30
Have you searched the forums? I remember seeing people with the same problem. Also, take a look at [http://www.ubuntulinux.org/wiki/SmartBootManagerHowto](http://www.ubuntulinux.org/wiki/SmartBootManagerHowto)

---

### Post by ssam on 2005-04-30
if i remember correctly this could be a dma issue.

at the boot prompt when you you boot from the cd, can you put

```
no dma
```

if this does not work try pressing F1 and see if there is any useful help

---

### Post by dueY on 2005-04-30
I should have mentioned, this new computer has no floppy drive.  I will try the dma command though.

---

### Post by dueY on 2005-04-30
The no dma tip didn't work.  Ubuntu still can't detect and mount my CDROM.  I switched into the console and typed ls /dev and here is what I had:

console, input, mem, ptmx, rd, shm, usb, fb, kmem, misc, pts, root,
tts, vc, ful, kmsg, null, pty, root.old, tty, vcc, ide, log, port, random,
scsi, urandom, zero

---

### Post by dueY on 2005-04-30
I fixed the CDROM issue by going into expert mode (type 'expert' at boot: ) and disabling the ata_piix

Now there's a problem with the partition.  I get the "No usable physical partitions found" error.  I think there's something wrong with the permissions on my harddrive or maybe Dell somehow locked it so their restore partition doesn't get messed with.  Even Partition Magic 8 threw a fit when I tried to use the new operating system wizard to partition some space, "The selected disk contains one or more partitions which cannot be moved. To complete this task use the Operations menu rather than a wizard."

Any ideas?

---

