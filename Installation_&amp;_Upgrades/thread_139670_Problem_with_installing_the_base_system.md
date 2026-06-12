---
title: "Problem with installing the base system"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by Gipper P on 2006-03-04
Hi there

I recently got the .iso for Ubuntu 5.10 and made the CD with which I am trying to install this OS on my laptop. However, approximately 67% of the way through the 'Install the Base System' stage of the installation, I get an error message saying that 'initrd-tools' cannot be installed and telling me to check '/target/var/log/bootstrap.log'. I don't think I can check this, since I dont actually have the OS installed! I could just do with some pointers as to what to do next.

Thanks in advance for your help!

Gipper

---

### Post by 4dz0 on 2006-03-04
Sorry if this post seems a little patronising - did you check the downloads md5sum?

---

### Post by Gipper P on 2006-03-04
... maybe I didn't specify that I am a complete newbie to this... so it isnt patronising, maybe I should check the newbie section? thanks for the pointer :) , I know its annoying when you get newbies posting questions in the wrong sections about things that should be easy to know!

edit: I looked on the md5sum file on the CD, wasnt quite sure what to look for, but found the following lines  when searched for 'initrd':

b22a20957c064ce6881a4f37085691db  ./pool/main/p/preseed/initrd-preseed_1.04ubuntu2_all.udeb

d99df13b470003a20ef081cee061ed6e  ./pool/main/k/kickseed/initrd-kickseed_0.31_all.udeb

ccf8a05a926a12adf3d4973e29eb688e  ./install/initrd.gz

8897f7006331765c1e691e5b2634b713  ./install/initrd.list

f32c1a4b6aac58d8824f9c498828002d  ./install/netboot/ubuntu-installer/i386/initrd.gz




do these seem in order?


Also, if it helps with diagnosis you might want to know the system I am trying to run it on. Its quite an old one (which could be part of the problem!!)...

Pentium 2 233Mhz
96MB RAM

erm... thats all I can find out at the moment!

---

### Post by Gipper P on 2006-03-06
hey sorry to bump this, but is there any solution to this problem? or shall I just download a new file and burn it on a new CD at a slower speed?

---

### Post by play0r on 2006-03-06
i had a similar problem myself. what i ended up doing was this:
do a "server" install. 
once the base system is installed issue these following cmd's:
"sudo aptitude update"
"sudo aptitude install ubuntu-desktop"
& viola.
i hope this helps you out. please post if it works.

<3
play0r

---

