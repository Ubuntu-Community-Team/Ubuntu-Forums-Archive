---
title: "Advice requested: getting ubuntu into schools"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by lpkb on 2005-07-06
First of all, I am new to Ubuntu (and largely new to Linux).

I work at a non-profit and we have a largely volunteer-run program in which we accept donated computers from businesses (usually as they replace their fleet of computers with new ones), and then we piece them together into working units and donate them to schools, non-profits, social justice groups, etc.

Instead of hassling with finding old copies of Windows, etc. I want to make a proposal to the executive director that we install Ubuntu. Usually we get batches of computers that are identical (10-20 computers at a time) or very similar, so ideally I'd like to do one installation, install anything that might be useful which isn't in the default package (eg. probably a windows emulator, or something like that) and then be able to ghost that disk image onto all the others, so that I only have to do the setup and tweaking once.

I am interested in any advice about any part of this procedure as I want to make a solid proposal which foresees any problems or potential reservations the E.D. may have, and have an answer ready.

What do you say? Here's some questions to start:

*what else should be installed besides the default ubuntu installation?
*what resources are available to the schools/sysadmins if they want to get help (besides this forum)?
*any advice on the ghosting options?
*should i also include documentation about Ubuntu or just a weblink?

If you have any thoughts or ideas or questions, throw them in the mix!
Thx.

---

