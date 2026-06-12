---
title: "Set up a NAS box UBUNTU server"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by raptorman on 2007-08-20
Sorry I am a newbie

Can someone point me in the direction for documentation on this.

Want to have 4 500 gog drive set up for storage,

what package would one use if it is even available

Thanks You

---

### Post by jakev383 on 2007-08-20
Samba will allow you to share them with Windows clients.  NFS will allow you to share them more efficiently with Linux clients.  There's some how-to's in the wiki that will guide you with those.
I do something similar here.  I have a Linux box that acts as my router/firewall. It also has 1TB of storage (in a RAID5 array) that I share to all the computers in my house.  One box, many hats.

---

### Post by raptorman on 2007-08-20
Thanks a million Jake,

You set up the RAID to span multiple drives?

Thank you

---

### Post by Jose Catre-Vandis on 2007-08-20
I have an ubuntu server running with 4 x HDDs on board. I use NFS only to serve up shares and for Windows Clients I install the Microsoft SFU (see my howto)
[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)
where you can also follow a link to an NFS howto

I didn't bother with RAID or LVM, as it makes it easier to swap out HDDs, IMHO!

---

### Post by jakev383 on 2007-08-20
> **raptorman said:**
> Thanks a million Jake,

You set up the RAID to span multiple drives?

Thank you

Yeah, I had a lot of MP3s (before Napster was even around, and before RIAA and fingernail-pulling) and when I had a HD die I lot 12,000 songs or so.  I was able to recover the ones I liked (believe it or not I did buy the CDs for the albums I liked), but ever since I have run a RAID5 array.  I know, you lose some space that way, but 200G drives were cheap at the time so I crammed as many as I could in the case (had to use an IDE PCI card to get 4 more channels) and then set the array up. Added a couple directories and setup Samba to share those directories.  Been great ever since, and now the wife can share files with me too!

---

