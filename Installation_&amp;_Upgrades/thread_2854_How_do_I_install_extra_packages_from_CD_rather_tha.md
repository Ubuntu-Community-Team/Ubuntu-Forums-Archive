---
title: "How do I install extra packages from CD rather than internet connection"
date: 2004-11-01
forum: Installation &amp; Upgrades
---

### Post by Rob on 2004-11-01
I'm fixing up an oldish computer for my parents to use. I've tried Ubuntu on it and it seems to be just what's needed. In fact, more than that, it seems very impressive.

Currently this computer is not connected to the internet, and when my parents have it they will only have a slow dial up connection. I need to find out how to use my broadband connected computer to write packages to CD so I can install them on my parent's machine.

I've searched around looking for an explanation of how to do this and not found much yet. I'm guessing I can just download things from [http://archive.ubuntulinux.org/ubuntu](http://archive.ubuntulinux.org/ubuntu), write them to CD, then take them across to the unconnected machine and somehow tell Synaptic to install from that CD.

I suppose my questions are:-

1. Will something like I've described above work?
2. Will I have to find all the dependancies by hand and make sure I put those packages on the CD too? And will just reading the dsc file tell me this?
3. Is there an easier way of doing this I've missed?

Thanks a lot,

Rob.

---

### Post by im_ka on 2004-11-01
just add the cdrom drive to /etc/apt/sources.list by hand or do it through synaptic.
as far as i can remember,  cdrom is even included in the default sources.list.

---

### Post by Rob on 2004-11-01
Thanks for your help, im_ka, I suspected it would be easy to install packages from a CD using Synaptic.

Do you have any thoughts on the best way to get the right data onto the CD in the first place? I suppose that's the part I'm most unsure about, and what I was trying to get at with my second and third questions.

Thanks a lot,

Rob.

---

### Post by jdong on 2004-11-01
You can place .debs from archive.ubuntu.com into /var/cache/apt/archives, and apt will get it from there.

---

### Post by Rob on 2004-11-01
[QUOTE=jdong]You can place .debs from archive.ubuntu.com into /var/cache/apt/archives, and apt will get it from there.[/QUOTE]

Following on from this, suppose I have identical Ubuntu installations on my parent's PC with no internet connection, and my PC with a broadband connection, would this work:-

1. Use Synaptic to install an extra package on my PC, which I believe will give the option of installing whatever packages are needed to resolve dependencies
2. Look in /var/cache/apt/archives on my PC to see which new .deb files have appeared
3. Write these .deb files onto a CD
4. Put the CD in my parent's PC and install using Synaptic

Is there a better way?

Sorry to keep seeking clarification, but as the PC's are not in the same location doing this by trial and error will be time consuming.

Thanks a lot,

Rob.

---

### Post by Juergen on 2004-11-02
[QUOTE=Rob]3. Write these .deb files onto a CD
4. Put the CD in my parent's PC and install using Synaptic[/QUOTE]

Installing directly from CD with 'dpkg -i' should work, but for apt and synaptic AFAIK you need to create a Packages.gz via dpkg-scanpackages and burn this on the CD too.

I'm using apt-move to create a local repository that can be burnt - it does all the work for you. Just burn it on a CD-RW until it's full, then start with a new, empty repository and a new CD.

And then there is apt-zip, but I don't use that.

---

### Post by Rob on 2004-11-04
Thanks Juergen, you’ve managed to get me most of the way there. What I tried last night was:-

1. Copy the .deb files from the CDRW I’d burned into a folder in my Ubuntu home directory
2. Used the following command in the folder:-

[FONT=Courier New]dpkg-scanpackages . /dev/null | gzip –9c > Packages.gz[/FONT]

(I’ve just looked up what the –9c means, out of curiosity, and found it means highest (though slowest) compression with the output going to stdout)

3. I then put the contents of the new folder back onto the CDRW using Nautilus, which incidentally meant the original contents got erased
4. Under Synaptic there is an option to add a CD, which I did. After saying I didn’t want to add another one Synaptic crashed
5. When restarting Synaptic it complained about the /etc/apt/sources.list file, so I went and had a look
6. The entry for the CD I’d just added didn’t seem to have been added correctly – the line started with “/ cdrom”, so I removed the space and added a deb at the start of the line to make it look more like the installation CD entry.
7. Synaptic was then happy to include the extra three packages from my CDRW in the list of available packages
8. I tried installing them but each of the three needed another package or two I didn’t have, or a more up to date version of something that was installed on my system.
9. By right clicking on each of the three packages and looking at the properties option I found out what else I needed

So my plan is to download the extra packages next time I’m able to access my broadband connected PC and hope they in turn don’t rely on something else, or I could be going backwards and forwards for a long time.

What I’ve described is one way of doing it (installing new packages from CD onto a PC without an internet connection). It has the drawback of not finding out about dependencies until late in the process and having to go backwards and forwards.

Can anyone suggest another method?

Juergen , would you be willing to post more details about how you use apt-move? I’ve had a look at the man pages but not got my head round it yet.

Thanks a lot,

Rob.

---

