---
title: "How to Install iso file"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Ubun2 on 2005-11-03
I am a novice, i have downloaded the "ubuntu-5.10-install-i386.iso" file. How do I install it, do i need to prepare my computer in any way. I tried to run in from my cd-drive and recieved a message that it was not a windows program. 
:confused:

---

### Post by slazh on 2005-11-03
You'll have to burn the file (called an cd image) with any cd writing program that can burn images. Nero can for example.

In nero you can select to burn an image. Browse to .iso file and select it.
Then just follow the steps and burn it.

After it's done, you can boot from that disc. If you don't know how to boot 
from a CD; you can set your boot sequence in the BIOS menu (pres DEL after you boot).

Just for the record; the .iso file isn't a program, but a CD image which contains the installation files and programs for Ubuntu :)

---

### Post by Ubun2 on 2005-11-03
Thank you slazh, I will give it a go i have Nero on my pc. Thanx

---

### Post by Felipe_U on 2005-11-03
[QUOTE=Ubun2]I am a novice, i have downloaded the "ubuntu-5.10-install-i386.iso" file. How do I install it, do i need to prepare my computer in any way. I tried to run in from my cd-drive and recieved a message that it was not a windows program. 
:confused:[/QUOTE]

Do you have a backup of you importan files?? if not, backup before installing. You'll need to have free umpartitioned disk space to create a ext3 partition from the installation. Or partition your disk with a partition tool like Partition Magic and make a partition for linux, If you wan't to be able to keep you windows and be able to dual boot.

Greetings,
Felipe

---

### Post by Ubun2 on 2005-11-03
Thanks for the info Felipe, I will be installing on a filefree computer..
Can you help with my original post. I reburned the disk with nero creating a bootable disk, using neros program. when i ran the disk, it booted the computer, but i was still unable to get the ISO file activated.. I am a little unsure about Slazh's advice regarding "burning an image" I presume it means to treat file as an image..My version of nero does not have a specifc Icon for burning images, I created a data cd..Is this incorrect? There is an icon to share photoes and music and movies, this icon is in extras..Could this be the correct Icon, I would have asked Slazh but he has logged off. 
Regards keith

---

### Post by dbott67 on 2005-11-03
** I moved this post and added it to the just under the next one **

-Dave

---

### Post by Felipe_U on 2005-11-03
[QUOTE=Ubun2]Thanks for the info Felipe, I will be installing on a filefree computer..
Can you help with my original post. I reburned the disk with nero creating a bootable disk, using neros program. when i ran the disk, it booted the computer, but i was still unable to get the ISO file activated.. I am a little unsure about Slazh's advice regarding "burning an image" I presume it means to treat file as an image..My version of nero does not have a specifc Icon for burning images, I created a data cd..Is this incorrect? There is an icon to share photoes and music and movies, this icon is in extras..Could this be the correct Icon, I would have asked Slazh but he has logged off. 
Regards keith[/QUOTE]

You did not burn it right. You have to choose Burn ISO or something like that from the Nero menu. You'll know when you have it right when you can see the contents of the cd instead of a *.iso file in the disc.

Are you planning to run just Ubuntu on your box? 

Greetings,
Felipe

---

### Post by dbott67 on 2005-11-03
The CD you burn should not be a data CD (or one for pictures/photos/music) or a bootable CD. There should be an option to "Create CD from Image File".
 
 An .ISO file is basically an entire CD (with normal files and directories) all packed up into one file called an 'image' --- it's kind of like using Winzip to take 100 files and compressing them into 1 zip file. In this case, it's taking an entire CD and making it into an ISO file. Most burning programs have a special option that allows you to 'burn' an image file to a CD, thereby extracting the .ISO file into it's original file & folder structure.
 
Check the 'help' section of the software and search for 'burning an ISO'. You can also post what software & version you're using to burn & maybe someone can find a link for you.

