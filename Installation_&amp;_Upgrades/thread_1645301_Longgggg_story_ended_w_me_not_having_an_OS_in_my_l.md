---
title: "Longgggg story ended w me not having an OS in my laptop..."
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by firedog09 on 2010-12-14
like i said long story... 
windows 7 went into a boot loop after i was in the msconfig folder n probably unchecked something important from the boot section...

now i am trying to install ubuntu 10.10 n i had already done so before as dual boot in my laptop.. but i had done it w wubi from within windows.. im trying w a install cd n i tried w a USB aswell, now i have 2 questions 

1. does it matter if i install ubuntu desktop on a laptop or should i try n install netbook version of 10.10?

i have tried to install desktop so i can have an operation sys on my laptop, i tried an install n used the entire disk. deleted win. 7 but to my sad surprise it fails install telling me their is a disk failure or it could b my cd its dirty or my reader is dirty.. i did a hard drive test n it says my disk has one error n its an epic fail.. 

2. can this b fixed? is there another way to install ubuntu ...

i have a lenovo g555 w 3gs of ram n 160gs of hard disk space n 2.5GHz dualcore processor.. it became handicaped friday when i decided i knew what i was doing in msconfig... there is now wind 7 to go back to, for now its just a shell ... 

tks guys..

---

### Post by firedog09 on 2010-12-14
this r some pics of the actual windows, i took em w my phone i dont kno if u guys can read what it says n maybe get a better idea of my problem it got stuck on the last picture i had to turn it off...

---

### Post by dabl on 2010-12-14
Are you giving up on Win 7?  If so, why don't you just boot a Live CD, and use GParted, and do "Device > New Partition Table" and start over with a clean hard drive?  Then you can partition it as you wish and be done with those silly MS partitions all over the place.

Of course, I assume you understand this will permanently nuke every byte of data and software on that drive ....

---

### Post by firedog09 on 2010-12-14
i did do that, nuked win 7... yes iv given up on it. i dont have the windows 7 live cd..

i have done the new partitions cleaned it all i was able to go into ubuntu "try it first" n moved all my important files to an external drive, so i could do install as needed.
i did the partition for swap n for the sys n for home.. but no go...

---

### Post by dabl on 2010-12-14
Did you make the new partition table, and choose "MS-DOS" type?

If yes, then maybe the only thing your BIOS needs is to have the "boot" flag set on the partition that has the OS on it.  In GParted, you can right-click on that partition, choose "Manage Flags", and tick the "boot" box.

---

### Post by firedog09 on 2010-12-14
ok can u pls explain the flags part? n what would b good configuration for the partitions... 
the times i have installed ubuntu was w wubi so partitions was not a big deal before... 

if i have 160gb? what would b the best to do this

tks for helping

---

### Post by firedog09 on 2010-12-14
i actually set my partitions like she said.. 

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

i didnt know how to do it. lol she helped until its stoped

---

### Post by dabl on 2010-12-14
Some BIOSs require that the "boot" flag is set on any drive partition where you want to boot an OS.  Set that flag on only one partition, using GParted, as I wrote above.

[http://www.gnu.org/software/parted/manual/html_node/set.html](http://www.gnu.org/software/parted/manual/html_node/set.html)

Partitioning is somewhat a matter of taste.  I make a generous 15GB or 20GB partition and install the entire OS including /home in it. (this way you can download an occasional DVD ISO or big video with no worries).  I use a swap partition equal to my RAM size, so I can always hibernate the system if I want to.

My data (music, docs, pix, etc.) stays on its own partition(s), which I have to set up for mounting in /etc/fstab.

Then I symlink my data in to my /home/dabl folder, so it appears there available, just as if it were literally in there.

Just my way ...  :)

---

### Post by firedog09 on 2010-12-14
tks Dabl i had lost hope i found Gparted n im rezising my drive as i type this i also the set the flag for boot on the drive i will b installing the OS i did a 25000MB for it.. i watch alot of movies n download alot of torrents :P 

i hope it works 

i atteched a pic of what u told if u could pls let me kno its right i think it is.. tks

