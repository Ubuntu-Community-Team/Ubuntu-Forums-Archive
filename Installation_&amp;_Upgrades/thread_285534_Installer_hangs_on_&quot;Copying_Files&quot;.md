---
title: "Installer hangs on &quot;Copying Files&quot;"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Hikaru79 on 2006-10-26
I'm trying to install Edgy from scratch; I ran the "Check CD for Defects" (twice) and I tried inserting the CD-ROM into two different CD-ROM trays on the same computer; but every time, when running the installer, it will partition the drive, start copying files over, and then always hang at 34% and just stay there (the rest of the GUI hangs too, making the LiveCD unusable, and I have to force-reboot it). I've tried this about five times and it hangs in the same place every time.

Normally I would assume it was just a problem with the CD or CD Drive, but the checksums all verified fine. And I tried two different drives. I'm very puzzled.

(PS: I've been running Ubuntu since Hoary, so I'm pretty sure my computer is not to blame)

Any ideas? :) Thanks in advance!

---

### Post by magicfab on 2006-10-27
Perhaps use the alternate CD instead, install a server version and then install the ubuntu-desktop package...?

---

### Post by Hikaru79 on 2006-10-27
Yes, that's a possibility, but I'd like to leave it as a last resort... (Mainly for bandwidth reasons; I'm on a University campus and already spent a lot of bandwidth downloading the LiveCD)

Is there a way to do a text-mode install from the Destop LiveCD? (Using the same installer that Hoary and Breezy used?)

---

### Post by magicfab on 2006-10-27
I am not sure this still works but try hitting "ESC" when the boot has shown the initial screen, then type "server". Even though you later install "ubuntu-desktop", the packages would first come from your CD. By all means come back and report here if it still works :)

---

### Post by OneSeventeen on 2006-10-29
I just thought I would add that I have the exact same symptoms.

I checked the MD5 of the file before burning the CD, then I burned it at low speed on a decent quality disc, then verified the disc with the CD burning software, then ran "check disc for defects" from the boot menu, then went to install the CD.

I left the CD going for about 5 hours (while I was away at Church and lunch with friends) and when I got back it was stuck on 33% "copying files"... now every time I re-try, it just stays stuck on 34% "copying files".

I will try another disc, and if that doesn't work, I'll try the server install.  I like the GUI install because I'm installing it alongside Windows and it is easier to change the partitions.

The voice in the back of my head is telling me "You should have waited for a month or so until the kinks were ironed out", but I just had to have edgy as soon as it was available...

I'll post back my results positive or negative, and I'd appreciate the same from everyone else having this issue.  If you find a way to get it to work, please let us know here so others can get help!

---

### Post by OneSeventeen on 2006-10-29
Third time was a charm.

I tried it a third time, using a different ratio of man partition and swap partition, and it worked perfectly.

Now let's see if I can figure out how to get wireless working...

---

### Post by Buffi on 2006-10-29
Im on my third try now.
Wish me luck

---

