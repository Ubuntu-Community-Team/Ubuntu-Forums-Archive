---
title: "Busy Box Error"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Funkyfactory29 on 2007-10-19
I am attempting to install Gutsy on my dell 1520 laptop.  I have used fiesty before but i wasnt a hardcore user.  When i attempt to install or load from the live cd i get a 

"Busybox v1.1.3 (debian 1:1.1.3-5 ubuntu7) Built-in shell (ash)"

Just wondering what can be done about this and what the error really means.

---

### Post by mobiSid on 2007-10-19
i've got the same problem :(
what video card do you use?
my - ati radeon saphire 9600se .

---

### Post by Funkyfactory29 on 2007-10-20
I have a Nvidia 8600M GT in my laptop.  I think it is the root of my problem but i am not sure.

~FF29

---

### Post by platypuss72 on 2007-10-21
i have had the same problem and managed to find an answer .... i could only boot up using the 2.6.20.16 kernal not the latest 2.6.22.14 ... and then i found an answer ... :KS

and it is posted on the post .... [http://ubuntuforums.org/showthread.php?t=582199&highlight=busybox](http://ubuntuforums.org/showthread.php?t=582199&highlight=busybox)

on post no.8 ...
:popcorn: 

here it is ....  it worked for me 

While 7.10 won't install for me either, I had no problem with this "ATA failing cause I don't have sata" issue while installing 7.04 but I had a slow boot and at the end of this post and I'm sure this is the issue with the 7.10 installation. (See the fix I used below).

The fix is great for the installed system but how do we modify a CD? I have no idea how to make it ignore "ata_piix" and use "ide_generic". Boot options? Some busybox commands?

It would be real nice if someone posted the steps to make this work for the the newbie and if it couild be made "sticky" in the forum, even better. This is messing up a lot of people.

************
edit /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

**************

Credit for this 7.40 slow boot fix goes to "Fabio Povoledo". He had it posted in a forum somewhere and I was days finding the solution. I saw a lot of people trying to fix the slow boot issue. I assume none of these people could do a fresh 7.10 install.
__________________

---

### Post by guitard00d on 2007-10-22
> **platypuss72 said:**
> Credit for this 7.40 slow boot fix goes to "Fabio Povoledo". He had it posted in a forum somewhere and I was days finding the solution. I saw a lot of people trying to fix the slow boot issue. I assume none of these people could do a fresh 7.10 install.

Ubuntu just smeared egg all over its face by launching this useless bug-ridden release. Too much focus on getting this release out the door in 6 months and not enough testing it on multiple hardware setups. What a total embarrassment, I was actually looking forward to this, and all I have out of it is a couple wasted CDRs. Yeah, a couple wasted ones, because someone in these forums said the entire problem was due to a faulty burn. Uh, no, both burns exhibit the same result and both images  have the same MD5 checksums. This is going to scare away OEMs with a quickness... :(

---

