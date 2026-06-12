---
title: "Install HELP.  ubuntu just won't install at all!!"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by snorkrat on 2007-05-30
Okay i'm getting quite annoied now.  i searched a bit before posting and coulnd't find any answers so here goes..

I downloaded the latest ubuntu desktop cd (7.04).  burnt the image to cd, booted up and ran the cd check - it passed.  i then proceeded to start/install ubuntu and it booted from the cd fine.  when i got into the live cd i then wanted to install ubuntu.  i went through all th setup/partitioning etc but the install fails time and time again.

i thought it might just be a problem with the cd - so i downloaded the alternate cd and tried the text based install.  again i went through all the options and partitioning etc.  it gets past the base install but hangs at the software etc install.

i'm brand spanking new to linux and ubuntu so i really don't know what to do.  does ANYBODY know what i can do??

thanks in advanced

-Scott

---

### Post by Shinobi326 on 2007-05-30
> **snorkrat said:**
> Okay i'm getting quite annoied now.  i searched a bit before posting and coulnd't find any answers so here goes..

I downloaded the latest ubuntu desktop cd (7.04).  burnt the image to cd, booted up and ran the cd check - it passed.  i then proceeded to start/install ubuntu and it booted from the cd fine.  when i got into the live cd i then wanted to install ubuntu.  i went through all th setup/partitioning etc but the install fails time and time again.

i thought it might just be a problem with the cd - so i downloaded the alternate cd and tried the text based install.  again i went through all the options and partitioning etc.  it gets past the base install but hangs at the software etc install.

i'm brand spanking new to linux and ubuntu so i really don't know what to do.  does ANYBODY know what i can do??

thanks in advanced

-Scott

I think you need to be more descriptive when you say "the install fails time and time again".  What do the error messages say?  What is the computer doing to indicate to you the installation has failed?

---

### Post by merlinus on 2007-05-30
Are you dual-booting with windows?  If so, are you trying to re-size your windows partition to make room for ubuntu?

If so, you may be better off downloading gparted live cd ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) and manually creating the partitions for installation.

And be sure to defrag your windows partition several times, and zero out virtual paging, which can be restored after installing ubuntu.

This page may also help:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck!

-merlin

---

### Post by snorkrat on 2007-05-30
> **Shinobi326 said:**
> I think you need to be more descriptive when you say "the install fails time and time again".  What do the error messages say?  What is the computer doing to indicate to you the installation has failed?

when using the normal cd it fails either at 78% when creating files or else when it is "configuring system locales".  I know it has frozen because i can go away and come back 30 mins later and it is at the same place, and the mouse doesnt move - it's just frozen.

when using the alternative cd it fails at the "Select and install software" stage, either at 1% when "configuring languange-pack-en-base" or else near the end when it is configuring something like support language or something (i cant remember the exact time it freezes near the end)

> **merlinus said:**
> Are you dual-booting with windows?  If so, are you trying to re-size your windows partition to make room for ubuntu?

If so, you may be better off downloading gparted live cd ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) and manually creating the partitions for installation.

And be sure to defrag your windows partition several times, and zero out virtual paging, which can be restored after installing ubuntu.

This page may also help:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck!

-merlin

i have 3 HDDs an IDE with windows and data on it, a SATA with just data and another SATA which is clean.  i am trying to install ubuntu on the 3rd, unused, clean SATA HDD.


again - thanks for the fast replies.

oh my specs, incase you need to know are:

AMD X2 3800+
2GB Corsair XMS RAM
DFI Lanparty SLI-D
Asus 7800 GTX

---

### Post by merlinus on 2007-05-30
My suggestion would be to use the gparted live cd to create the partitions (/swap, /home and /) on your sata drive beforehand, and then install to those.

It might work....

-merlin

---

### Post by snorkrat on 2007-05-31
> **merlinus said:**
> My suggestion would be to use the gparted live cd to create the partitions (/swap, /home and /) on your sata drive beforehand, and then install to those.

It might work....

-merlin

Thanks for the help, but unfortunatly this didnt work either =[

any other suggestions? i just want to get ubuntu up and running!  but cannont get past the install at all!!

---

### Post by snorkrat on 2007-05-31
bump?

---

### Post by rsain on 2007-05-31
I had a similar problem on my clean install of 7.04 Server (x2200 with SATA 250g x2) but it was solved by correct partitioning during the installer. I was screwing up the RAID config.

What choices are you making along the way (exactly)?

- Ryan

---

### Post by snorkrat on 2007-05-31
> **rsain said:**
> I had a similar problem on my clean install of 7.04 Server (x2200 with SATA 250g x2) but it was solved by correct partitioning during the installer. I was screwing up the RAID config.

What choices are you making along the way (exactly)?

- Ryan

i dont have a RAID setup on my pc.   i'm just letting it auto partiton the full HDD during install.  so i doubt it's making a mistake.  also because it (in txt installer) installs the base system - just not the software etc.

---

### Post by sk545 on 2007-05-31
> when using the normal cd it fails either at 78% when creating files or else when it is "configuring system locales". I know it has frozen because i can go away and come back 30 mins later and it is at the same place, and the mouse doesnt move - it's just frozen.

Hey guys, i am having the EXACT same problem.  It just freezes at "system locales".  Is there anyway to get a more verbose output during install or maybe drop to a root terminal?  I mean, i can't even move the mouse and the keyboard dies too when this happens.

I am dual booting with XP, and have the partitions like so:

/dev/hda1 : NTFS (primary, boot flag)
/dev/hda2: NTFS (primary)
/dev/hda3: FAT32(primary)
/dev/hda4: Extended
/dev/hda5: reiserFS (mounted on /)
/dev/hda6: swap



The extended and the other ones i made through the ubuntu manual paritioning utility that comes with the installer.

I have gone through 3 cds's and have checked the md5sums and also a cd defect check in the beginning of the ubuntu installer.  So its not a cd problem (i even have the official ubuntu cd's from shippit, and they give the same result).

