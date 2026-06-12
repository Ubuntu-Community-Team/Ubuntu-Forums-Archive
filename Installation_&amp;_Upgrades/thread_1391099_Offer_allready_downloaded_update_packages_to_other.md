---
title: "Offer allready downloaded update packages to other computers"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by drfFlK on 2010-01-26
In our School we have 20 Computer with Ubuntu installed. Our problem is that the internet connection isn't really fast and updating all 20 computers separately consumes a lot of bandwith.

I'm searching for a way that allows us to update the teacher's computer first and, after that, update the other computer using the packages the teacher's computer allready downloaded (if some package is missing it must still search it via Internet).

I readed documentation about apt-mirror but that will configure a complete mirror, downloading all packages (21 GB!!), which is not really necesary.

Thanks in advance.

---

### Post by earthpigg on 2010-01-26
once downloaded and installed on a single computer, the files go to /var/apt/cache/archives on that computer.

from there, you can copy them onto the other computers and use dpkg to install them.... or, i am fairly sure if you ran 'sudo apt-get whatever' on those target computers, it would verify that it already had the current version, skip downloading it 'over' again, and install the one it finds in it's own /var/apt/cache/archives.

a slightly more complex version of this would be to use sshfs to mount the teacher's computer's /var/apt/cache/archives folder at /var/apt/cache/archives on each local machine. how strong is your networking-fu? 

this was the guide i read when i got started with ssh and sshfs: [http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)

you will need to translate the arch instructions to ubuntu (ubuntu is an easier to use distro than arch, but the arch wiki is the best one out there in my opinion. i always go there before looking at ubuntu documentation.)... replace 'packman -Sy' with 'sudo apt-get install', and ignore the stuff about 'daemons' as ubuntu does that automatically.

basically, here is how i would go about this:
0. set up and fully configure ssh and sshd on the teacher's computer and one other. test it, make sure you have the process down.
1. sit down at each of the 19 other computers and set it up.
2. sit at the teacher's computer. ssh to studentcomputer1. use sshfs to mount the /var/apt/cache/archives folder on teacherscomputer to /var/apt/cache/archives on studentcomputer1.
3. from teacherscomputer while ssh'd into studentcomputer1, run sudo apt-get update.
4. rinse, repeat with the 19 remaining.

5. for the long term, start working on a bash script that will execute steps 1-4 for each of the studentcomputers. the desired endstate is that you sit at teacherscomputer, and a single command that downloads and installs updates once, and then does so on every other computer but downloads them from teachercomputer over the LAN instead of from the ubuntu repos..

if you don't want to get that complex about stuff, you can just burn a CD or DVD with all the stuff from the teacher's /var/apt/cache/archives and go from computer to computer, installing all the packages on the cd.

if you want to go the complex/nerdtastic/elegant way (***not*** burning a dvd, and using the LAN and ssh/sshfs), and you can't figure it out on your own, let us know and we can help you out.

---

### Post by earthpigg on 2010-01-26
well, that's how i would go about it anyways. mostly because i am already familiar with ssh, and its 'simple'. ssh let's you remotely control a computer. sshfs let's you mount a folder on another computer on the network as if it where a local folder. the primary thing i do with sshfs is listen to all my music stored on my desktop at my house while on my netbook (8gb hard disk) at my girlfriends house - my personal little streaming multimedia server :P .

but there is more than one ways to skin a cat.

what non-trivial networking tools are you already familiar with? perhaps we can adapt that tool to serve here.

---

