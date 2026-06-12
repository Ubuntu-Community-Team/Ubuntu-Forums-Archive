---
title: "GRUB loading, please wait....  INSTALL FAILS."
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by pterandon on 2006-03-22
Hello, I'm on my 4th or 5th attempt at installing.

**Media:** a DAO mode-burned kubuntu 5.10 CD, burned as iso image, with a media check afterwards for binary equivalency, and I looked at MD5 calc--looked the same as that on web page.

It went throught the whole install process and now upon reboot, is saying, "GRUB loading, please wait...." for an indefinitely long time. (>>10 minutes).  Green HDD light is on and staying on. 

**Box:** An IBM Netvista with 2.8GHz chip, >>0.5Gb RAM (I forget at moment). Box previously had kanotix linux on it. I took out the old HDD for the Kanotix installation and put in new hitachi Deskstar (which BTW is a brand that is successfullly running my other box's SUSE installation, from which I'm typing).  Box also has a second HDD on it, which worked fine for kanotix. 

This is my fourth or fifth attempt. Previous burn of kubuntu locked up before got to end of install twice.  Tried ubuntu 5.10 CD, same story as here.  Keep locking up. :mad: :mad: :mad: :mad: :mad: 

Powering off, repowering on, gives same situation, where green light of HDD just stays on and on and on.

---

### Post by pterandon on 2006-03-23
okay, now that I think about it, the setting up of the formatted partition on my /root paritition failed.   

I did a <go back> and thought I was safe because the installation went to the very end, but perhaps not.   

I'm trying again with reiserfs.

Any tips?](*,) ](*,) ](*,) ](*,)

---

### Post by neoflight on 2006-03-23
[QUOTE=pterandon]okay, now that I think about it, the setting up of the formatted partition on my /root paritition failed.   

I did a <go back> and thought I was safe because the installation went to the very end, but perhaps not.   

I'm trying again with reiserfs.

Any tips?](*,) ](*,) ](*,) ](*,)[/QUOTE]

i might be wrong...but some
tips:  
1)make the mount point root..... '/' where you install ubuntu
2) bootable flag 'on'
3) lnstall grub on master boot record...just say 'yes'...

i just reinstalled ubuntu...this was my 12th i guess !!!

here is a good demonstration if you have another computer working (i guess u do ....u put a message here :) )

[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu)

if this link doesnt work....go to google videos and search for ubuntu.

hope this helps....

---

### Post by pterandon on 2006-03-23
I believe I did all those things with no success. 'cept watch the video yet.

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by pterandon on 2006-03-23
Hello?

I've also got a knoppix live CD.  Any ways I could debug the current setup using that?

---

