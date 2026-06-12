---
title: "Can't Install Ubuntu 7.10"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Monkey1 on 2008-02-21
Hello,

Recently i wanted to install Ubuntu on one of the PC's at my house but i failed to do so. I downloaded Ubuntu 7.10, burned it to a CD and then inserted it to the PC after i restarted i chose the "Start or Install Ubuntu" option and it came up with a box saying "Loading Linux Kernal 7%". After a while it did nothing and came up with another box saying "I/0 error Error reading boot CD.".

I later used an alternate desktop CD the text-based installer everything worked perfectly until it came to the "Installing the base system" section. It came up with a message saying;

"[!!] Install the base System
Debootstrap warning
Warning:
file:///cdrom/pool/main/libg/libgpg-error/libgpg-error0_1.4-2ubuntu1_i386.deb was corrupt"

I clicked Continue and it instantly came up with another message saying;

"[!!] Install the base system
Deboot warning
Warning: couldn't download package libgpg-error0"

I clicked Continue again and it instantly came up with another message saying;

"[!!] Install the base system
Debootstrap warning
Warning: file:///cdrom/pool/main/libi/libidn/libidn11_1.0-0_i386.deb was corrupt"

There was hell of a lot more messages when i kept clicking Continue.

Quite a few people told me the problem could be that my CD is corrupt and that i should try burning at a lower speed. I tried burning it again at 40x before i had read the message and the same problem occurred although i burned using 4x before and still had the same error. Someone else told me to check MD5SUM, i checked that and it was exactly the same.

Thank you very much i hope someone can come up with a solution for me.

---

### Post by PmDematagoda on 2008-02-21
Did you try installing Ubuntu using the Alternate CD?

Also, did you check your CD-ROM so as to ensure that it is not the CD-ROM itself causing the problem?

---

### Post by dstew on 2008-02-21
> Someone else told me to check MD5SUM, i checked that and it was exactly the same.But was it correct? Did you check it with the published value [here]("https://help.ubuntu.com/community/UbuntuHashes")?

---

### Post by Monkey1 on 2008-02-21
> **PmDematagoda said:**
> Did you try installing Ubuntu using the Alternate CD?

Also, did you check your CD-ROM so as to ensure that it is not the CD-ROM itself causing the problem?

Yes, i tried installing it using the Alternate CD and everything worked perfectly until it came to the "Installing the base system" section. I don't know if it's the CD-ROM which is causing the error but could you please tell me how i could check to see if it is the CD-ROM that's causing the error.

> **dstew said:**
> But was it correct? Did you check it with the published value [here]("https://help.ubuntu.com/community/UbuntuHashes")?

Yes, it was correct and i checked it with the "published value".

---

### Post by jcitguy78 on 2008-02-21
Is this a full install or dual boot, if so what OS is already on?

---

### Post by zvacet on 2008-02-21
When you boot CD you will see option** check cd integrity**.Do that.

---

### Post by Monkey1 on 2008-02-21
> **zvacet said:**
> When you boot CD you will see option** check cd integrity**.Do that.

I tried this just now it worked for a while and then it came up with a box saying;

"[!] Configuring cdrom-checker-menu
Integrity test failed
The
./pool/restricted/r/restricted-manager/restricted-manager-core_0.33.1_all.deb file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted."

Thanks for your responses everyone very much appreciated :).

---

### Post by zvacet on 2008-02-21
I hope that you still have iso witch you downloaded.Now  download same iso with torrent and point download where existing iso is.That way torrent will just check your iso and replace corrupted files with good ones.Check md5sum again and then burn iso on lower possible speed.After that check CD integrity.If eveything is O.K. go for install.

---

### Post by Monkey1 on 2008-02-22
> **zvacet said:**
> I hope that you still have iso witch you downloaded.Now  download same iso with torrent and point download where existing iso is.That way torrent will just check your iso and replace corrupted files with good ones.Check md5sum again and then burn iso on lower possible speed.After that check CD integrity.If eveything is O.K. go for install.

Yes, i still have the existing .iso file i downloaded. When you said to download it with torrent i didn't exactly understand what you meant, if you could explain to me what to do in order to download with torrent i would appreciate it. Many thanks.

---

### Post by PmDematagoda on 2008-02-22
You can find out what a torrent is from [here]("http://en.wikipedia.org/wiki/.torrent").

Just use a torrent client such as [Deluge]("http://deluge-torrent.org/") and then download the proper file with the .torrent extension from [here]("http://releases.ubuntu.com/7.10/"), open it with the torrent client and tell it to download the file to the location where the old ISO file is found.

After that is done, burn the "old" ISO to a CD at a sped of 1x(just to be safe), see if you can boot the Live CD properly then.

---

### Post by Monkey1 on 2008-02-22
> **PmDematagoda said:**
> You can find out what a torrent is from [here]("http://en.wikipedia.org/wiki/.torrent").

Just use a torrent client such as [Deluge]("http://deluge-torrent.org/") and then download the proper file with the .torrent extension from [here]("http://releases.ubuntu.com/7.10/"), open it with the torrent client and tell it to download the file to the location where the old ISO file is found.

After that is done, burn the "old" ISO to a CD at a sped of 1x(just to be safe), see if you can boot the Live CD properly then.

Ok, I've downloaded Deluge and the torrent file. I've put the torrent file where the earlier .iso file is located and it's currently "Seeding" but unfortunately the CD's i have can't write at 1x it can only do 4x. Many thanks :).

---

### Post by Monkey1 on 2008-02-22
I just tried the CD which i recently burned unfortunately without any success. I think what I'll do is wait for the CD's which i requested for on 2008-01-17 from Ubuntu and if all goes well I'll see how Ubuntu goes but if it disappoints me i might think about switching back to windows, thanks a lot for your help everyone.

---