Here's a few screenshots of Nero 6 (StartSmart and Nero Express):[LIST=1]
[*]For StartSmart, select 'Copy & Backup' and then choose 'Burn Image to Disk'
[*]To Switch to Nero Express, click 'Applications' and select 'Nero Express'
[*]To burn an image in Nero Express 6, select the bottom option 'Disk Image or saved project'
[*]Select the .ISO file and follow the steps... you should be burning like Rome[/LIST]If you're using another program, or would like to download a freeware CD burning application, follow this link:
[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

Hope this helps.

-Dave

---

### Post by ecobuntu on 2005-11-03
[QUOTE=Felipe_U]You did not burn it right. You have to choose Burn ISO or something like that from the Nero menu. You'll know when you have it right when you can see the contents of the cd instead of a *.iso file in the disc.

Are you planning to run just Ubuntu on your box? 

Greetings,
Felipe[/QUOTE]

Maybe you downloaded it wrong...what did you get for md5sum?  If this fails you'll need to re download

---

### Post by Ubun2 on 2005-11-03
Thank you for your help Felipe_U,  dbott67 posted an image for me to follow, this was my third CD i have ever burnt, you were correct in saying i burnt it the wrong way, i burnt it as a data disk and it gave me an exact copy..I am setting up a classroom of refurbished computers, doing crash course in linux so as to be able to help an Aboriginal Community in my town, "Glen Innes Australia" to be able to own and use a computer.These people have very little money to spend on pc and programs etc. Thank you dbott67.

Ubun2

---

### Post by dbott67 on 2005-11-03
You're welcome.

---

### Post by kmukund87@gmail.com on 2006-10-03
Hi everyone,

I have downloaded the xubuntu installation iso file. (i forgot toused synaptic).  Now how do i install it. Is there anyway of installation without burning to a cd?

Thanks in advance.

---

### Post by Cynical on 2006-10-03
Yes, but its a good idea to burn it to a cd. The other installation methods are not meant for new users.

---

### Post by dbott67 on 2006-10-04
I would concur with 'Cynical' --- just burn the ISO.  However, if you are installing Ubuntu in a virtual machine (VMWare, MS Virtual PC, etc.) you can mount the .ISO as a cd.

-Dave

---

### Post by trriangle on 2006-11-09
Hello,

Speaking about CD writing tools I suppose ISO-Burner is a great one. It is extremely easy to use, just a few clicks, quick and reliable.
[http://www.ntfs.com/iso-burning.htm](http://www.ntfs.com/iso-burning.htm)

---

### Post by belikralj on 2007-03-18
I too have a question about .iso files, how can I burn them from ubuntu? I have Dapper and have so far used windows to do my CD-burning, but since I got the internet running I want to siwtch fully to Ubuntu. Is there some software like Nero or do the tools come standard?

thanx in advance

---

### Post by Lord Illidan on 2007-03-18
K3B - for KDE and Brasero - for gnome can both burn iso files, and are available in the Ubuntu repositories. Note that although I said For KDE and for Gnome, they can run in either environment.

---

### Post by Oddler on 2007-11-20
I downloaded a program from the internet under an ISO format and I'm having a hard time installing it. These file formats have always kicked my butt and it's doing it again ](*,)

I followed all the steps advice and links you guys gave on this thread Oh-so many years ago but I still can't get it to work. I've burned two CDs thus far with two different programs.

 First was Iso Recorder Power Toy as the first recommendation on the petri website. When I used this program it seemed pretty straight-forward...Although, when I tried to burn the Image file onto a CD  all it did was Copy the Folders and Files onto the CD like it was on my computer. There wasn't an install .exe 

Then I used ActiveISO burner....pretty much same deal. 

I have tried to use PowerISO as well but this program was much more complicated and I couldn't even find the Burn Image to CD option :lolflag:

I would like to install this program onto my computer but not sure what I'm doing wrong. 
If any of you would like to chat in real time on AIM or MSN I'd sooooo appreciate that hehe. 

Thanks again,
 Ronnie

---

