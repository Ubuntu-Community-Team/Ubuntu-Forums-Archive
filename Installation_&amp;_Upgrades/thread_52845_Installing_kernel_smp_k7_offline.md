---
title: "Installing kernel smp k7 offline"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by abs on 2005-07-29
hello all,

I have downloaded the kernel smp k7 image, and tried to install it but there was a dependency problem, I dont have the internet, and my system is a dual AMD athlon MP, but have 686 kernel installed, silly me. anyhow back to the problem,

when i try to install the kernel, i get a problem saying, that i have the wrong initrd or something similar, sorry about this i should be more precise but forgot to cut and past the error msg,

it basically says i have version initrd ubuntu3 when it needs initrd ubuntu2,

Ill post it when i get into work on Monday,

but if anyone has an idea do let me know, 


thanks people,

p.s. ubuntu is great, :)  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/

---

### Post by kosmic on 2005-07-29
Try this :

in a machine with intenet acess with ubuntu in it do :

sudo apt-get clean
sudo apt-get autoclean

then
sudo apt-get install -d linux-headers-k7-smp

then
mkdir /tmp/debs
sudo cp /var/cache/apt/archives/*  /tmp/debs

and finaly
cd /tmp/debs
sudo dpkg-scanpackages .* | gzip > Packages.gz

"EDIT -> I FORGET TO WRITE THIS STEP, IT IS VERY IMPORTANT"
mv Packages.gz /tmp/debs

when it finish...copy the content to a CD, go to your SMP k7 machine and insert the CD and in the file -> /etc/apt/sources insert :

deb file:/media/cdrom debs/ 

then 
sudo apt-get update
sudo apt-get install linux-headers-k7-smp and voila :)

It will resolve all the dependecies problems

---

### Post by abs on 2005-08-02
cheers dude,

I will give it a try and see how it goes, thanks again for that,


/abs

---