Specs:

X2 3800+
1GB DDR 3200
6600GT
MSI K8N neo4 Platinum
USB mouse
PS/2 keyboard.
i386 Desktop Ubuntu iso.

Here is another post with someone with the same issue:

[http://ubuntuforums.org/showthread.php?t=246375&highlight=system+locales](http://ubuntuforums.org/showthread.php?t=246375&highlight=system+locales)

---

### Post by snorkrat on 2007-05-31
glad i'm not alone on this!!

it's really frustrating as the partitions (in my eyes) are fine, and i'm doing nothing wrong.  the cds are fine - no defects and everything seems to be setup correctly, yet it just won't install for some unknown reason!

edit - i just noticed you're using a X2 3800 + (like me)  i take it you're using the amd64 bit Ubuntu version? well, that's the one i am using anyway!

---

### Post by MattAd on 2007-05-31
I've been having a similar problem in both Ubuntu and Kubuntu, on the Live CD and alternate CD. The impression I'm getting is that there's problems with my hard drive. I've run fsck, fixed errors, but still have the same problem. Am I missing something, or is my hard drive just completely broken?

---

### Post by snorkrat on 2007-05-31
> **MattAd said:**
> I've been having a similar problem in both Ubuntu and Kubuntu, on the Live CD and alternate CD. The impression I'm getting is that there's problems with my hard drive. I've run fsck, fixed errors, but still have the same problem. Am I missing something, or is my hard drive just completely broken?

well my hard drive is fine, it should be it's brand new.

i've completely wiped it of everything and ubuntu is the only thing that is going on it.


Unless anybody can figure out how to get past this problem i think i'm going to just use the 32bit version or try UbuntuStudio.

---

### Post by sk545 on 2007-05-31
> **snorkrat said:**
> glad i'm not alone on this!!

it's really frustrating as the partitions (in my eyes) are fine, and i'm doing nothing wrong.  the cds are fine - no defects and everything seems to be setup correctly, yet it just won't install for some unknown reason!

edit - i just noticed you're using a X2 3800 + (like me)  i take it you're using the amd64 bit Ubuntu version? well, that's the one i am using anyway!

Nah, i am using the 32-bit version of Ubuntu Desktop iso.  Even that doesn't work, but give it a shot...maybe it'll work for you.

I found this thread:

[http://ubuntuforums.org/showthread.php?t=319397](http://ubuntuforums.org/showthread.php?t=319397)

It says to run this command:

cd /usr/lib/locale

sudo ln -s es_ES.utf8 es_ES 


However, how do you run the above command during installation when the system is frozen??

Another option is to use the alternative iso of Ubuntu...that doesn't have the gui, but its still not too difficult to use.  I did try it, and the install went fine.  However, when it rebooted and the desktop came up, both my mouse and keyboard froze after a few minutes :(

---

### Post by sk545 on 2007-06-01
bump

---

### Post by saikat on 2007-06-01
I'm also having the same problem. I'm trying to install Kubuntu 7.04 amd64 bit edition. Also tried Ubuntu 7.04 32 bit. [COLOR="Red"]Every times installation stalls at "Select and Install Software" section at 85% ("Installing openoffice.org-java-common").[/COLOR]

My configs are:

[COLOR="SeaGreen"]AMD Athlon64 X2 Dual-core 3600+
Biostar NF61V MicroAM2 mother board
1 GB DDR2 533 RAM
nVidia GeForce 6200 256MB PCIe graphics card
160 GB Seagate SATA + 40 GB Seagate IDE  HDD
IEEE1394 Fireware Card
Windows XP Home installed on SATA[/COLOR]

[COLOR="DarkOrange"]Please help us!!!![/COLOR]

---

### Post by mettu on 2007-06-01
I've been having similar problems and have noticed we and others are all using AMD Athlon 64  CPUs + SATA drives ...

Could this be the reason?

---

### Post by sk545 on 2007-06-01
who knows, i mean, without the console giving the messages, there is no way to know where its hanging.  Is there any way to have it do a verbose install?  Anyone?  Anyone?

---

### Post by sk545 on 2007-06-02
Bump

---

### Post by saikat on 2007-06-03
[COLOR="Lime"]Solution at last![/COLOR]

Hey guys! I was so foolish. I've found the solution. [COLOR="DarkOrange"]You have to be connected to the internet for installing 64bit version of Ubuntu/Kubuntu.[/COLOR]
Here it is: 
1) During installation configure your network card
2) Keep your modem on
3) During "Select and Install Software" section at around 85% after installing "openoffice.org-java-common" the installer will fetch some sources and some small packages from Ubuntu multiverse & universe repository. 
4) Installation will complete within minutes.

To view the detailed process of installation you may activate console by pressing **Left Alt + F4** and return to text mode installation screen by pressing **Left Alt + F1**.

Happy exploring Ubuntu! :popcorn::D

---

