---
title: "Defragmentation"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by doubleeagle on 2006-02-28
Hey,

I'm pretty new to all this so forgive me if this question is stupid. I'm intending on installing ubuntu along with windows xp on my laptop. I've defraged my hd using windows defrag, but instead of putting all the data to the start of my hd it shows it as been in 3 seperate large blocks. Will ubuntu regconize this as one when i try to partition the hd? Or do i need to have it all at the start of the hd?

Thanks.

---

### Post by uberlaff on 2006-02-28
Your best bet for installing all Win XP and Ubuntu on the same machine is to start from scratch and keep the two on seperate partitions.  

Have you tried using the Live CD?  This will boot your PC into linux off the cd without doing anything to your hard drive.  This is your safest bet for trying out Ubuntu...

---

### Post by aysiu on 2006-02-28
Defragmentation in Windows defragments only what it can. Sometimes there are unmovable blocks of data even after defragmentation.

The partition is still *one* partition. It's only the data *within* that partition that's in blocks.

P.S. Best dual boot guide:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by manicka on 2006-02-28
you may find these articles useful

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by tomski on 2006-02-28
Ubuntu will not 'move the windows files' it will ignore them until you 'mount' the windows drive (tell ubuntu that this disk can be accessed)

when you say 'it shows it as 3 seperate blocks' do you mean the entire hd if so then that maybe because you 3 partitions on the hd in question (still read the next paragraph) or if not then:
1 block will be 'system files' that are green & can only be defragged at boot time because windows uses them
1 block will be user files which can be defragged when ever
1 block will be the page file this is virtual ram (linux/unix uses a whole partition not a file) this too can only be defragged during boot time.

if this is still not the correct explanation then it maybe due to the fact that windows allocates disk space for various reasons like extra room for page file so it can grow dynamicaly when needed or if you use p2p software and have a lot of files in the download que then windows will also allocate the required space (common cause of corruption) for the total amount in the que...

you can get around some of these grouping of files by using diskeeper as this has the ability to 'colate/defrag free space' & can put the page file at the end of the windows partition & it can 'colate/defrag system files' all during boot time other people may know of other disk defraggers that also do this but i tend to stick with what i know works but if a system is configured/used/installed correctly then most of these problems can be resolved IE:
3 partitions for win 
1 for the base system
1 pagefile partition 1Gb on the secondary ide/sata cable
1 for user data/my documents/program files 
this way can be changed to suit but proves to have more performance and less fragmentation because all the core componets are split up; yes files will frag up but that is a windows issue but you will have less because the drive heads cant put parts of user files in with system files because they are on a seperate partition table or F.A.T. (file allocatition table)

or just ditch Mikewrongshafted Windblows out of billys arse and just get used to working in linux....

also linux/unix filesystems do not need to be defragged because they handle the files better/differently than filesystems used by windows but you will need at least 2 partitions for ubuntu to be installed so the simplest example you would have:

partition 1 C:\ (hda1 for linux) 20Gb these 2 can be mounted by linux but only in read only if ntfs
partition 2 D:\ (hda2 for linux) 20Gb
partition 3 unknown (hda3 or /(root) for linux 20Gb windows can read these linux file systems
partition 4 unknown (hda4 or swap for linux) 1Gb


I hope that was not too long an explanation & shed a light on a few thoughts

---

### Post by snellgrove on 2006-02-28
This isn't really appropriate for Ubuntu but I know a great util for defragging parts of windows - basically it does it while your PC is booting - like when a scandisk is set for XP, it does it while booting... same kind of thing.

[click here](http://www.sysinternals.com/Utilities/PageDefrag.html)

Extract the file to your C:\ or somewhere, run it and tell it to defrag on next-boot, jobs a good'n :mrgreen:

as for things being in 3 seperate blocks or so, I dunno why this happens but I've seen it on plenty of PC's. as long as the files are defragged its probably not a major problem, must be a file system thing that it puts things in different areas of a partition. used, unused etc..  ?

---

### Post by tomski on 2006-02-28
page defrag only used to defrag the page file! 
have they updated it now then

---

### Post by snellgrove on 2006-02-28
Does the page file and a variety of other usually-locked system files :)

Take a look at that page, theres a screenshot

it shows how many fragments too, so you dont have to run it if they're all showing 1 or 2 or whatever, as it wouldn't be a massive hit on performance.

---

### Post by yager on 2006-03-01
Do a google on DIRMS.  It has a free 30 day trial and $10 to register.  I just used this tool on my Windows XP Home C: and it squashed everything down to the beginning of the Windows partition.

It now has a GUI frontend so most of the instructions are no longer accurate about being a command line item.  Also, don't push the compress button unless you have 3 days to wait.  The defrag button was alot faster, maybe 1 hour, and was what put everything in the first part of the drive.

---

### Post by soonindallas on 2006-03-02
[QUOTE=doubleeagle]Hey,

I'm pretty new to all this so forgive me if this question is stupid. I'm intending on installing ubuntu along with windows xp on my laptop. I've defraged my hd using windows defrag, but instead of putting all the data to the start of my hd it shows it as been in 3 seperate large blocks. Will ubuntu regconize this as one when i try to partition the hd? Or do i need to have it all at the start of the hd?

Thanks.[/QUOTE]

point is I think the ubuntu partitioner in the installer shrinks partitions without data loss.  It doesn't defragment but you should not lose any data.

I *know* from experience that gparted shrinks ntfs partitions without data loss: I used the live cd on mine and it works perfectly.  I had defragmented it with the windows utility but the data had not been shifted to the front end.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

