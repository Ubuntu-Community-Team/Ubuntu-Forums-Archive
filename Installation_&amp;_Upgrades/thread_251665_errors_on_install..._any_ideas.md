---
title: "errors on install... any ideas?"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by Nightsail on 2006-09-05
Okay, I admit it, this isn't the newest computer I'm trying to install Ubuntu on, and I *am* a beginner at linux, but I figured Ubuntu might be the place to start.  So I pulled out an old 400 Mhz comp from the garage and tried installing it off the Dapper Drake dvd that came in the Linux magazine I recently purchased.

I know, the live mode didn't work -- it hung up at some point where the cursor was a "waiting..." type of wheel-shape, and went back to a text display that said something about the second....  er...  loadup phase or something?  and everything seemed to go well... except that it kept repeating this.  So I thought maybe it was just the live version not playing nice with the comp, and maybe the installed version would do better, and tried just installing the thing anyway. (if it doesn't work out, I can always just give up, wipe the thing, and install Windows 2k or something... but I don't *want* to!)

The actual install went fine, until I had to do the "sudo oem-config-prepare" command....  something went wrong a minute or five later (well, it's a slow computer...) and it gave me another error message, and kept redoing that same message until I finally hit the pause key a few good times, which seemed to break it out of that cycle.

the message is as follows:

[FONT="Fixedsys"]Traceback (most recent call last):
 File "usr/sbin/oem-config-dm", line 58, in ?
  sys.exit(dm.run(*sys.argv[3:]))
 File "usr/sbin/oem-config-dm", line 44, in run
  os.kill (server.pid, signal.SIGTERM)
OSError: [Errno 3] No such process[/FONT]



Currently, I've left it sitting on the table upstairs, with the prompt "root@ubuntu:/#" on the screen, and am no longer sure what to do.  Any help would be appreciated at this point!

---

### Post by Nightsail on 2006-09-06
No ideas? ....any other info you guys want me to try to get? (I don't know the hardware specs for this computer, sadly...)

---

### Post by wpshooter on 2006-09-06
> **Nightsail said:**
> No ideas? ....any other info you guys want me to try to get? (I don't know the hardware specs for this computer, sadly...)

Can you tell us how much memory/RAM the machine has ?

How about what size hard drive ?

Thanks.

---

### Post by Nightsail on 2006-09-07
The hard disk is 8 GB.

I think it's got 128 MB of RAM -- but it might be more.  Should I dare reboot it to find out via the memory test when it first starts up?  I'm rather not daring to touch it at this point out of a lack of knowing whether doing so will make it more difficult to get back to where I currently am with it or not...  but I know that it said it was in some sort of low-memory mode during the earlier part of the installation.

---

### Post by wpshooter on 2006-09-07
> **Nightsail said:**
> The hard disk is 8 GB.

I think it's got 128 MB of RAM -- but it might be more.  Should I dare reboot it to find out via the memory test when it first starts up?  I'm rather not daring to touch it at this point out of a lack of knowing whether doing so will make it more difficult to get back to where I currently am with it or not...  but I know that it said it was in some sort of low-memory mode during the earlier part of the installation.

Yes, you probably really should find out how much memory you have.

Does the computer have a floppy drive ?

Do you have another computer to use to do downloads ?

Do you know how to download and run memtest86 ?

Go to this page & download the Floppy Dos version and test the memory and see how much it has while you are doing the testing.

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

Let us know the results.

P.S. - Actually, if you have a bootable Win98 floppy, you could just boot the machine to that and when the initial boot screen information comes up on the machine, it should tell you how much memory the system has, just hit the pause key if you need to stop it so you can read the amount of memory.  Or you could just go into the BIOS and the amount of memory installed should be listed somewhere in there.  Make sure you don't change anything in the BIOS by mistake.

---

