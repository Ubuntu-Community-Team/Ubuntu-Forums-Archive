---
title: "Unable to boot ubuntu or xubuntu"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by robcarr on 2008-04-05
Hi,

Having tried on a number of occasions to get Linux up and working I am on the verge of giving up.  I have an oldish PC that I have just put some more Ram into which is now about 368mb. I recently got puppy Linux up and running on this same PC but found that the interface wasn't as friendly as I had hoped so on the recommendation of a friend I upgraded the RAM and loaded Ubuntu.  I successfully burned an ISO image doing all the checks advised.  The machine booted the ubuntu disc and gave the options for starting and instaling ubuntu etc.  However when I select that option (and most of the others including safe start etc it eventually comes to the same screen and freezes.  i know the disc works because I have booted it on my lap top.

I will attempt to type what the screen says as I dont know how to get the info on the screen back to the laptop from which I am typing this message.

[I]BusyBox v1.1.3. (Debian 1:1.1.3-5ubuntu7) Built-in-shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) (113.655975) ata1.00: exception Emask OxO SAct OxO SErr OxO action Ox2 frozen
(113.656052) ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/eo tag cdb OxO data 4096 in.

It then repeats this with slightly different numbers the finishes off with 

(204.719234) sd 2:0:0:0:0:  (sdb) Assuming drive cache:write through

I am afraid I have no idea what any of this means and would really appreciate some help 

thanks

Rob

---

### Post by stefangr1 on 2008-04-05
Have you already tried the alternate install cd? That one might work better on some older hardware.

---

### Post by Sef on 2008-04-05
Check out [Launchpad Bug #154591]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591") and this [Ubuntu Forum Thread]("http://ubuntuforums.org/showthread.php?t=585566").

---

### Post by prshah on 2008-04-05
> **robcarr said:**
> 
[I]BusyBox v1.1.3. (Debian 1:1.1.3-5ubuntu7) Built-in-shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) (113.655975) ata1.00: exception Emask OxO SAct OxO SErr OxO action Ox2 frozen
(113.656052) ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/eo tag cdb OxO data 4096 in.
Rob

Same problem, see [http://ubuntuforums.org/showthread.php?t=703228&highlight=tsstcorp](http://ubuntuforums.org/showthread.php?t=703228&highlight=tsstcorp), espeially the screenshot

Finally cleared it by using a NON samsung/tsstcorp CD drive. (Used LG). After installation was complete, put the samsung CDROM drive back and it woked.

---

### Post by robcarr on 2008-04-06
I have tried some of the simpler suggestions without success so I am going try PR Shahs suggestion of a CD Drive chnage as I found another thread that had a very similar problem shown [http://ubuntuforums.org/showthread.php?t=653545](http://ubuntuforums.org/showthread.php?t=653545)

Thanks for all your help I will let you know how I get on!

Rob

---

### Post by robcarr on 2008-04-06
Have just spent the last 4 hours swapping cd drives but sadly to no avail.  I tried two different drives so I dont think the problem is there.

However I have discovered one thing - Before the page that gives the Ubuntu options a message flashes up.  This does not happen on the two computers that successfully boot Ubuntu up.  I managed to photograph this line as it flashed past and it read - 

0.0000001 ACPI: BIOSage (1997) fails cutoff (2000) acpi = force is required to enable ACPI 

Does this mean my mother board is too old for UBUNTU?

Rob

---

### Post by prshah on 2008-04-06
> **robcarr said:**
> 
0.0000001 ACPI: BIOSage (1997) fails cutoff (2000) acpi = force is required to enable ACPI 
Rob

I get it all the time, I ignore it and my old machines (1xMediacenter, 1xserver, 1xJustlikethat) all work fine.

---

### Post by shiggs on 2008-04-09
> **prshah said:**
> Same problem, see [http://ubuntuforums.org/showthread.php?t=703228&highlight=tsstcorp](http://ubuntuforums.org/showthread.php?t=703228&highlight=tsstcorp), espeially the screenshot

Finally cleared it by using a NON samsung/tsstcorp CD drive. (Used LG). After installation was complete, put the samsung CDROM drive back and it woked.


I was getting this error as well, switched the DVD drive and all was good.

---

