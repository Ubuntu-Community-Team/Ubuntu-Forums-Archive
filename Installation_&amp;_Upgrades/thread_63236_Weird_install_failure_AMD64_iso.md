---
title: "Weird install failure AMD64 iso"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by jvictor on 2005-09-07
Hi guys !
Me runnin into some kind of weird problem. I am trying to write the amd64 iso; the burn process goes on fine.. and the install fails half way saying that e2fsprogsXXX.udeb could not be retreived or something of that sort.

I verified the md5 and found it same as given in the site. The e2fsprogs udeb can be found in the cd if  i open it from win.. and am able to browse /copy etc from that folder..so i feel that its not a cd problem also. 

I use Nero for burning the image, and find that if i use 10x speed the error occurs at 15% and if i use 4x speed, the error occurs @ 25%. I use a sony dvd writer.. ne clue y this happens ? i have tried downloading the same image twice...and burning ...but get the same result... my patience is getting tested !

My machine config

AMD athlon 64 3000+
Gigabyte GA-k8vm800m
1G kingston ram (512x2)
80 GB barrcuda (PATA)
Sony DVD RW DRU-810-A

---

### Post by rafakl on 2005-09-07
The problem can be in your cd/dvd writer OR in your blank disc.

Try downoading a newer driver from the manufacturers page.
 :)

---

### Post by jvictor on 2005-09-16
I downlaoded kubuntu and tried burning it to a new CD-RW; same state continues.. MD5 sum matches.. but install fails when copying udebs. Is the iso broken ?  I use an opensource downlad manager called wxDownloadFast. Any clue why this happens ? This is proving to be just a waste of time, bandwidth  and resources ..

---

### Post by skskarda on 2005-10-31
I had similar problem.  I found a post that showed how to enable dma during Ubuntu install.

[http://www.ubuntuforums.org/showthread.php?t=82402](http://www.ubuntuforums.org/showthread.php?t=82402)

Fixed my problem.

---

