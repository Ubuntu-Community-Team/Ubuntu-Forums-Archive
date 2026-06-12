---
title: "Pre-Migration Questions"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by dasunst3r on 2005-04-20
Hi, everybody!  I am considering deploying Ubuntu as a replacement to Fedora Core 3 because of these reasons:
1. No MP3, scanner, NTFS support out of the box
2. Need to type in /usr/bin/{command} or /sbin/{command} for a few commands
3. Have to deal with multiple repositories
4. No power management support
5. SELinux = bloatware

Now I have a few pieces of software whose binaries are only distributed on RPMs, such as National Instruments' LabView, OpenOffice, Skype, and Webmin (all of which are noarch RPMs).  From what I found, all I need is the "alien" command, is that right?

I am also getting a laptop this summer.  For those of you who are running Ubuntu without problems on your laptops, can you tell me what model it is so that I can look into its options?  I don't care if it's on the business line, but I do care if the processor's a Celeron or if the brand is not well-known.

Finally, as far as servers are concerned, if I want to update my server at home from anywhere (e.g. my dorm), I can just ssh into the server, type in "apt-get upgrade," and let her rip, right?

Thanks in advance!  I look forward to jumping off the Fedora ship and onto a cool distro! :)

---

### Post by Leif on 2005-04-20
You can use alien to convert rpms to deb, but at the very least OpenOffice and Skype have debs themselves - Openoffice is in the main repositories (even the v2 beta), and you can download skype debs.

Yes, you can remotely keep things updated, but you'd need to apt-get update before upgrade.

---

### Post by Stormy Eyes on 2005-04-20
Ubuntu doesn't have MP3 or DVD support out of the box either, for legal reasons.

---

### Post by dasunst3r on 2005-04-20
[QUOTE=Stormy Eyes]Ubuntu doesn't have MP3 or DVD support out of the box either, for legal reasons.[/QUOTE]OK... it looks like MP3 and DVD support can easily be acquired by using Synaptic, so I'm not too concerned :)

P.S. Props to you all for the great documentation I found about adding repositories and laptop support!  The laptop support section really gives me a good reason to switch. :)

Now can you guys point me to a place where I can download (preferably via BitTorrent) the DVD ISO with many packages in it?  I want to be able to get done with install faster.

And oh, yes... a bootloader will be installed and the installation will detect my Windows XP installation, right?

---

### Post by woifi on 2005-04-21
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

warty added the lines for winxp in the grub.conf, i guess hoary does that too ;)

---

