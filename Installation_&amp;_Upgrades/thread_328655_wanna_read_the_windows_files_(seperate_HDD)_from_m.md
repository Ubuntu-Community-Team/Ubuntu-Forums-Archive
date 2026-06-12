---
title: "wanna read the windows files (seperate HDD) from my Edgy HDD"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by run1206 on 2006-12-31
Hi, i just installed Edgy into my desktop (have Dapper on the laptop, works great) :D and i have two hard drives, 80GB and 60 GB, respectively.  I installed Edgy on the 60 GB drive and the 80GB has Windows XP on it.  I did the Dapper installation with my single HDD laptop and i use both Windows and Linux on the same HDD.  My question is, can there be a way to read my "Windows" (HDD and files) from my "linux" drive?  I seem to be able to do it(read files from windows in Linux) with the laptop, yet i can't see the windows files from my 60GB linux HDD:-k, let alone i can't see the Windows hard rive itself!!](*,)  Any suggestions would be greatly appreciated. Thanks Much!! :)

---

### Post by Sef on 2006-12-31
yes, it's called ntfs-3g.  I know it is in beta now.  Don't have to to google it, but if you do, you should find out how to download it.

---

### Post by run1206 on 2006-12-31
thanks sef, i used ntfs-3g, did the ./confgure (not the make and make install), and i installed all the fuse packages and the built in ntfs-3g packages in synaptic.  someway, somehow, it works!!!!:D 
Thank you so much for your help!!!:):) 
i do have another question,  before the install of Edgy, i shifted some of my movie files(windows) over into the same drive i'm using Linux on (linux filesystem with swap is 25GB, the rest for the movies).  I can't read those movies files, but i can read the windows files with ntfs-3g. Do i use the same application for the movie file within my Linux HDD, and if so how?
Thanks

---

### Post by run1206 on 2006-12-31
just figured it out. :shock:  do the same as the other drive but this time i mounted it to a different file.  it's hdb1 (NTFS), so instead of /mnt/windows, i did the first one in the windows file and the second "movie section" on the /mnt/windows1 section of the linux drive.  now i can access BOTH the movies and the regular windows drive.:)  Thanks very much again!!!!!!:D :D :D

---