---

### Post by dabl on 2010-12-14
That will work just fine.  In the "Unallocated" space, go ahead and format it to ext4 as well -- that will be a good place to keep your videos after you've watched them.  :)

---

### Post by firedog09 on 2010-12-14
My last question!!!

when i set it to boot from on the bottom before i chose the partitions in the setup ...

it says boot from, i choose this partition correct?

n there was a partion that had this "/" what does that mean? do i have to make it?
so on this 25gb partion i make it /Home correct?

tks again

---

### Post by dabl on 2010-12-14
In the GParted graphic that you showed, the first (top) partition is the one where you will install the entire OS.  It has the "boot" flag marked correctly.  Don't set the "boot" flag on the other partition, just format it to ext4.

When you boot the Live CD or Alternate Install CD (I prefer the Alternate), and you start the installer, you will choose "Manual Partitioning".  It will show you the disk partitions, and you will choose to set the mount points.  The only mount points you want to set during installation are "/" for that first /dev/sda1 partition, and "swap" for the swap space -- it will be obvious.  Then let it complete the installation with defaults, including writing Grub to the MBR of the hard drive.  The second (large) ext4 partition probably will be picked up for automatic mounting, with a name like "/media/disk1" or something equally useless, but that is fixable after you've rebooted and have your system up and running.

Don't worry, if the installation gets messed up, you just call it "practice" and do it again.  :D

---

### Post by firedog09 on 2010-12-14
it didnt work... it gives me the same error 5 input/output error.. 

im gonna try again leaving the unalocated space the way it is, i had it as ext4 .... but maybe if it has less space to work it will install beter

---

### Post by dabl on 2010-12-14
Your first two graphics indicate a defective DVD or CD.  Did you (a) check the md5sum on the downloaded ISO image, and (b) burn it at the slowest speed available?

---

### Post by firedog09 on 2010-12-14
sry had to go get my bro..

hmmm idk how to check the md5sum, i got the .iso from the ubuntu site, maybe if i use the netbook .iso since i have a laptop..

also how slow? max50 i think... just like 10x?

i used a USB yesterday n it still gave me that same problem... is der anywhere i may b able to get 10.4? maybe this version just doesnt like lenovo lol

---

### Post by dabl on 2010-12-14
No, not 50x -- you need to set the burn speed at the slowest speed your burner offers -- 4X or 8X. Look at #1 here:

[http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

---

### Post by firedog09 on 2010-12-14
u have  whole thread on that tks lol ill give it a good read... 

ill get w u tomorrow... if u can check back .. tks. im gonna try ubuntu netbook n im gonna re make the live cd at slow speeds. i did mine at 50x lol i hope thats the rpoblem

tks again

---

### Post by firedog09 on 2010-12-15
so i did the burn of the image at 8x the slowest my driver can do it, i try the install n no bueno.. not it wont even give me option to install just has the ubuntu screen w the 4 dots, n tries den stops n gives me an error...

on the other hand surfin the google i found alot of ppl come across error 5..n alot of em solve it by doing a text install? do u kno how to do it, others have solve it by removing RAM sticks n leaving just one, n intalled like that.. idk just throwing ideas your way maybe w ur knowledge it will make more sence..

[http://ubuntuforums.org/showthread.php?t=600126](http://ubuntuforums.org/showthread.php?t=600126)

he used a terminal command?

[http://www.linuxquestions.org/questions/linux-newbie-8/errno-5-input-output-error-639355/](http://www.linuxquestions.org/questions/linux-newbie-8/errno-5-input-output-error-639355/)   

_ second posts gives the ram solution

[http://ubuntuforums.org/showthread.php?t=1298179](http://ubuntuforums.org/showthread.php?t=1298179)
he gives a solution to this but i dont understand xD lol

k tks if u can hit me up i downloaded netbook 10.10 n hopefully it will work

---

### Post by dabl on 2010-12-15
Yeah, try the Alternate Install CD image -- that has the character mode installer, rather than Ubiquity.  I should have thought of it -- that's the only one I use. Burn it slow ...

---