### Post by sigma2805 on 2005-07-06
hello and welcome to the forum. regarding the ghosting, you can use the [System Rescue CD](http://www.sysresccd.org/) to create a backup of the ubuntu partition. this is done using Partimage. here is the debian.org page about partimage.
[http://packages.debian.org/unstable/admin/partimage](http://packages.debian.org/unstable/admin/partimage)

the manual for the system rescue cd is located at 
[http://www.sysresccd.org/manual.en.php](http://www.sysresccd.org/manual.en.php)

looking through the list of packages on the ubuntu cd, it looks like it doesn't include this utility by default so this looks like the way to go for you to be able to "ghost" the other machines.  

for a list of resources available i'm assuming you want something like technical support besides this forum. here is an exhaustive list of places that provide technical support and services 

[http://www.ubuntulinux.org/support/supportoptions/marketplace/view?searchterm=services](http://www.ubuntulinux.org/support/supportoptions/marketplace/view?searchterm=services)

in my opinion i would include some documentation about Ubuntu. Include what it is, what ubuntu means stuff like that cause the executive director probably hasn't heard of ubuntu before. I would also include the overall benefits of ubuntu versus other distributions versus windows. 

I'm not sure what other programs you would need besides the other install. what i would do is make a list of programs that you currently install in windows then take a look at [this post](http://www.ubuntuforums.org/showthread.php?t=33183) to see what some alternatives would be.

I hope i helped :)

---

### Post by lpkb on 2005-07-06
Thanks! I'll have to check that out.

I guess I am also looking for suggestions as to software--things that will make this successful in the school computer labs, maybe even providing some software they don't use currently but might have an educational use for...etc. Currently if we can find an old copy of Windows to include with the computer we install it but not much else--I want to wow them with open source, though.

Thx

---

### Post by varunus on 2005-07-06
I would recommend providing all of the computers with Java, Flash, and Realplayer, which are not installed by default in Ubuntu but are available.

The ubuntu guide might be a good thing to include too, or some of the howtos in the tips and tricks section.

---

### Post by bored2k on 2005-07-06
[QUOTE=varunus]I would recommend providing all of the computers with Java, Flash, and Realplayer, which are not installed by default in Ubuntu but are available.

The ubuntu guide might be a good thing to include too, or some of the howtos in the tips and tricks section.[/QUOTE]
 Consequently, you could create custom disc with its own custom installation script containing the applications not included in Ubuntu. If the users will be people not really interested in technology, you might consider Kubuntu as its usually easier for old Windows users (note: KDE can be slower than GNOME, so it depends on the speed of the box).

Extra apps? 
Adobe Reader
Macromedia Flash
Sun JRE
MPlayer or Totem-xine with w32codecs (for streaming -- you would need to disable ESD to get RealPlayer working)
Mozilla Thunderbird
Abiword+Gnumeric (if they're slow computers)
Free Windows emulator (QEmu) [http://www.ubuntuforums.org/showthread.php?t=39513](http://www.ubuntuforums.org/showthread.php?t=39513)

---

### Post by sigma2805 on 2005-07-06
hmm...i guess in a school it would also depend on what the computers would be used for. for example, in an html class include nvu. In a programming class include one of the open source compilers. probably wouldn't want gaim  [-X  in a school so i would remove that using synaptic. i'm really trying to think of programs i used in school. openoffice already comes with ubuntu. hmmmm....maybe inkscape hmmm....this is tough!  :)

---

### Post by bored2k on 2005-07-06
[QUOTE=sigma2805]hmm...i guess in a school it would also depend on what the computers would be used for. for example, in an html class include nvu. In a programming class include one of the open source compilers. probably wouldn't want gaim  [-X  in a school so i would remove that using synaptic. i'm really trying to think of programs i used in school. openoffice already comes with ubuntu. hmmmm....maybe inkscape hmmm....this is tough!  :)[/QUOTE]
 Yes absolutely no Gaim. I'm not even sure you would want SUDO on school computers (maybe disable it student accounts). And those computer would absolutely need bios passwd protection so you can block booting from floppy or CDs. This way you would avoid anyone trying to use Knoppix or Tom's floppy disc ;).

---

### Post by mingus on 2005-07-07
I run a new non-profit with a similar mission to yours, although our target benefiaries are lower-income students of all ages without internet-connected computers in the home, as opposed to organizational entities.  

It appears with the various entities you support, you may have more than one set of requirements.  Perhaps there will be users like ours above, but others very different.  Some general comments:

*what else should be installed besides the default ubuntu installation?*

Again, the challenge is the multiple audiences and requirements.  With the students above, if the system does not perform reasonably well and include the "popular" applications, and is not easy to use, many will end up unused - or broken; kids are bright but we don't want then compiling right away!  This may also be true of recipients of some non-profits that you support.  Not hard to find out what youngsters want; take a straw poll.  On the other hand, school systems will probably have strict rules about the apps, plus rqmts for security and administration.  Our advice is, don't guess; ask them.  

*what resources are available to the schools/sysadmins if they want to get help (besides this forum)?*

Our strategy is to circumvent as much as we can through proactive training and documentation.  We require training to get the system; it's bundled in the cost.  The training center doubles for support, and we invite users to stop by with questions.  We also offer a 90-day warranty with email support.  After that, they are on their own with the Forums, wiki, and google.  But again, if you are delivering to schools, you have a hurdle:  You have to coexist with their W$ environment, the staff probably knows nothing about Linux and may feel threatened by it.  You may have to do extra work to accomodate the schools security and network architectures; you may not have had to do this with W$ systems but with Linux you probably will.  Again, our approach would be to collaborate in advance with them on a model.  You can get professional support from Ubuntu or possibly resellers in your region, but that is usually cost prohibitive for non-profits; that info is in the Forums and the wiki (see Marketplace).

*any advice on the ghosting options?*

There are a lot of alternatives.  Look *very* carefully at the bit-imaging tools.  Some are geared towards cloning to a partition of the same size; you can put the image on a larger partition, but to utilize the full space the partition will have to be resized.  Also, some of these tools work with individual partitions only, others with only the whole disk.  Another consideration is whether you are imaging each system individually by hand, using a batch method, or using a network.  You can find a lot of suggestions by googling; this is a general Linux thing, not specific to any distro.

We haven't made a final decision, but we seriously considering just using tar.  Tar was originally written for tape file transfer (or backup).  It supports compression, and preserves file attributes and permissions.  It can be segmented across multiple media (like CD's), and can be used over the network.  So we like its flexibility and reliability.  We will probably image like systems in groups of 10 from a network server, using a Live-CD and a script to automate the process.  Come to think of it, this isn't difficult just using the cp command with the -a option, if you don't need the compression.

We are pre-architecting the systems.  We will be buying off-lease equip in volume, rather than taking donations.  This enables us to verify in advance, and do the inevitable config and tweaking, to get the hardware working right - if you are taking in a wide variety of hardware, you are going to spend a fair amount of time doing this.  This is especially true with some makes/models, with quite a few different components for a given function (check out how many diff audio or video devices you will find in some Dell's!).  We will only be using PIII's with the Coppermine core with 256MB RAM (our price is $200US).  We will then create images that are specific to each hardware/software combination.
  
*should i also include documentation about Ubuntu or just a weblink?*

Our documentation, delivered with the training, will all be on the system; no hard copy expense.  It will stress the various ways to get information or assistance.  We really don't want to provide out-of-warranty support, although we may provide a per-incident service.  Here you have an advantage with sysadmins; they are used to looking for answers.  The challenge is, will they understand what they find?  Another topic to discuss in advance.

Regarding training and documentation, do a wiki search from google (better than the wiki search engine).  There are several projects underway in this area.  You can get on the mailing lists to determine the status.  There may be a lot that you can leverage.

Good luck!

---

