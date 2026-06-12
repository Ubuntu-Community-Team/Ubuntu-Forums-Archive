---
title: "Problems installing Xubuntu"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by Oren on 2006-04-22
Hi

I must be doing something completely wrong....

I downloaded an image of Xubuntu 6.06 (***not live cd***) burned to CD and tried to install but midway through the install, warnings started coming thick and fast telling me most of the packages are corrupted.

What gives?

Does anyone know why this is happening?

Thanks.

---

### Post by mscman on 2006-04-22
Sounds like your CD is corrupt; did it pass the CD integrity check?
Try downloading and burning the image again.

---

### Post by Oren on 2006-04-22
Hi and thanks.

I have downloaded twice and burned twice.... :( 

I will try and use a different media.... :confused: 

Anyway of checking the image before burning? :-k 

Thanks, again.

[COLOR="Blue"]**Update: Media change did not help... So I am assuming it is the image afterall. However, no harm in trying again. Oh well, it only takes a couple of hours to download and about 15 minutes to burn so... what the hell....**[/COLOR]

---

### Post by jchomarat on 2006-04-23
What the status because I have the same probleme. I tried 2 times, and cannot install it

---

### Post by Sef on 2006-04-23
> Anyway of checking the image before burning? 

Yes.  Do an md5sum to check the file before burning.  There is a number from the site that you burned and it should match the md5sum.  If not, you got a bad iso.

Applications > Accessories > Terminal

change to the directory where the iso is located.  'cd ~/directory_where_file_is_located' (without the quotes)

then

md5sum path_to_file

The other option is downloading bitorrent (if you don't have it) and using it to download.  It md5sums the iso while downloading.

Note: Don't burn your iso at more than 4x.  Faster may cause corruption of the burned iso.

---

### Post by Oren on 2006-04-23
Hi

First thing's first, thanks sef for your tips! 
I will definitly implement these next time I need to download and burn a distro image.

[QUOTE=sef]The other option is downloading bitorrent[/QUOTE]

Did both HTTP and Bittorrent. The problem occured with both images.

Anyway, problem solved with the live image. I am not sure if other users are aware but once logged in with the live CD you can install Xubuntu.
I did that, configured my Speedtouch 330 (should be set-up as with Kubuntu Dapper Drake) updated my packages and upgraded whatever needed to and that's it.

I really like the new install and cannot wait for the proper release in June. :cool:

---

### Post by tut21 on 2006-04-24
I'm experiencing the same problem with corrupted ISOs but the LiveCD isn't an option for me due to incompatible video drivers. The screen fills with garbage and I can't continue.

The ISO verifies fine after I download it. I've ratcheted down the speed of my burner but the ISO is still corrupted and my MD5 utility hangs when trying to verify its integrity. The Ubuntu installer doesn't like it either and it picks a random file to crash on each time.

**Update:** Putting it on a CD-R instead of a CD-RW seemed to fix the problem.

---

