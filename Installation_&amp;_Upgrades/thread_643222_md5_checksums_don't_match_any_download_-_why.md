---
title: "md5 checksums don't match any download - why?"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by jblake on 2007-12-17
I recently posted an issue about gutsy gibbon - I tried it earlier in the year and had bad results then.
I know you should run checksums but didn't bother. I downloaded the software to run on windows to do md5 check sums from Nullriver Software and none of the recent downloads matched. I decided to make fresh downloads from a different mirror - Heanet in Ireland, and got the same results. The first images were downloaded from Canonical UK mirrors and they did not match. And before anyone thinks I did not put the right checksum in I did. What can the matter be? I am pulling my hair out and have wasted 3 cds so far. Am using Nero Express that came with my external LG DVD-Ram/DVD-Rom Writer and have not had any issues with other Linux distros this year - infact Geubuntu (ubuntu with enlightenment) 7.10 downloaded and burned without any trouble. When I do burn, the ISO burning software automatically sets to whatever medium is in the burner (ISO burner from [www.NTFS.com](www.NTFS.com)) which has never failed me over the past 12 months. I think if this is not resolved I shall stick with the 'feisty fawn' issue. I have checked previous threads and I am not a newbie - I have used GNU/Linux for the past 2-3 years and actively promote it on my website (including Ubuntu) but this might have to change.
:confused:

---

### Post by Pumalite on 2007-12-17
Are you talking about md5sums made by k3b? I've had no problems.

---

### Post by jblake on 2007-12-17
No - I downloaded the md5 hash list from the mirrors which list all the md5 checksums for each type of 7.10 download and followed the links that Taurus kindly provided. I used the winMd5sum software as advised for doing this and none matched, whether I used the calculate button or not. After I had burned 2 discs, the startup screen appears but the Kernel Loader does not appear - the drive that I try to boot from just keeps whirring. And as I have said, I have had no problems burning Geubuntu in Windows using  the ISO burner software from [www.NTFS.com](www.NTFS.com).

---

### Post by Pumalite on 2007-12-17
> **jblake said:**
> No - I downloaded the md5 hash list from the mirrors which list all the md5 checksums for each type of 7.10 download and followed the links that Taurus kindly provided. I used the winMd5sum software as advised for doing this and none matched, whether I used the calculate button or not. After I had burned 2 discs, the startup screen appears but the Kernel Loader does not appear - the drive that I try to boot from just keeps whirring. And as I have said, I have had no problems burning Geubuntu in Windows using  the ISO burner software from [www.NTFS.com](www.NTFS.com).

If you are using Ubuntu, use k3b to burn your images. I assure you it will not fail. It provides an accurate md5sum before it burns. You can compare that to your sources. I have had no problems with the downloads either. Recently downloaded and burned Ubuntu, Kubuntu, Xubuntu, LinuxMint and others. All successful.

---

### Post by jblake on 2007-12-17
Guess I will have to boot to Sabayon and try it that way. Buried on another drive I have 6.06 but I think the mbr has got messed up on the other drive - strange, I can still access my SuSE 10.0 gnome on the other drive but not the Ubuntu one. Ah well I will give it a go. Cheers.

---

### Post by Pumalite on 2007-12-17
LinuxMint 4.0 also comes with k3b

---

### Post by psusi on 2007-12-17
Try downloading via bittorrent since it inherently verifies correctness and will redownload any corrupted parts.

---

