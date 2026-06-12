---
title: "[SOLVED] Corrupt Files in 8.10 Ibex Torrent??"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Devi 710 on 2008-10-30
Hi,

I just tried burning the ISO of Ubuntu 8.10 Desktop which I downloaded via bit torrents (from ubuntu.com) twice in Brasero, and both times when I checked the integrity of the disk it came back with errors.

Does this mean there was some problem with my bit torrent client (Deluge), or the ISO itself, or the Brasero burning software?

Anyone else get the same problem? I used a slower speed the second time (25x), could that be the problem.

If I like Ibex I will make a fresh install (still in Gutsy 7.10 - wasn't crazy about Hardy) but I want to be positive there are no corrupt files first.

I know I can just download it from the site, but I am curious about the torrent.

Thanks

---

### Post by Partyboi2 on 2008-10-30
check the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso you downloaded that it is correct. When burning to disk to avoid possible corruption burn at x4 or less

---

### Post by sudo_chop on 2008-10-30
I got a CD error after burning and went back and md5'd the iso I downloaded from the official torrent and it was BAD?!? wtf? how could this happen with torrent? I dont want to have to download it all over again. is there some way to force my torrent to recheck the file and redownload the bad part?

---

### Post by Partyboi2 on 2008-10-30
> I got a CD error after burning and went back and md5'd the iso I downloaded from the official torrent and it was BAD?!? wtf? how could this happen with torrent? I dont want to have to download it all over again. is there some way to force my torrent to recheck the file and re-download the bad part?


If you still have the iso you downloaded you should be able to restart the torrent and it should check and  re-download the missing or corrupt files.

---

### Post by sudo_chop on 2008-10-30
> **Partyboi2 said:**
> If you still have the iso you downloaded you should be able to restart the torrent and it should check and download the missing files.

Cool, I just figured it out, I just stopped it and clicked force recheck and it went down to 98.something% complete.

New md5 checks out

Hope that is the only hiccup in my install!

---

### Post by Devi 710 on 2008-10-30
> **Partyboi2 said:**
> check the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso you downloaded that it is correct. When burning to disk to avoid possible corruption burn at x4 or less

Thanks for the helpful link about checking the md5sum Partyboi2 (and the quick response). I am running a live session right now from one of the 'corrupted' disks.

When I boot back up I will check the md5sum and burn in slower speeds next time.

---

### Post by Devi 710 on 2008-10-30
Yup my md5sum matches! I will just burn it slower to avoid errors. Thanks for all the help. I am marking it solved.

To those looking for the Ubuntu Ibex 8.10 MD5 Sum Hashes:
[http://releases.ubuntu.com/8.10/MD5SUMS](http://releases.ubuntu.com/8.10/MD5SUMS)

---

### Post by razorxpress on 2008-10-31
Even without torrents the iso are corrupt. With wget i download the file which seem to be corrent in file size. I did a md5sum check after downloading the around 700MB file which after md5check shows to be  828618484. I ruined all. MD5 just sucks. Now how do i recover this

---

### Post by Partyboi2 on 2008-10-31
Best to use torrents, as the larger the file you are trying to download the chances of corruption increases if this happens with a torrent atleast you have an option to try and fix it without having to start the process all over again.

---

